---
title: "Need Help Grub Repair-Triple Boot Ubuntu,CentOs,Windows"
date: 2016-04-24
forum: Installation &amp; Upgrades
---

### Post by kapilnegi1 on 2016-04-24
Hello all,


I'm new to Linux. I had a running system with Ubuntu and Windows in MBR mode. Recently I converted the MBR partition to GPT using EASUS partition manager. Then I installed Centos 7 in UEFI mode , after which everything went kaput.


1. I used grub repair tool "boot-repair". But it didn't fix the problem. Instead it made the Quick Boot menu (F11) very confusing. I see 4 entries for the same hard disk.
I've three Hard Disks.
sda-->120 GB SSD
sda2-->Windows 10
sdb --> 2TB
sdc --> 500GB
sdc2-->Ubuntu
sdc5 --> Centos

boot-repair
[http://paste.ubuntu.com/16020743/](http://paste.ubuntu.com/16020743/)


2. Then I followed the steps mentioned on 
[http://askubuntu.com/questions/88384/how-can-i-repair-grub-hw-to-get-ubuntu-back-after-installing-windows](http://askubuntu.com/questions/88384/how-can-i-repair-grub-hw-to-get-ubuntu-back-after-installing-windows)
But got stuck at grub-install /dev/sda (even tried with /dev/sdb and /dev/sdc/) where it says "grub-install: error: cannot find efi directory"

3. Moreover I've 4 options for same Hard Disk in Quick Boot Menu. On entring these option I boot into:
a) Centos -->Centos Boot Menu where I have Ubuntu also. But if I enter Ubuntu, I get 
[B]can't find 'linux'
can't find 'initrd'[/B]
b) ubuntu --> **grub Mode**
c) Windows Boot Manager --> redirects to centos boot menu
d) SATA6 --> grub rescue Mode
Attached is the image. 
Please see Centos option is working and I can boot into CentOs


4) I tried working from grub rescue mode, but ls command is not showing hd2 (sdc)

Can some please help me here. Thanks in advance.

---

