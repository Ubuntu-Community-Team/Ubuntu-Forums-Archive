---
title: "Grub2 keeps getting wiped out by windows"
date: 2009-12-07
forum: Installation &amp; Upgrades
---

### Post by 2quick on 2009-12-07
Hi all!

I am having a bit of a problem with windows wiping out grub everytime I boot into windows then reboot back into linux(Ubuntu 9.10).  The issue started after a Windows Vista update took place.  I did not have this issue after the initial install or with 9.04.  The computer is an Asus G50V laptop.  Upon reboot I get the error:

Grub loading.
no module name found.
Aborted.  Press any key to continue.

So I boot via a Super Grub Disk back into Linux.

the only way to get grub back that has worked for me is using these commands:

```
cd /
sudo grub-install --root-directory=/ dev/sdX
sudo update-grub
sudo update-grub2
sudo reboot
```

This is a bit of info about the HD layout:

```
laptop:~$ sudo fdisk -l

Disk /dev/sda: 320.1 GB, 320072933376 bytes
4 heads, 44 sectors/track, 3551945 cylinders
Units = cylinders of 176 * 512 = 90112 bytes
Disk identifier: 0xfdfbcdb6

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          12     1775977   156284928    7  HPFS/NTFS
/dev/sda2         1775989     3551942   156283952    f  W95 Ext'd (LBA)
/dev/sda5         1775989     3255250   130174972    7  HPFS/NTFS
/dev/sda6         3255251     3348340     8191920   82  Linux swap / Solaris
/dev/sda7         3348341     3440969     8151330   83  Linux
/dev/sda8         3440970     3551942     9765602   83  Linux

```

Can someone help me in getting this right?  Thank you so much for the assistance!

---

### Post by phillw on 2009-12-07
Hi,

This is a reported problem on certain brands of computer. Can you post back your make ?

Regards,

Phill.

---

### Post by 2quick on 2009-12-07
> **phillw said:**
> Hi,

This is a reported problem on certain brands of computer. Can you post back your make ?

Regards,

Phill.

I have an Asus G50V laptop

I previously had Ubuntu 9.04 installed and I did not have this issue.  Also 9.10 was working fine until I did a large update for Windows Vista was installed.  I should have included that information in the original post, sorry!

---

### Post by phillw on 2009-12-07
Hmm, the Asus is not on the list of affected computers. However the symptoms point to the same issue whereby one of the recovery software software packages is over-writing the MBR. For once, we can't blame M$ for this, it's only doing as it is told !!

The things to go 'a hunting for' are listed in this thread - which also leads to another couple of threads. There are several possibilities. Basically, you're looking to disable a backup 'Service' from within Win environment.

[http://ubuntuforums.org/showthread.php?t=1338439](http://ubuntuforums.org/showthread.php?t=1338439)

If you'd post back with how you get on, it will allow us to 'look out' for similar issues with Asus machines.

Regards,

Phill.

---

### Post by 2quick on 2009-12-08
Looks like I found the culprit.  It was Norton Ghost running in the background, that I had just recently installed.  I disabled it during startup through msconfig and no more trouble.  Thanks for the links!

---

### Post by semacore on 2010-04-30
I have the same issue with Windows 7 on a dell 

I get this...

no module name found
Aborted. Press any key to exit.
Intel(R) Boot Agent GE v1.3.35
Copyright (C) 1997-2009, Intel Corporation

PXE-E61 : Media test failure, check cable
PXE-M0F : Exiting Intel Boot Agent.
Operating System not found


I did find this as a solution but it seems to be a temporary solution at best:
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

### Post by oldfred on 2010-04-30
See these sites:
[http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR](http://sourceforge.net/apps/mediawiki/bootinfoscript/index.php?title=Boot_Problems:Windows_Writes_To_MBR)
[http://www.supergrubdisk.org/wiki/WindowsErasesGrub](http://www.supergrubdisk.org/wiki/WindowsErasesGrub)
HP ProtectTools, Dell Recovery, and a few others write into MBR meierfra.
[https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941](https://bugs.launchpad.net/ubuntu/+source/grub2/+bug/441941)
[https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all](https://bugs.edge.launchpad.net/ubuntu/+source/grub2/+bug/441941?comments=all)
Dell Media direct issues with MBR
[http://ubuntuforums.org/showthread.php?t=923576](http://ubuntuforums.org/showthread.php?t=923576)

---

