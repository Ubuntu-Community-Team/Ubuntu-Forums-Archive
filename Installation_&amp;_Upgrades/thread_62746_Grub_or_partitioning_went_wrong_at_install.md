---
title: "Grub or partitioning went wrong at install"
date: 2005-09-05
forum: Installation &amp; Upgrades
---

### Post by yesplease on 2005-09-05
I bought a second SATA hard disk for Ubuntu. Motherboard is MSI K8N Neo2 Platinum, where Neo2 means that it is nForce3 (duh).

Ubuntu could not install after I formatted 4 partitions with the install disk and it appeared the formats went wrong. Never mind about that now.

Eventually I erased the entire disk and chose an automatic partitioning scheme of the type Desktop machine. At install basesystem I chose Linux-368. 

I put Grub on /dev/sdb1 (WinXP is on sda1 according to the partition prog).

At rebooting I chose Ubuntu 2.6.10-5-386. This returned:

root (hd1.0) filesystem type unknown, partition type 0x7
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sdb1 r0 quiet splash
error 17 cannot mount selected partition

With a live CD I could read Grub/ device map and menu.list

(hd0) /dev/sda
(hd1) /dev/sdb


default 0
timeout 10

title Ubuntu, kernel 2.5.10-5-386
root (hd1,0)
kernel /boot/vmlinuz-2.6.10-5-386 root=/dev/sdb1 r0 quiet splash
initrd /boot/intird.img-2.6.10-5-368
savedefault
boot

(two other titles)

title Windows NT/2000/XP
root (hd0,0)
safedefault
chainloader +1

My questions are: is something wrong with menu.lst? How do I correct this? Please spell this out because with boot: rescue with the install disk I got a blue screen with one line on it and was only able to type exit :)  The manual says follow the instructions but I did not see any.

I wondered also if I have the default installation now.

Somewhere (after installation) I saw an unhappy face, instead of a smiley, at the swap partition. That doesnt seem right too.

I read the answers to a lot of dual boot questions before install, but I do not recognize my questions there. Anyway, it make no sense to me to reinstall before I know what went wrong.

---

### Post by yesplease on 2005-09-06
Perhaps I should try to reinstall Ubuntu and put grub on a floppy?

I would prefer to make my own partitions; is it advisable to make a 10 MB hidden partition at the beginning? I suppose that should it be bootable? and should this be free space or formatted as FAT or as FAT32?

---

### Post by yesplease on 2005-09-06
Edit: Perhaps I can make this tread helpfull for other beginners who worry and read a lot before install. Partitioning with the install disk went well, installation went well (I was happy that the network connections where configured automatically), the problem was with the bootloader Grub. During install Grub ask you if you want to put it on the mbr. If you dont want that you will get the option to put in on a floppy (among other choices). If you put grub on the a partition and it doesnt work at all (as in my case) you can put on a floppy afterwards with the method in:

[http://ubuntuforums.org/showthread.php?t=24113](http://ubuntuforums.org/showthread.php?t=24113)  ,

In this thread 4) mount /, /boot and swap means: select those partitions and restore the  filesystem (ext3), mount point (root, swap and home) and do not change the setting "leave files on partition, or something similar". I had to the whole thing twice, because the first time it did not finish writing grub on floppy. I set the BIOS to boot from floppy, and could boot windows, and Ubuntu. 

So, there is nothing wrong with the grub program. Now that you can boot from a floppy temporarely and search for a definte solution: search for "map grub menu.lst device.map" and read the grub manual.

---

