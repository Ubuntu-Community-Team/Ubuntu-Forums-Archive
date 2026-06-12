---
title: "FTP server Upload data"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by audireddy on 2011-11-11
Hi All,

I am install Ftp server in ubuntu 10.10 desktop edition.

My requirement is Ftp server one user have only upload the data like write access that 

user did not read the data also.

Is it possible or not can you tell me

Thanks
Audinarayana Reddy

---

### Post by Lars Noodén on 2011-11-11
[Avoid FTP](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/), it is insecure.  You can get the ability to securely upload files using SFTP.  That comes as part of the package OpenSSH-server and needs no further configuration to use.  Nautilus and Filezilla include SFTP support.

---

