---
title: "Ftp &amp; Ssl"
date: 2006-10-16
forum: Installation &amp; Upgrades
---

### Post by andnos on 2006-10-16
Hi, 

It seems I've installed SSL to work with FTP, but I'm getting the following:

Status:	Connecting to server.com ...
Status:	Connected with server.com, negotiating SSL connection...
Response:	220 ProFTPD 1.2.10 Server (server.com) [132.xxx.xxx.xxx]
Command:	AUTH SSL
Response:	234 AUTH SSL successful
Error:	Can't establish SSL connection
Error:	Disconnected from server
Error:	Unable to connect!


Any idea why this happens? it looks like it connects, but then cancels.

---

### Post by JonahRowley on 2006-10-16
Is sftp available?  I've never had any problems with sftp or scp, and endless problems with FTP.  I just avoid it wherever possible now.

---

### Post by andnos on 2006-10-16
SFTP (FTP with SSH) works fine for all accounts, what I set up is proftpd+mysql, and it's the "virtual" accounts that I want to use FTP with SSL, but can't get it to work. 

Somebody told me that as long as I have openssl set up it should work fine, but it's not working fine....

---

### Post by andnos on 2006-10-18
Has anybody had any experience securing "ANY" and all FTP access to their servers with SSL?

---

