---
title: "My final thoughts on Grub2"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by degarb on 2010-12-18
I have wrestled with grub2 for a week.  I have over 100 pages pasted into my google docs, documenting grub2.  This is insanity!!

I tried 3 installs (two ubuntu disks, checking checksums and scratches) on external drive. but grub2 is junk. I see multiple complaints on boards that grub2 won't load an OS not on grub drive. At least, with ide bios gen computer and usb hard drive. I think the developers are missing this because they are setting the other drive as the boot drive. Not thinking, some people want grub in the primary master and linux on the usb drive. It doesn't work. 

I was forced to install debian mint on sda (the installer doesn't hang like Ubuntu's), along side windows, with a limited drive size. I hoped that would pickup the external drive's lmde install. It did. Just won't boot to it. 

Moreover, grub is one thing in linux that is actually harder than 10 years ago. I am not the first to say this. I don't see any way of changing the grub menu. The cfg file is a mess, and it instructs no editing. WTH? Then, grub needs to be OS independent and not dependent on an install: BY DEFAULT!

---

### Post by oldfred on 2010-12-18
Grub2 does have a higher learning curve. It is trying to accommodate all the new systems with drives over 2TB, LVM, RAID and anything developed in the last few years as grub legacy was not maintained at all. Each distribution may have made minor tweaks to old grub to work with their install but not then with others.

If old grub works for you, you still can use it. Ubuntu boots fine with it (at least for now). If you do not have nor plan any new hard ware old grub should be just fine.

The way to edit grub2 parameters (the top portion of grub legacy's menu.lst) is in /etc/default/grub. If you want to customize entries you do that with:
```
gksudo gedit /etc/grub.d/40_custom
```If you want you can totally turn off all the automatic probing of other systems and maintain your menu boot stanzas in 40_custom. This was like in menu.lst adding entries before or after the automagic area.


 GRUB 2  has three main parts plus a boot loader installed to the MBR:

   1. /etc/default/grub - the file containing GRUB 2 menu settings.
   2. /etc/grub.d/ - the directory containing GRUB 2 menu creating scripts.And a place for totally custom entries 40_custom.
   3. /boot/grub/grub.cfg - the GRUB 2 configuration file, not editable.

You do not have to save all the grub2 data. There are many posts here in the forums and they have finally updated a manual. (I just save links to drs305's posts as they all are very good).

[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://www.gnu.org/software/grub/manual/](http://www.gnu.org/software/grub/manual/)
The Grub 2 Guide (formerly Grub 2 Basics)
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by I'mGeorge on 2010-12-18
Also if you want your boot loader to look really fancy check out [BURG]("http://ubuntuguide.net/decorate-grub-2-boot-loader-using-burg"), a GRUB 2 extension

---

