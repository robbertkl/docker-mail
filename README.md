# robbertkl/mail

[![](https://badge.imagelayers.io/robbertkl/mail:latest.svg)](https://imagelayers.io/?images=robbertkl/mail:latest)

Docker mail server container.

Software:

* Postfix as MTA (SMTP)
* Dovecot as LDA (IMAP) + sieve
* OpenDKIM for DKIM checking / signing
* OpenDMARC for DMARC checking
* postfix-policyd-spf-python for SPF checking

Features / config:

* No database (everything is file based)
* User authentication through password file
* Local storage in persistent volume
* Multi-domain supported (using separate DKIM keys)
* Delivery through `dovecot-lda` (LMTP prevents `X-Original-To` header)

## Usage

Run it like this:

```
docker run -d -h <mail.domain.org> -v <path-to-ssl>:/private/ssl -p 25:25 -p 143:143 -p 587:587 -p 993:993 robbertkl/mail
```

See [robbertkl/docker-base#ssl](https://github.com/robbertkl/docker-base#ssl) for info on SSL file naming. A cert+ca bundle file for dovecot is created automatically.

## Authors

* Robbert Klarenbeek, <robbertkl@renbeek.nl>

## License

This repo is published under the [MIT License](http://www.opensource.org/licenses/mit-license.php).
