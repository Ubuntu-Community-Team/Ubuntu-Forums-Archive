---
title: "trouble installing aegisub"
date: 2015-02-15
forum: Installation &amp; Upgrades
---

### Post by remmas-sido on 2015-02-15
I'm running ubuntu 12.04 ,and I'm trying to install aegisub_2.1.8-0.2_i386.deb here is a direct link if anyone's interested:
[http://www.deb-multimedia.org/pool/main/a/aegisub/aegisub_2.1.8-0.2_i386.deb](http://www.deb-multimedia.org/pool/main/a/aegisub/aegisub_2.1.8-0.2_i386.deb)
I'm facing dependancy problem here is what come to the terminal when I type: sudo dpkg -i aegisub_2.1.8-0.2_i386.deb 
Selecting previously unselected package aegisub.
(Reading database ... 186326 files and directories currently installed.)
Unpacking aegisub (from aegisub_2.1.8-0.2_i386.deb) ...
dpkg: dependency problems prevent configuration of aegisub:
 aegisub depends on libavcodec52 (>= 5:0.6~svn20100726); however:
  Package libavcodec52 is not installed.
 aegisub depends on libavformat52 (>= 5:0.6~svn20100726); however:
  Package libavformat52 is not installed.
 aegisub depends on libavutil50 (>= 5:0.6~svn20100726); however:
  Package libavutil50 is not installed.
 aegisub depends on libhunspell-1.2-0 (>= 1.2.11); however:
  Package libhunspell-1.2-0 is not installed.
 aegisub depends on libpostproc51 (>= 5:0.6~svn20100726); however:
  Package libpostproc51 is not installed.
 aegisub depends on libswscale0 (>= 5:0.6~svn20100726); however:
  Package libswscale0 is not installed.
dpkg: error processing aegisub (--install):
 dependency problems - leaving unconfigured
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for hicolor-icon-theme ...
Processing triggers for man-db ...
Errors were encountered while processing:
 aegisub
any help is appreciated 
thank you

---

### Post by SeijiSensei on 2015-02-15
Just install it from the Ubuntu repositories, and it will pull in the dependencies automatically.
```
sudo apt-get install aegisub
```
The current Ubuntu version is 3.0.4-2build1, by the way.

Always try the official Ubuntu repositories first for open-source applications like this one.  Installing from other locations, or building from source, should always be your last resort.

---

### Post by remmas-sido on 2015-02-15
> **SeijiSensei said:**
> Just install it from the Ubuntu repositories, and it will pull in the dependencies automatically.
```
sudo apt-get install aegisub
```
The current Ubuntu version is 3.0.4-2build1, by the way.

Always try the official Ubuntu repositories first for open-source applications like this one.  Installing from other locations, or building from source, should always be your last resort.

By the way, from which repository did you get it, because when I type: "sudo apt-get install aegisub"here is what comes:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package aegisub
I'm running ubuntu 12.04, maybe you are running a newer version, because I read somewhere in this site or askubuntu website that aegisub is included by defaut starting from 12.10 release.

---

### Post by Bucky Ball on 2015-02-15
> **remmas-sido said:**
> ... I read somewhere in this site or askubuntu website that aegisub is included by defaut starting from 12.10 release.

Then I presume you are using 12.04 LTS. You are trying to install a very old version. Try installing the newer one from [here]("http://www.aegisub.org/downloads/#source") or upgrading, perhaps to 14.04 LTS. I have it in the Ubuntu repositories here on 14.04.

---

