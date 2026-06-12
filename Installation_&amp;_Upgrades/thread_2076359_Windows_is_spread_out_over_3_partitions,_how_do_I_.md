---
title: "Windows is spread out over 3 partitions, how do I set it up for dual boot"
date: 2012-10-25
forum: Installation &amp; Upgrades
---

### Post by Djalmahal on 2012-10-25
I've set up my computers with dual boot before but this HDD setup confuses me, this one is an Asus n56vz with 750GB HDD.

Basically Windows is spread out over 3 partitions, with one extra recovery partition (backed that one up).

Here is the gparted output in the first attachment
The second attachment is from inside the installer.

At this point I cancelled the installation for now to understand better what's going on.

The partition OS (sda3,280GB,100 GB used) contains Windows, Applications and the Download etc folder.
The partition DATA (sda4,393GB, 3 GB used) at this point contains only wo folders "$recyclebin" and "System Volume Information"
The partition SYSTEM (sda1, 200MB, 30MB used) contains only one folder called "EFI" with a lot of subfolders and carries the boot flag.

I would want a total of 150GB Windows, the rest Ubuntu, can be just in one partition (no need for seperate / and /home). Especially the SYSTEM partition confuses me.

Has anyone dealt with this kind of setup on ASUS computers? Is DATA necessary? And what about SYSTEM which has the boot flag?

Thanks for four replies....

---

### Post by Djalmahal on 2012-10-25
I've set up my computers with dual boot before but this HDD setup confuses me, this one is an Asus n56vz with 750GB HDD.

Basically Windows is spread out over 3 partitions, with one extra recovery partition (backed that one up).

Here is the gparted output in the first attachment
The second attachment is from inside the installer.

At this point I cancelled the installation for now to understand better what's going on.

The partition OS (sda3,280GB,100 GB used) contains Windows, Applications and the Download etc folder.
The partition DATA (sda4,393GB, 3 GB used) at this point contains only wo folders "$recyclebin" and "System Volume Information"
The partition SYSTEM (sda1, 200GB, 30GB used) contains only one folder called "EFI" with a lot of subfolders and carries the boot flag.

I would want a total of 150GB Windows, the rest Ubuntu, can be just in one partition (no need for seperate / and /home). Especially the SYSTEM partition confuses me.

Has anyone dealt with this kind of setup on ASUS computers? Is DATA necessary? And what about SYSTEM which has the boot flag?

Thanks for your replies....

---

### Post by newb85 on 2012-10-25
> **Djalmahal said:**
> The partition SYSTEM (sda1, 200GB, 30GB used) contains only one folder called "EFI" with a lot of subfolders and carries the boot flag.

Your Windows is installed in the newer UEFI instead of the older MBR, which brings about two key points
[list=1]
[*]You are not limited to four primary partitions.  You don't need to use an extended partition.  You can simply shrink the existing partitions and add more.
[*]You need to install Ubuntu in UEFI mode.  (Mixing these modes makes dual-boot not work right.)  Read up on this in the [official documentation]("https://help.ubuntu.com/community/UEFI").
[/list]

You probably already know this but it's generally safer to shrink your Windows partitions with Windows.  If you can't, at least defragment Windows partitions first.

---

### Post by oldfred on 2012-10-26
+1 on newb85 analysis.

Some threads with examples. You do have to use the 64 bit version of Ubuntu as it is the only one that supports UEFI.

Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)


The Arch site has a lot of technical details.
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)

---

### Post by Mark Phelps on 2012-10-26
Sorry, not personally familiar with EFI systems, so I can't advise you on those ... but I can tell you, if you're planning on shrinking the Win7 OS partition, do NOT use GParted or the Ubuntu installer to do that; instead, use the Win7 Disk Management utility.  It will give you less flexibility, but you won't risk the filesystem corruption that sometimes comes from using GParted or the Ubuntu installer to do that.

---

### Post by oldfred on 2012-10-26
Duplicate threads merged.

Please do not create duplicate threads. We all are volunteers and need to see what others have already contributed so we do not duplicate that info.

---

