---
title: "NTFS rw support?"
date: 2005-10-25
forum: Installation &amp; Upgrades
---

### Post by gfournier on 2005-10-25
Hi! I've heard that there is an stable version of the driver for writing on ntfs partitions, but I don't remember where I read about it :confused: 
The question is about the avaible posibilities of mounting a ntfs partition for rw and share it on my LAN.
I know that you can change the file system from ntfs to fat32 but I don't like to do that. I wonder if wine could do that :rolleyes: 
Thanks for your answers!!

PD: How do you see the packages installed in apt?

---

### Post by jasmuz on 2005-10-26
There is support for writting to NTFS partitions in the kernel, but you will have to recompile or download captive-ntfs, wich allows you to write to ntfs partitions (warning; its very confusing).

To see all the packages installed in the system by apt, do this
sudo apt-cache pkgnames

---

### Post by gfournier on 2005-10-26
So I heard!! Thanks! Linux is great!! :KS 
I have two more questions... captative-ntfs is diferent from the support included in the kernel? I read that writing a ntfs partition with captative could be a little risky... 
So I think they are different and I'd like to recompile my kernel... So what I have to do? :confused: 
Thanks again!!

:D Enjoy unbuntu :D

---

