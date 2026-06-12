---
title: "message /grub/i386-pc/normal.mod' not found."
date: 2018-09-05
forum: Installation &amp; Upgrades
---

### Post by jk7275 on 2018-09-05
Hello 
I am getting [COLOR=#242729][FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]/grub/i386-pc/normal.mod' not found.  I have a computer that is 8-10 years old and the hard drive started to fail. I have  an external hard drive and I felt this would be a good time to try Linux. If this matters the mother board is an asrock n68-vgs3[/FONT]

[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]I install Ubuntu and put it on a USB drive. When I started I got an message about offset of 3584 so I used LVM. Everything install system reboots and I got that message about normal.mod not found and stuck in grub rescue [/FONT]

[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]When I use ls I see some folders and when I use ls to see what is in then I get unknown file system. There is one where instead of msdos0 it is lvm/ububuntu--root [/FONT]

[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]When I boot off the USB  and select try Ubuntu I can see the external hard drive and access it. Is there some configuration file I can edit [/FONT]


[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]I tried opensuse and i was able to boot into it but when it updates the os gets corrupt [/FONT]

[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]I downloaded Ubuntu 3 times and used a different program to make the usb and the results are the same, I also tried mint and I get normal.mod not found [/FONT]

[FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]I dont know where to start. Should I try another distro? This is an old computer and I prefer not spending money to get it up and running with windows. I was saving up to  on replace with something newer[/FONT]

 [FONT=Consolas, Menlo, Monaco, Lucida Console, Liberation Mono, DejaVu Sans Mono, Bitstream Vera Sans Mono, Courier New, monospace, sans-serif]I havent tried doing a manual  partition  as I dont how big to make the partitions and what file systems to use [/FONT][/COLOR]

---

### Post by oldfred on 2018-09-05
Your LVM install converted drive from normal partitions to LVM- logical volumes inside one large partition. LVM most often used with servers, but if you want full drive encryption, you have to use LVM.
       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM)

If installing to external drive, you must use Something Else install option and be sure to install grub boot loader to external drive on partitioning page. And then set system to boot from that external drive first.

Your error is typical of system trying to boot from the wrong version of grub or from a version of grub in MBR from an old install looking for partitions that now do not exist as you did not write a new grub to MBR.

If you want more details, and a gui way to fix it Boot-Repair usually works, but often best to have someone review configuration first, so just post link to summary report.
        
 May be best to see details, use ppa version with your live installer or any working install,  not older Boot-Repair ISO:
Just run the summary report, the auto fix sometimes can create more issues.
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

