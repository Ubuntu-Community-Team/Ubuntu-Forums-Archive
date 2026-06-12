---
title: "Getting Flash Player for Ubutnu 6.10 Edgy"
date: 2006-11-12
forum: Installation &amp; Upgrades
---

### Post by Urinemachine on 2006-11-12
I just installed (woo!) but now I want to visit youtube.com, it says I either have javascript turned off (its enabled in Mozilla) or I do not have Flash Plugin.  So I followed the add/remove thing and found Flash Plugin, installed it, I think, restarted firefox but it still says i dont have flash.

What do I do?

---

### Post by bruenig on 2006-11-12
To get flash copy and paste the following commands in order

This removes any flashplugins you may have installed earlier
```
sudo apt-get remove flashplugin-nonfree
```
This downloads the flash plugin
```
wget http://3v1n0.tuxfamily.org/pool/dapper/3v1n0/flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
```
This installs it.
```
sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
```

Note this installs flash 9 beta plugin. Flash 7 is the other one. Flash 9 beta is better and I have had absolutely no problems. In flash 7 videos are often out of synch and there is a sound bug that often causes you to be unable to hear sound. I would go with flash 9, so to do that just copy and paste those commands.

---

### Post by DannyG on 2006-11-12
My flash is out of sync with the audio even with the Flash Player 9, is there something I can do to remedy this?

Note, that I originally had Flash 7 and I simply replaced the .so file with the Flash 9 .so file, could this be the problem?

---

### Post by Urinemachine on 2006-11-12
I followed your instructions but get:


jon@jon-desktop:~$ sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
Selecting previously deselected package flashplugin-nonfree.
dpkg: regarding flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb containing flashplugin-nonfree:
 flashplugin-nonfree conflicts with libflash-mozplugin
  libflash-mozplugin (version 0.4.13-8ubuntu1) is installed.
dpkg: error processing flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb (--install):
 conflicting packages - not installing flashplugin-nonfree
Errors were encountered while processing:
 flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb

---

### Post by bruenig on 2006-11-12
> **Urinemachine said:**
> I followed your instructions but get:


jon@jon-desktop:~$ sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
Selecting previously deselected package flashplugin-nonfree.
dpkg: regarding flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb containing flashplugin-nonfree:
 flashplugin-nonfree conflicts with libflash-mozplugin
  libflash-mozplugin (version 0.4.13-8ubuntu1) is installed.
dpkg: error processing flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb (--install):
 conflicting packages - not installing flashplugin-nonfree
Errors were encountered while processing:
 flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb

Didn't realize you had that installed. Most people don't.
```
sudo apt-get remove libflash-mozplugin
```
Then do the
```
sudo dpkg -i flashplugin-nonfree_9.0.21.55-3v1ubuntu0_i386.deb
```
Like before.

---

