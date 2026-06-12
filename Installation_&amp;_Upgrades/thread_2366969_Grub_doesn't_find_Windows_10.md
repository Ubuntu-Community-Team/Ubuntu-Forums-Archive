---
title: "Grub doesn't find Windows 10"
date: 2017-07-24
forum: Installation &amp; Upgrades
---

### Post by 4l3x2 on 2017-07-24
Good morning.
I've just installed Ubuntu 16.04.2 on a new laptop of a friend/colleague of mine.

I have a strange issue with the boot loader:
if I select in the bios UEFI mode the pc start automatically Windows, if I select Legacy it starts automatically Ubuntu without showing the selection menu.

If I try to open the terminal window giving:
sudo update-grub

it doesn't find any of the Windows partitions/kernel, so I mounted the partition where Win 10 is installed and gave the same line again with no success.

How can I make grub recognize the Win 10 partition without having to change the bios settings every time?
Thank you very much.

---

### Post by yancek on 2017-07-24
You didn't read the Ubuntu documentation at the page below on dual booting with windows 10.  The proper way of doing it is explained at their site.  You had a windows 10 install using UEFI/GPT and you installed Ubuntu with the oldr MBR/Legacy boot.  They conflict and until you do a UEFI install of Ubuntu, the only way you will be able to boot is the way you are now.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2017-07-24
Since the BIOS boot version of Ubuntu install to a gpt partitioned drive does not convert it to MBR as Windows would, you can reinstall grub2's boot loader and convert install to UEFI boot.
Probably easiest with Boot-Repair. If it complains about something from running inside your Ubuntu install use the Ubuntu live installer and add Boot-Repair to it.

Do not run auto fix. You have to use the advanced mode and full uninstall/reinstall of grub2's boot loader.
       Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot, only use ppa download into Ubuntu live installer.
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
[https://sourceforge.net/p/boot-repair/home/Home/](https://sourceforge.net/p/boot-repair/home/Home/)

---

