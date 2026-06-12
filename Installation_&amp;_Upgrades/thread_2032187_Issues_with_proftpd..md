---
title: "Issues with proftpd."
date: 2012-07-23
forum: Installation &amp; Upgrades
---

### Post by lesone on 2012-07-23
Hello,

I followed a tutorial about installing proftpd. And I have a few errors when I launch it.

```
ksxxxx.kimsufi.com proftpd[29854]: mod_tls/2.4.3: compiled using OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.1 14 Mar 2012' library
ksxxxx.kimsufi.com proftpd[29854]: mod_sftp/0.9.8: compiled using OpenSSL version 'OpenSSL 1.0.0e 6 Sep 2011' headers, but linked to OpenSSL version 'OpenSSL 1.0.1 14 Mar 2012' library
ksxxxx.kimsufi.com proftpd[29854]: mod_tls_memcache/0.1: notice: unable to register 'memcache' SSL session cache: Memcache support not enabled
ksxxxx.kimsufi.com proftpd[29854]: mod_dso/0.5: module 'mod_ctrls_admin.c' already loaded
ksxxxx.kimsufi.com proftpd[29854]: Fatal: LoadModule: error loading module 'mod_ctrls_admin.c': Operación no permitida on line 7 of '/etc/proftpd/proftpd.conf'

```

Please can I have some help.

I'm starting on the ubuntu's world, hehe

Thanks!!

---

### Post by TheFu on 2012-07-23
This isn't an answer, rather a warning.  Before you get too far down running an FTP server, some light reading about all the dangers.

* [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) - my opinion.
* [http://www.zdnet.com/blog/storage/ftp-untrustworthy-file-transfer/344](http://www.zdnet.com/blog/storage/ftp-untrustworthy-file-transfer/344)
* [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
* [http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787](http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787)
* [http://news.softpedia.com/news/Horde-FTP-Server-Hacked-Files-Maliciously-Altered-252708.shtml](http://news.softpedia.com/news/Horde-FTP-Server-Hacked-Files-Maliciously-Altered-252708.shtml)
* [http://www.zdnet.com/blog/security/nasas-goddard-space-flight-center-ftp-server-hacked/8660](http://www.zdnet.com/blog/security/nasas-goddard-space-flight-center-ftp-server-hacked/8660)
* [http://news.techworld.com/security/11561/logins-for-8700-ftp-servers-found-on-sale/](http://news.techworld.com/security/11561/logins-for-8700-ftp-servers-found-on-sale/)
* [http://www.directadmin.com/forum/showthread.php?t=42875&page=1](http://www.directadmin.com/forum/showthread.php?t=42875&page=1)

Especially if you are new to Linux/Ubuntu, you probably want to use something else besides FTP.  Better options are  **sftp** or **scp** for internet and **samba** or** NFS** for LAN file access.  Be certain you lock down **ssh**  [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) if you allow access over the internet.

---

### Post by lesone on 2012-07-23
> **TheFu said:**
> This isn't an answer, rather a warning.  Before you get too far down running an FTP server, some light reading about all the dangers.

* [http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp](http://blog.jdpfu.com/2011/07/10/why-you-need-to-stop-using-ftp) - my opinion.
* [http://www.zdnet.com/blog/storage/ftp-untrustworthy-file-transfer/344](http://www.zdnet.com/blog/storage/ftp-untrustworthy-file-transfer/344)
* [http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/](http://olex.openlogic.com/wazi/2011/stop-using-ftp-how-to-transfer-files-securely/)
* [http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787](http://www.zdnet.com/blog/security/open-source-proftpd-hacked-backdoor-planted-in-source-code/7787)
* [http://news.softpedia.com/news/Horde-FTP-Server-Hacked-Files-Maliciously-Altered-252708.shtml](http://news.softpedia.com/news/Horde-FTP-Server-Hacked-Files-Maliciously-Altered-252708.shtml)
* [http://www.zdnet.com/blog/security/nasas-goddard-space-flight-center-ftp-server-hacked/8660](http://www.zdnet.com/blog/security/nasas-goddard-space-flight-center-ftp-server-hacked/8660)
* [http://news.techworld.com/security/11561/logins-for-8700-ftp-servers-found-on-sale/](http://news.techworld.com/security/11561/logins-for-8700-ftp-servers-found-on-sale/)
* [http://www.directadmin.com/forum/showthread.php?t=42875&page=1](http://www.directadmin.com/forum/showthread.php?t=42875&page=1)

Especially if you are new to Linux/Ubuntu, you probably want to use something else besides FTP.  Better options are  **sftp** or **scp** for internet and **samba** or** NFS** for LAN file access.  Be certain you lock down **ssh**  [http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures](http://blog.jdpfu.com/2011/08/23/securing-ssh-connections-and-blocking-failures) if you allow access over the internet.


Hello,

It's for a private seedbox. Not public.

Thanks.!

---

### Post by TheFu on 2012-07-23
> **lesone said:**
> Hello,
It's for a private seedbox. Not public.
Thanks.!
If it is connected to the internet, it is public and so is the FTP server.  You are a big boy and responsible, so I'll stop preaching.

Those error messages say that the version of OpenSSL on the machine doesn't match the version needed for the proftp version that you installed.  Without the exact tutorial and exact steps that you followed, there isn't any way to know what happened. Starting over is probably easiest.

Remove any openssl and proFTP stuff that you've installed, then simply use the Ubuntu package manager of choice to install proftp.  [http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html](http://www.ubuntugeek.com/settingup-an-ftp-server-on-ubuntu-with-proftpd.html) has steps that seem fairly straight forward and should avoid the SSL conflicts that you are seeing today.

If you are installing an FTP server behind a home router, it becomes more complicated since FTP used multiple ports for data and control. Using sftp gets around this ... as highlighted in my initial reply.

Good luck!

---

### Post by rnosal on 2013-03-28
If you are trying it on Ubuntu 12.04  - The bug is in the queue since Oct 1st.
[https://bugs.launchpad.net/ubuntu/+source/proftpd-dfsg/+bug/1059722](https://bugs.launchpad.net/ubuntu/+source/proftpd-dfsg/+bug/1059722)

---

