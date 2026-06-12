---
title: "Sony Vaio SVE11126CVW - Boot Problems - Boot Screen then Black Screen"
date: 2013-04-16
forum: Installation &amp; Upgrades
---

### Post by SaiyanEye on 2013-04-16
Okay, this is my Dad's netbook.  He purchased this in the Phillipenes I don't know what happened to his Windows 8 install, I tried booting and it would lag so bad I couldn't do anything to try to fix it.  Tried to do his Windows recovery.  It was corrupted.  I don't know what he did.  

I convienced him to switch to Linux :D, telling him that I could install Ubuntu on his laptop with no problems and it would take 30 min after downloading Ubuntu 12.10.  I was wrong.  It is now day two and I am still trying to figure out how to get Ubuntu working on his laptop.


I then installed it from the USB drive (will not boot from USB in Legacy mode only UEFI mode).  The Live USB boots fine, perfectly.   I tried installing Ubuntu normally, and I can't even get Grub to work.  I tried boot-repair numerous times.  For some reason, I decided for sh!ts and giggles, to install in OEM mode.  Guess what, now I have GRUB.  It booted into GRUB, I then seen the Ubuntu loading screen.  [COLOR="#696969"](I was thinking YAY!  It worked!)[/COLOR]   Then it goes to a black screen after showing the Ubuntu loading screen.  The HDD light flashes at a slow steady pace.  Over and over.

HELP!  I am getting desperate, iritated and wondering why I am having so much trouble.  I have never had this much trouble installing Ubuntu.  I have installed Ubuntu it seems like a hundred times with no problems!  I am stumped!
:confused:


```
Scanning for Btrfs filesystems
fsck from util-linux 2.20.1
fsck from util-linux 2.20.1
dosfsck 3.0.13, 30 Jun 2012, FAT32, LFN
/dev/sda2: clean, 170119/30285824 files, 2658174/121136128 blocks
/dev/sda1: 14 files, 6188/95491 clusters
 * Starting mDNS/DNS-SD daemon[164G[ OK ]
Skipping profile in /etc/apparmor.d/disable: usr.bin.firefox
Skipping profile in /etc/apparmor.d/disable: usr.sbin.rsyslogd
 * Starting AppArmor profiles       [170G 
 * Starting bluetooth daemon[164G[ OK ]
[164G[ OK ]
speech-dispatcher disabled; edit /etc/default/speech-dispatcher
saned disabled; edit /etc/default/saned
 * Stopping System V initialisation compatibility[164G[ OK ]
 * Starting System V runlevel compatibility[164G[ OK ]
 * Starting [164G[ OK ]
 * Starting [164G[ OK ]
 * Starting ACPI daemon[164G[ OK ]
 * Starting anac(h)ronistic cron[164G[ OK ]
 * Starting [164G[ OK ]
 * Starting [164G[ OK ]
 * Starting save kernel messages[164G[ OK ]
 * Starting [164G[ OK ]
 * Starting [164G[ OK ]
 * Starting [164G[ OK ]
 * Starting configure virtual network devices[164G[ OK ]
 * Starting configure network device security[164G[ OK ]
 * Starting automatic crash report generation[164G[ OK ]
 * Starting regular background program processing daemon[164G[ OK ]
 * Starting deferred execution scheduler[164G[ OK ]
 * Starting network connection manager[164G[ OK ]
 * Starting CPU interrupts balancing daemon[164G[ OK ]
 * Stopping [164G[ OK ]
 * Starting LightDM Display Manager[164G[ OK ]
 * Stopping cold plug devices[164G[ OK ]
 * Stopping log initial device creation[164G[ OK ]
 * Starting enable remaining boot-time encrypted block devices[164G[ OK ]
 * Starting save udev log and update rules[164G[ OK ]
 * Stopping save udev log and update rules[164G[ OK ]
 * Stopping enable remaining boot-time encrypted block devices[164G[ OK ]
 * Stopping save kernel messages[164G[ OK ]
```

Here is the boot log if that helps...

What else can I post if you guys need it.

---

