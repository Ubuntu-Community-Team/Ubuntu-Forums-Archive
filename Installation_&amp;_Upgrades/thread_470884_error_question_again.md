---
title: "error question again"
date: 2007-06-11
forum: Installation &amp; Upgrades
---

### Post by kystorms on 2007-06-11
I was trying to load the real player from synaptic and obviously did something wrong - i think i messed up the helix player

The upgrade messed up, so it said in terminal i had broken dependencies, and to use 
sudo apt-get install -f, which i did, and this is the error iget - any reference on what i need to do next?

The following NEW packages will be installed:
  helix-player
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 4062kB of archives.
After unpacking 10.4MB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) feisty/universe helix-player 1.0.6-3 [4062kB]
Fetched 4062kB in 1m14s (54.7kB/s)                                             
(Reading database ... 144951 files and directories currently installed.)
Unpacking helix-player (from .../helix-player_1.0.6-3_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de/LC_MESSAGES/libgtkhx.mo', which is also in package realplay
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/helix-player_1.0.6-3_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
lisac@lisac-desktop:~$ 

thank you for any help

:(

---

### Post by wpshooter on 2007-06-11
I believe what I would do is to attempt to uninstall where ever it is that you got installed and then go to the REALPLAYER website and download and attempt to install the REALPLAYERGOLD10.BIN that you find there.  I would place the downloaded file in my /home directory.  I believe that perhaps you might need to do this as SUDO.

Good luck.

---

### Post by kystorms on 2007-06-11
thank you

Is there a place that explains how to put folders where they belone, i mean the actual steps for doing what you suggest?
I have been doing it all in synaptic, but I am not learning anything that way, and maybe this would help me to NOT mess up anymore

thank you for your help
:KS

---

