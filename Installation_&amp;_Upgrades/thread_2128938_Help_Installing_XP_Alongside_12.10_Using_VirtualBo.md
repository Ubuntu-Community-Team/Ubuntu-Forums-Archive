---
title: "Help Installing XP Alongside 12.10 Using VirtualBox"
date: 2013-03-24
forum: Installation &amp; Upgrades
---

### Post by electricmaster on 2013-03-24
I'm having a problem installing XP alongside Ubunu 12.10, and I'm wondering if anyone could help me.

What I basically did, was create a new partition (/dev/sda2) and then booted up Ubuntu. Since my computer doesn't have a CD drive, I obtained an ISO of my CD to install XP using VirtualBox. Next I created a VMDK link to my physical partition using the comand "*&#8203;VBoxManage internalcommands createrawvmdk -filename "/home/maclm01/.VirtualBox/WinHD.vmdk" -rawdisk [/dev/sda]("http://ubuntuforums.org/dev/sda") -partitions 2*." After that, I went into VirtualBox, created a new machine and installed Windows XP, which worked without any issue. Then, I went into the terminal and ran update-grub, which detected XP no problem and added it to the menu.

When I went to boot, however, instead of starting Windows, it rebooted the computer and went back to BIOS and GRUB. My first thought was that XP need Microsoft's boot manager, but I can boot just fine in the virtual environment. Even so, I tried most of the suggestions others had on the Internet, which was to try re-installing the boot manager using ms-sys, but all that did was corrupt /dev/sda2, so I had to start over, and now I'm at the same point I was before.
Anyone have any suggestions? I have no idea what to do next.

```
maclm01@maclm01-AO532h:~$ fdisk -l

Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders, total 312581808 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000b531b


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1            2048   245471231   122734592   83  Linux
/dev/sda2       245471232   308385791    31457280    7  HPFS/NTFS/exFAT
/dev/sda3       308385792   312580095     2097152   82  Linux swap / Solaris

```

[IMG]http://i.imgur.com/Tg6BRXc.png[/IMG]
[IMG]http://i.imgur.com/CCj8sCg.png[/IMG]
[IMG]http://i.imgur.com/TOq8BpJ.png[/IMG]

VirtualBox's guest additions aren't installed or anything like that. Any help would be much appreciated, thanks :)

---

