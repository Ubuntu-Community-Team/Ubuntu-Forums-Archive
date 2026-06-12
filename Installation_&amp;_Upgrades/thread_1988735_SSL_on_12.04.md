---
title: "SSL on 12.04"
date: 2012-05-28
forum: Installation &amp; Upgrades
---

### Post by nariub on 2012-05-28
Bug report is here
[https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/1001040](https://bugs.launchpad.net/ubuntu/+source/postfix/+bug/1001040)

workaround is to add to /etc/postfix/main.cf 

smtpd_tls_exclude_ciphers = RC4-MD5

however my android gingerbread phone now thinks my email server doesnt support SSL.

My PC clients see my server just fine.  Just not my android phone.

The bug report above lists something that went on in google land that stopped email from gmail to my server until I excluded RC4-MC5.

I would say that google is to blame and rah rah hate the man and all.  But i am actually leaning toward something horked up in OpenSSL.

Thought I would drop a note say it is a problem and look for a workaround.   

FYI
I have a my own CA and created SSL certs for my web email servers. Gingerbread wont let me import my CA but had been giving me a prompt and letting me view the cert then letting me continue on without complaints.  Those days appear to be gone now.

My carrier is supposed to be giving me ICS in the next month or so. Maybe then.  Maybe then.

---

### Post by nariub on 2012-06-09
My bad,
My ASUS eeePC running 12.04 32bit and running Thunderbird cannot connect to my upgraded email server either.

so now the client on my android and my eeePC do not work.

I guess I gotta actually fix it now.

---

### Post by nariub on 2012-06-09
012-06-09 09:44:55 imap-login: Info: Aborted login (no auth attempts): rip=<EEEPCCLIENTIP>, lip=<SERVERIP>
2012-06-09 09:44:55 imap-login: Info: Aborted login (no auth attempts): rip=<EEEPCCLIENTIP>, lip=<SERVERIP>
2012-06-09 09:45:08 imap-login: Info: Login: user=<marione>, method=PLAIN, rip=192.168.10.240, lip=<SERVERIP>, mpid=16183, TLS
2012-06-09 09:45:09 master: Error: service(imap-login): child 16181 killed with signal 11 (core dumps disabled)
2012-06-09 09:45:09 imap(marione): Info: Connection closed bytes=0/285
2012-06-09 09:45:10 imap-login: Info: Disconnected (no auth attempts): rip=<EEEPCCLIENTIP>, lip=<SERVERIP>, TLS: SSL_read() failed: error:14094416:SSL routines:SSL3_READ_BYTES:sslv3 alert certificate unknown: SSL alert number 46
... the last line repeats alot...

2012-06-09 09:45:55 imap-login: Info: Disconnected (no auth attempts): rip=<EEEPCCLIENTIP>, lip=<SERVERIP>, TLS handshaking: SSL_accept() failed: error:14094416:SSL routines:SSL3_READ_BYTES:sslv3 alert certificate unknown: SSL alert number 46
2012-06-09 09:45:55 imap-login: Info: Disconnected (no auth attempts): rip=<EEEPCCLIENTIP>, lip=<SERVERIP>, TLS: SSL_read() failed: error:14094416:SSL routines:SSL3_READ_BYTES:sslv3 alert certificate unknown: SSL alert number 46
... the last line repeats alot again...

then she alternates between alot of fails and a few handshaking fails.


the android phone
2012-06-09 11:40:45 imap-login: Info: Disconnected (no auth attempts): rip=<ANDROIDCLIENTIP>, lip=<SERVERIP>, TLS: SSL_read() failed: error:140943FC:SSL routines:SSL3_READ_BYTES:sslv3 alert bad record mac: SSL alert number 20
2012-06-09 11:45:12 imap-login: Info: Login: user=<USERNAME>, method=PLAIN, rip=<ANDROIDCLIENTIP>, lip=<SERVERIP>, mpid=18576, TLS

lots of bad record mac's followed by login attempts.

when i upgraded from 11.10 to 12.04 i kept all original configuration files, while she upgraded 
postfix (2.8.5-2~build1) to (2.9.1-5)
dovecot (1:2.0.13-1ubuntu3.2) to (1:2.0.19-0ubuntu1)
openssl (1.0.0e-2ubuntu4) to (1.0.1-4ubuntu5.2)

other than excluding RC4-MD5 in /etc/postfix/main.cf
I haven't touched my configuration from when I installed it on back in the day

---

### Post by nariub on 2012-08-03
update:
commented out the workaround in /etc/postfix/main.cf 
#smtpd_tls_exclude_ciphers = RC4-MD5

an update to postfix resolved the google email delivery

android phones connecting to my dovecot IMAP server are still causing segfaults in openssl
there is an upgrade 5.4 in proposed that should fix the seqfaults..

openssl_1.0.1-4ubuntu5.4_amd64

considering downloading the deb and installing it early..
might have to if the 12.04.1 point release does not include an update.

gotta read up on how to do that.

---

### Post by nariub on 2012-08-30
openssl 1.0.1-4ubuntu5.5

solved my issue..  My android phone can now pull emails from my mail server again..

woop woop  I am so happy now..

---

