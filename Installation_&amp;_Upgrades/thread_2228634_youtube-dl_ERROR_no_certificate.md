---
title: "youtube-dl ERROR: no certificate"
date: 2014-06-08
forum: Installation &amp; Upgrades
---

### Post by VeryFoggy on 2014-06-08
I tried to upgrade youtube-dl a few months ago. Not only did it NOT upgrade, it disabled the program. I don't know what I am doing, or not doing right. I don't know how to use no check certificate. Any thoughts?

----------------------------------------------
sudo wget [https://yt-dl.org/downloads/2014.06.07/youtube-dl.sig](https://yt-dl.org/downloads/2014.06.07/youtube-dl.sig) -O youtube-dl.sig
gpg --verify youtube-dl.sig /usr/local/bin/youtube-dl
rm youtube-dl.sig
candy@candy-HP-Compaq-nc6400-EH522AV:~$ sudo wget [https://yt-dl.org/downloads/2014.06.07/youtube-dl.sig](https://yt-dl.org/downloads/2014.06.07/youtube-dl.sig) -O youtube-dl.sig
[sudo] password for candy: 
--2014-06-08 15:30:34--  [https://yt-dl.org/downloads/2014.06.07/youtube-dl.sig](https://yt-dl.org/downloads/2014.06.07/youtube-dl.sig)
Resolving yt-dl.org (yt-dl.org)... 95.143.172.170, 2001:1a50:11:0:5f:8f:acaa:177
Connecting to yt-dl.org (yt-dl.org)|95.143.172.170|:443... connected.
ERROR: no certificate subject alternative name matches
    requested host name `yt-dl.org'.
To connect to yt-dl.org insecurely, use `--no-check-certificate'.
candy@candy-HP-Compaq-nc6400-EH522AV:~$ sudo curl [https://yt-dl.org/downloads/2014.06.07/youtube-dl](https://yt-dl.org/downloads/2014.06.07/youtube-dl) -o /usr/local/bin/youtube-dl
sudo: curl: command not found
candy@candy-HP-Compaq-nc6400-EH522AV:~$ 
candy@candy-HP-Compaq-nc6400-EH522AV:~$ sudo wget [https://yt-dl.org/downloads/2014.05.13/youtube-dl](https://yt-dl.org/downloads/2014.05.13/youtube-dl) -O /usr/local/bin/youtube-dl
--2014-06-08 15:34:20--  [https://yt-dl.org/downloads/2014.05.13/youtube-dl](https://yt-dl.org/downloads/2014.05.13/youtube-dl)
Resolving yt-dl.org (yt-dl.org)... 95.143.172.170, 2001:1a50:11:0:5f:8f:acaa:177
Connecting to yt-dl.org (yt-dl.org)|95.143.172.170|:443... connected.
ERROR: no certificate subject alternative name matches
    requested host name `yt-dl.org'.
To connect to yt-dl.org insecurely, use `--no-check-certificate'.

---

### Post by bapoumba on 2014-06-09
[http://ubuntuforums.org/showthread.php?t=1850955](http://ubuntuforums.org/showthread.php?t=1850955)
Thread closed.

---

