---
title: "ubuntu 6.06 does not recognize CentOS file system"
date: 2007-09-25
forum: Installation &amp; Upgrades
---

### Post by davidstrug on 2007-09-25
Hi everyone,

I have a  PC running CentOS 4.4 installed on hda2 - master  partition. After  installing Ubuntu 6.06 on another hdb - slave partition, the computer can be rebooted only in Ubuntu and doesn't recognize existing file system on hda with CentOS on it.  I couldn't mount hda with mount command, also it appears in 'disks' GUI as unknown file system. hda1 is mountable and contains CentOS grub files (I don't know why hda1 has it. The hda1 is only 100 MB compare to hda2 40Gb where I installed CentOS). I did edit Ubuntu's GRUB menu file to include CentOS kernel by copy paste method but when booted 'kernel panic...'  message appeared. It happened probably because the boot sequence points on hda1 and not on hda2 where CentOS is located. When I manually changed address from hd0,0 to hd0,1  I still couldn't boot the machine in CentOS.  I will appreciate any help or advise of how to:

Make CentOS bootable again and 
How to get the files out of hda1 (I made a terrible mistake not to backup my data before Ubuntu installation)  

Thanks again,
David

---

