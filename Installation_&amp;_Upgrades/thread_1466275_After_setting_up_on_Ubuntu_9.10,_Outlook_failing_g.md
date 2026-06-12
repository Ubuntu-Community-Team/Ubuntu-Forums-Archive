---
title: "After setting up on Ubuntu 9.10, Outlook failing gnutls_handshake"
date: 2010-04-30
forum: Installation &amp; Upgrades
---

### Post by bsgcic on 2010-04-30
I have been googling for three days now to no avail.
 
I have just reconfigured relevant email settings (exim4, mailscanner, clamav, saslauthd, ldap, samba, dovecot, ssl, ca-certificates, .crt and .pem files) on ubuntu 9.10 by updating the current version of each's settings files with my customizations that I had made on Ubuntu 8.04 LTS.
 
I am able to receive email fine but can no longer send. My configuration requires TLS over port 587.
 
Please note again that the customizations, certificates, etc are those that worked on 8.04 LTS.
 
Outlook 2007 produces the following error (not exact wording):
Sending of test email message: does not support the encryption type supplied by the server. Please change the encryption method. Contact your administrator...
 
And in the mainlog:
SMTP connection from [123.123.123.123]:1185 I=[123.123.123.124]:587 (TCP/IP connection count = 1)
2010-04-30 16:05:21 [2808] no host name found for IP address 123.123.123.123
2010-04-30 16:05:22 [2808] TLS error on connection from (mycomp) [123.123.123.123]:1185 (gnutls_handshake): A TLS packet with 
unexpected length was received.
2010-04-30 16:05:22 [2808] SMTP connection from (mycomp) [123.123.123.123]:1185 I=[123.123.123.124]:587 closed by EOF
2010-04-30 16:05:22 [2808] no MAIL in SMTP connection from (mycomp) [123.123.123.123]:1185 I=[123.123.123.124]:587 D=6s C=EHLO,STARTTLS
 
I did the following test:
I first used the keys that include my public hostname (i.e., the ones that I have been using all along on Ubuntu 8.04LTS).
 
exim4 -bd -d+tls -oX 127.0.0.1.587 -tls-on-connect
gnutls-cli -p 587 127.0.0.1
 
I got the following:
 
Resolving '127.0.0.1'...
Connecting to '127.0.0.1:587'...
- Successfully sent 0 certificate(s) to server.
- Ephemeral Diffie-Hellman parameters
- Using prime: 1024 bits
- Secret key: 1023 bits
- Peer's public key: 1021 bits
- Server has requested a certificate.
- Certificate type: X.509
- Got a certificate list of 1 certificates.
- Certificate[0] info:
- subject `C=US,O=My Org,OU=My Unit,L=MyCity,ST=MyState,CN=MyHostname,EMAIL=MyEmail', issuer `C=US,O=MyCA,OU=MyCAUnit,L=MyCity,ST=MyCity,CN=MyHostName,EMAIL=MyEmail', RSA key 1024 bits, signed using RSA-SHA, activated `ADateIn2008', expires `ADateIn2011', SHA-1 fingerprint `ABunchOfLettersAndNumbers'
- The hostname in the certificate does NOT match '127.0.0.1'
 
So, I then generated a new exim.crt and exim.key using exim-gencert and configured exim to use those (just for this following test) and set the CN to 127.0.0.1
 
Then did gnutls-cli -p 587 127.0.0.1 again and this time a connected with a successful gnutls_handshake.
 
I tried using various values for the CN in subsequent exim.crt and exim.keys but still get the same error message in Outlook.
 
Were there any changes between 8.04 LTS and 9.10 that would cause this behavior Any ideas?
 
I would greatly appreciate help on this.
 
Thank you

---

