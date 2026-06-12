---
title: "I can't install Windows 7 on a GPT hd with Ubuntu."
date: 2015-01-09
forum: Installation &amp; Upgrades
---

### Post by paracuentas666 on 2015-01-09
Hi everyone,

I've got a laptop with Ubuntu and some free space on it and I want to install Windows 7 so that I can have a nice dualboot. The problem is that when I try to install Windows, the installer says: 
> Windows cannot be installed on this disk. The selected disk is of the GPT partition style

I know that it is easier to install Windows first and then Ubuntu, but this is a friend's laptop that already has Ubuntu installed.

BTW, I also read that creating a NTFS partition with Gparted helps, but  in this case doing so or leaving free space doesn't make a difference.

Some people at online forums would recommend other people to set the UEFI boot on the BIOS, so I tried that and Windows 7 dvd (64bit) wouldn't even boot. So, **is there a way to install Windows 7 on a GPT hard disk with Ubuntu on it?**

---

### Post by ajgreeny on 2015-01-09
I think gpt partitions for windows will only work with a UEFI system, which maybe you do not have.  Show the output from terminal of command **sudo parted -l**

---

