---
title: "Boot.ini"
date: 2005-07-09
forum: Installation &amp; Upgrades
---

### Post by paladinhugo on 2005-07-09
I've installed Ubuntu Linux in a partition of my hard drive. I want to edit the boot.ini file for a dual Windows XP and Ubuntu Linux boot.

This is the line for Win XP boot:

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Professional" /fastdetect

What should I put for the Ubuntu Linux? All I know is that the partition of the Ubuntu Linux installation is number 6.

---

### Post by mingus on 2005-07-09
Here are two sources I picked up with a quick wiki search.  There are *many* such instructions if you google the question, each with a different twist.  

[https://wiki.ubuntu.com/WindowsDualBootHowTo](https://wiki.ubuntu.com/WindowsDualBootHowTo)
[http://www.geocities.com/epark/linux/grub-w2k-HOWTO.htm](http://www.geocities.com/epark/linux/grub-w2k-HOWTO.htm)

Without getting into a lot of theory, essentially what is needed is for the Linux boot loader to reside in the same partition as does the W$ loader and for ntldr to be able to find it in boot.ini.  There are 4 steps necessary to do this:

1.  Install the grub boot loader to the Ubuntu root (/) partition (unless you have placed the /boot directory on a separate partition, in which case you install grub there).

2.  In Ubuntu create a file which is a copy of the grub boot loader; the file needs to be on media that Windows can also read, either a floppy or a FAT32 partition.  (Most instructions don't include using a CD, but that should work too).

3.  In Windows copy the grub file to C:\ from the media above.

4.  Add a menu entry and pointer in boot.ini.

---

### Post by paladinhugo on 2005-07-09
First time I've installed Ubuntu, I couldn't install grub on Win XP partition. I got an error and I was unable to do it. Although, I've reinstalled Ubuntu and this time I was able to install grub in Win XP partition. My problem is solved for now.

   I had already seen those two sites. I guess I don't have the knowledge to follow those instructions.

Thanks anyway.

---

