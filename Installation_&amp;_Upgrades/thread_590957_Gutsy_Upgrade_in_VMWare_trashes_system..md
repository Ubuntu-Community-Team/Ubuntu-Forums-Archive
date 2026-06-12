---
title: "Gutsy Upgrade in VMWare trashes system."
date: 2007-10-25
forum: Installation &amp; Upgrades
---

### Post by bolucpap on 2007-10-25
I am at the moment trying to upgrade my Ubuntu installation from Feisty to Gutsy. I am running Feisty as a guest in an XP VMWare Host. Everything is fine with VMWare tools working perfectly. After the first boot following the upgrade I get: 

e2fsck: Bad magic number in super-block while trying to open /dev/hdb1
The superblock could not be read or does not describe a correct ext2
filesystem.  If the device is valid and it really contains an ext2
filesystem (and not swap or ufs or something else), then the superblock
is corrupt, and you might try running e2fsck with an alternate superblock:
    e2fsck -b 8193 <device>

Unfortunately, my /usr is supposed to be mounted on that device, so the bootup cannot continue because all the necessary stuff is there. When I boot up with the Dapper live CD, I can see all hard drives fine and mount them, and all the data is intact. If I hit esc during grub and boot from the previous (2.6.20) kernel, the system starts up fine. 

Unfortunately this is a reproduction of a previous error. The first time I tried to upgrade to gutsy everything was fine after the first reboot, but then I installed VMWare tools and I started getting that error. I rolled back to Dapper (by restoring the virtual disk file from backup), upgraded to Edgy and then Feisty with no problems whatsoever, installed VMWare tools, which worked great, then after upgrading to Gutsy I hit the wall. 

At another location I have a clean Gutsy install with VMWare tools (same version) installed which works real well, so I know there is no inherent conflict between Gutsy and VMWare tools.

It's all very weird, I am currently practicing and building my skills on a virtual ubuntu to prepare myself for the big switch to a real world ubuntu box, but I need to know what to do before I switch because it would really suck to have that problem on a non virtual box.

---

