---
title: "New ubuntu user with 2 problems"
date: 2005-03-06
forum: Installation &amp; Upgrades
---

### Post by lmbebo on 2005-03-06
Hi, I'm forced to write this from my laptop since ubuntu has seemed to cut off access to both linux and windows....

1)windows.
When I try to boot into windows, all i see is 
root (hd0,0)
savedefault
make active
chainloader +1

I have linux and windows xp booting up off the same HD.

2) linux
when I try to boot into ubuntu, the system stahls at starting the hotplug subsystem
modprobe error for inserting pciehp and shpchp saying operation not permitted and the system boot up stops there.

I was able to get in once with the recovery boot mode of grub, but not anymore.

edit: recovery mode let me back in again
reading off of another thread my partition table for my boot drive reads like this

/dev/hda1 *    HPFS/NTFS
/dev/hda2       Linux
/dev/hda3       W95 Ext'd (LBA)
/dev/hda5       Linux swap


thanks

---

### Post by lmbebo on 2005-03-06
[QUOTE=lmbebo]Hi, I'm forced to write this from my laptop since ubuntu has seemed to cut off access to both linux and windows....

1)windows.
When I try to boot into windows, all i see is 
root (hd0,0)
savedefault
make active
chainloader +1

I have linux and windows xp booting up off the same HD.

2) linux
when I try to boot into ubuntu, the system stahls at starting the hotplug subsystem
modprobe error for inserting pciehp and shpchp saying operation not permitted and the system boot up stops there.

I was able to get in once with the recovery boot mode of grub, but not anymore.

edit: recovery mode let me back in again
reading off of another thread my partition table for my boot drive reads like this

/dev/hda1 *    HPFS/NTFS
/dev/hda2       Linux
/dev/hda3       W95 Ext'd (LBA)
/dev/hda5       Linux swap


thanks[/QUOTE]
 well, I decided to try and just get back into windows

so i did fixmbr.... came up with error loading operating system
so i did fixboot ...same error
so I did  chkdsk, said no problems
tried the repair option, same result

stuck at this point now ....

---

### Post by Gary Powers on 2005-03-07
If yyou can get into the BIOS, change the hard drive setting from AUTO to LBA.  That solved the problem of booting into WinXP for me.  Not sure how it will impact the "boot in Ubuntu" problem.

Let us know if that works.  It's solved the same problem on two of my machines.

Gary

---

### Post by lmbebo on 2005-03-08
[QUOTE=Gary Powers]If yyou can get into the BIOS, change the hard drive setting from AUTO to LBA.  That solved the problem of booting into WinXP for me.  Not sure how it will impact the "boot in Ubuntu" problem.

Let us know if that works.  It's solved the same problem on two of my machines.

Gary[/QUOTE]
 thanks, but I kinda gave up on it.  I ended up having to do a low level format of the drive.  I think the problem was related to bad sectors on my HD.  Its that IBM 45 gig HD that caused such a ruckus a few years back.

I've gotten ahold of an old dell pc now, gonna see what parts I can toss into it and play with it.  Was thinking of trying to get it to use MythTV.

We'll see.

thanks for the help.

---

