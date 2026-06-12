---
title: "Can't install updates"
date: 2007-06-12
forum: Installation &amp; Upgrades
---

### Post by prodigy_00 on 2007-06-12
I get this whenever I try to install the updates: 

E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

If I type "dpkg --configure -a" in the terminal I get:

Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
Downloading...
--23:08:20--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.114.70
Connecting to fpdownload.macromedia.com|72.246.114.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,703 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... .......

and it stays like this forever. I can't seem to be able to install anything else either.

---

### Post by zvacet on 2007-06-12
```
sudo dpkg --configure -a
```

---

### Post by prodigy_00 on 2007-06-12
I tried that but I still keep getting:

Setting up flashplugin-nonfree (9.0.31.0.2ubuntu1) ...
Downloading...
--00:43:36--  [http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz](http://fpdownload.macromedia.com/get/flashplayer/current/install_flash_player_9_linux.tar.gz)
           => `./install_flash_player_9_linux.tar.gz'
Resolving fpdownload.macromedia.com... 72.246.114.70
Connecting to fpdownload.macromedia.com|72.246.114.70|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 2,609,703 (2.5M) [application/x-gzip]

    0K .......... .......... .......... .......... ......

---

### Post by gbusse on 2007-06-20
I have this same problem on two different machines (both running fully updated copies of Feisty) on completely different networks and isp's.

This is really annoying... any tips would be appreciated.

Thanks,
Gordo

---

