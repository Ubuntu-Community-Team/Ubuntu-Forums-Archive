---
title: "Installation option"
date: 2007-12-27
forum: Installation &amp; Upgrades
---

### Post by karthik_jce on 2007-12-27
Hi,

I have two sata hard disks disk A and disk B. 

disk A is a 250 GB hdd and has windows XP

disk B - did not have any OS - a new harddisk.

I entered into CMOS and changed the boot order as follows:

[INDENT][INDENT][LIST=1]
[*]CDROM
[*]DISK B
[*]DISK A
[/LIST][/INDENT][/INDENT]

then I installed Ubuntu 7.04 to disk B. My whole idea was to avoid installing the grub boot loader from getting installed on to my 250 GB windows harddisk.

But after installing and when I boot I see that Grub has got installed and shows my windows XP operating system also. I see this grub bootloader even if I change the boot sequence as [LIST=1]
[*]CDROM
[*]DISK A - windows XP 
[*]DISK B
[/LIST]

Now I am not sure in which disk's MBR has the GRUB been installed. so that even if I reinstall windows at some later point of time I should not lose my linux.

Please clarify.

Regards
Karthigeyan

---

