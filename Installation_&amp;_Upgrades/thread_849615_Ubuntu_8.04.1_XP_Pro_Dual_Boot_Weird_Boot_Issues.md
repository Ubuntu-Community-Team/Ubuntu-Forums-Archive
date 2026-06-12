---
title: "Ubuntu 8.04.1 XP Pro Dual Boot Weird Boot Issues"
date: 2008-07-04
forum: Installation &amp; Upgrades
---

### Post by ananswam on 2008-07-04
Hi, first off I'd like to say I needed to install linux for a research project, and i was wary at first of having to use cryptic command line commands with a complete lack of support, but these forums have answered every question I've had, so thanks a lot to everyone who is on here solving everyone's problems!

I installed Ubuntu onto my hard drive (not using Wubi) from the CD (ubuntu 8.04.1 x86 32 bit) onto my Dell Latitude D630 which is running XP Pro. I partitioned the hard drive using guided-resize, and the install seemed to go fine. However, when I boot my system, the grub loads up giving me options to boot into Ubuntu or XP, and when I select XP, the screen goes blank and I have to force shutdown the computer. However, when I restart and do the same thing, XP goes to a "Windows did not start successfully" screen and gives me options to boot into Safe Mode, Safe Mode with Networking, etc. When I select "Start Windows Normally", XP boots fine. I'd appreciate any help on how to fix this issue. That is, why does XP not boot normally, but boot fine when it is starting from an unexpected shutdown?

---

### Post by logos34 on 2008-07-04
What does 

**sudo fdisk -l**

show? (i.e. if you have a recovery partition that might be causing the boot problem).  Check the windows entry at the bottom of /boot/grub/menu.lst too.

After you resize a windows partition it's supposed to run error checking automatically the next time you try to boot back into windows.  Maybe that didn't happen.  Try this:

boot into windows safe mode, open 'Run' dialog box, and enter:

**CMD**

at the subsequent prompt, type:

[B]chkdsk /r

[/B]It will run file system check with recover/repair option.

---

### Post by ananswam on 2008-07-04
Here is the output from sudo fdisk -l:

```
anandh@anandh-laptop:~$ sudo fdisk -l
[sudo] password for anandh: 

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x41ab2316

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           9       72261   de  Dell Utility
/dev/sda2   *          10       12447    99908235    7  HPFS/NTFS
/dev/sda3           12448       14593    17237745    5  Extended
/dev/sda5           12448       14497    16466593+  83  Linux
/dev/sda6           14498       14593      771088+  82  Linux swap / Solaris
```

I did run chkdsk \r as you said, but that did run when Windows started up the first time; I ran it again anyway, and it completed normally. I still have the same issue, however if I hibernate Windows, then Windows resumes fine when I select it from the grub menu. I realize that this makes no sense, but I'd appreciate if you could maybe provide me with something further to try.

---

### Post by logos34 on 2008-07-04
ok, so chkdsk did run. 

It's definitely not grub's fault, because it's chainloading windows, but something immediately freezes and you have to reboot.  I agree, it doesn't make sense that you can boot into xp on second try.  


(edit--misread the part about hibernation)

---

### Post by logos34 on 2008-07-04
I'd start thinking about backing up your files and doing an XP recovery/repair installation (I assume it's on the dell utility partition)

---

