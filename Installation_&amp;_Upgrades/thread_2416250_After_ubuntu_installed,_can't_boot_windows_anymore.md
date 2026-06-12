---
title: "After ubuntu installed, can't boot windows anymore"
date: 2019-04-07
forum: Installation &amp; Upgrades
---

### Post by sv.123 on 2019-04-07
Hello all

After Ubuntu 18.04.2 LTS install, I can't boot or access Windows10 anymore on a Dell laptop. Tried to use windows recovery but no luck recovering data.

Here is what fdisk ourput is showing from ubuntu. Any ideas?

Disk /dev/sda: 465.8 GiB, 500107862016 bytes, 976773168 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disklabel type: gpt
Disk identifier: xxxxxxxxxxxxxxx


Device       Start       End   Sectors   Size Type
/dev/sda1  2099200   3123199   1024000   500M EFI System
/dev/sda2  3123200   3385343    262144   128M Microsoft reserved
/dev/sda3  3385344 842356312 838970969 400.1G Microsoft basic data

Thanks so much.
SV

---

### Post by Rubi1200 on 2019-04-08
Hi and welcome to the forums :-)

Please post the results of the boot info summary from a liveCD/USB (see link in my signature).

Thanks.

---

### Post by yancek on 2019-04-08
Did you install Ubuntu or are you simply using it on a DVD/USB?  The fdisk output you posted shows no sign of any Ubuntu/Linux system installed.  Might you have another drive on which you installed Ubuntu?  Post the boot repair output suggested and use the Create BootInfo Summary option, do not try to make any repairs.

---

