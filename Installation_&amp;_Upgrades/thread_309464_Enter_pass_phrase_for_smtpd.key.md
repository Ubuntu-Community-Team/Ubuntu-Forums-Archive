---
title: "Enter pass phrase for smtpd.key:"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by Bill007 on 2006-11-29
Kia Ora 

whatis my (Enter pass phrase for smtpd.key:)


**root@production:/home/bill007#** mkdir /etc/postfix/ssl
openssl x509 -req -days 3650 -in smtpd.csr -signkey smtpd.key -out smtpd.crt
openssl rsa -in smtpd.key -out smtpd.key.unencrypted
mv -f smtpd.key.unencrypted smtpd.key
openssl req -new -x509 -extensions v3_ca -keyout cakey.pem -out cacert.pem -days 3650mkdir: cannot create directory `/etc/postfix/ssl': File exists
**root@production:/home/bill007#** cd /etc/postfix/ssl/
**root@production:/etc/postfix/ssl#** openssl genrsa -des3 -rand /etc/hosts -out smtpd.key 1024
248 semi-random bytes loaded
Generating RSA private key, 1024 bit long modulus
..............................................................++++++
.................++++++
e is 65537 (0x10001)
Enter pass phrase for smtpd.key: **??????????**

---

### Post by smeago on 2008-05-01
Hello, I recently installed Ubuntu on my linode system. I Have installed Postfix and I would like to enable SMTP AUTHORIZATION. However, I have not been sucesful. Can anyone help me with the sample command line syntax to install this . 

I tried using some online tutorial but I got similar error as above:

Enter pass phrase for smtpd.key


Thannks

---

