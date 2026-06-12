---
title: "Having problems with apt-get installation"
date: 2007-03-25
forum: Installation &amp; Upgrades
---

### Post by DylanBrams on 2007-03-25
So I'm trying to upgrade from 5.06.  I changed the text in the sources.list file, and attempted to update everything.  This was apparently a bad idea.  At this point I can't figure out (from quite a bit of searching) how to load the proper packages to get the package management software to run properly.  Anyone have any hints on what I might be doing wrong?  How to go back and not do it wrong?  Whatever is going wrong here, I'd like to be able to go back and fix it, or just wipe everything and start anew with a non-live Ubuntu installation CD. (the computer I have is not capable of install from LiveCD)

At the moment, I type, "apt-get dist-upgrade" and get, 
"
E: Read error - read (5 Input/output error)
E: Prior errors apply to /cdrom//pool/main/n/ndiswrapper/ndiswrapper-common.1.18-1ubuntu2_all.deb
debconf: apt-extracttemplates failed: Bad file descriptor
dpkg-split: error reading /cdrom//pool/main/n/ndiswrapper/ndiswrapper-common.1.18-1ubuntu2_all.deb: Input/ Output error
dpkg: error processing /cdrom//pool/main/n/ndiswrapper/ndiswrapper-common.1.18-1ubuntu2_all.deb (--unpack): subprocess dpkg-split returned error exit status 2
Errors were encountered while processing:
/cdrom//pool/main/n/ndiswrapper/ndiswrapper-common.1.18-1ubuntu2_all.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by chocbar31 on 2007-03-25
Will this help?

[http://daniel.holba.ch/blog/?p=14]("http://daniel.holba.ch/blog/?p=14")

Seems a little common, what you are going through. I normally take heed to the warning. "If this is a production.....I'm not afraid to lose data, as I have another computer with enough storage for backups.

To be honest...I would blow-out the HDD myself; keyword? Fresh Install.

LOL, kinda like being a Billionaire, only to shop on used car lots. <- Bill Gates best practices!!!:lolflag:

---

### Post by zvacet on 2007-03-26
If you try to upgrade from Breezy to Dapper here is 
```
 gksudo "update-manager" 
```

here is list of options
[https://help.ubuntu.com/community/DapperUpgrades?highlight=%28upgrades%29%7C%28dapper%29]("https://help.ubuntu.com/community/DapperUpgrades?highlight=%28upgrades%29%7C%28dapper%29")

---

### Post by Intro5pection on 2007-12-18
This is my first post, but i've been searching on here for a while. I can't seem to find anyone with the same problem so here goes.

I'm trying to get my intel onboard audio to work and another post suggested using :

sudo aptitude install linux-backports-modules-generic

Whenever I try this I get :

E: Couldn't find package linux-backports-modules-generic


But everyone else seems to be having success.  I have gutsy backports enabled and SOME other apt-get installs have worked, but I have also gotten this same error with others, thus posting here.

---

