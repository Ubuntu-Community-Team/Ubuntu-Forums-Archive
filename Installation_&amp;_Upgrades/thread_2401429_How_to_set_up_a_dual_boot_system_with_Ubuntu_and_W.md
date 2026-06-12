---
title: "How to set up a dual boot system with Ubuntu and Windows 10?"
date: 2018-09-18
forum: Installation &amp; Upgrades
---

### Post by ankubra on 2018-09-18
[FONT=Arial]I tried to install Ubuntu 18.04.1 LTS on a computer that already runs on Win 10 Pro and there's no following option in the installation menu: "Install alongside Windows...". Why? I also disabled hibernation and pagefile on W10 (according to some tips published on Stack), and then I've created a new partition of 30 GB for Linux (disk is basic, not dynamic). That option still doesn't display. And it says "free space: 1 MB" in "Installation type". Pendrive is prepared correctly, Ubuntu occupies .ZIP file. What did I do wrong? Is there a way to solve that? FYI: I do not want to create partitions for Linux manually.[/FONT]

---

### Post by yancek on 2018-09-18
There is an official documentation page at the Ubuntu site at the link below specifically covering that subject.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2018-09-18
You cannot create partitions in Windows for Ubuntu, Windows does not know Linux formats like ext4, Ubuntu's default.

It should work if free or unallocated space.
But if older Windows 7 or upgrade from Windows 7, it may be BIOS /MBR and those default Windows installs used all 4 primary partitions allowed under MBR. You have to convert one primary to an extended partition which can hold many logical partitions.

You have to use live installer. Or Ubuntu ISO has to be extracted using an install.
       Also link on how to create a  bootable DVD or USB flash drive, using Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
[http://www.ubuntu.com/download](http://www.ubuntu.com/download)

Post this from Ubuntu live installer's terminal in live mode.
sudo parted -l

---

