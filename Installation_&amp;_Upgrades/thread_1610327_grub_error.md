---
title: "grub error"
date: 2010-10-31
forum: Installation &amp; Upgrades
---

### Post by pjmlmas on 2010-10-31
hi:

I had hard drive = 2 partition, 1 being extended

I had two ubuntu instances+swap+fat on extended and XP on primary


I moved a partition = success
I create a new partition = success
I installed new ubuntu instance ->  fail on restart->
I saw sector error on screen on restart.

So, Grub has lost 1 existing ubuntu instance and could not create new entry for new ubuntu instance.

Read on forum just boot from Live CD and execute some grub cmds from terminal???

---

### Post by 73ckn797 on 2010-10-31
See if this will help:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

---

### Post by pjmlmas on 2010-10-31
I ran the grub repair option from working ubuntu instance - aok now...

Still, should I be concerned with sector error message?
If MBR were to go fubar...the partitions would be ok? However, could I still boot to them somehow?

---

### Post by 73ckn797 on 2010-10-31
> **pjmlmas said:**
> I ran the grub repair option from working ubuntu instance - aok now...

Still, should I be concerned with sector error message?
If MBR were to go fubar...the partitions would be ok? However, could I still boot to them somehow?
That is doubtful so I would not be too concerned. You, typically, will be the only reason for a grub/mbr problem, unless the HD is faulty.

---

### Post by pjmlmas on 2010-10-31
ok, tried to again install new 10.04 instance, same problem...

now worried.

this is what is see after repairing grub on boot menu

2.6.32-25 /sda5
XP
ubuntu 10.04.1 LTS /sda10
2.6.32-25 g /sda7
2.6.32.24 g /sda7

Naive questions - max size of MBR ok to handle all instances?
Drive setup - 
/dev/sda1 - ntfs - xp
/dev/sda3 - extended
//dev/sda5 - swap -shared
//dev/sda6 - fat32
//dev/sda10 - ext4 - attempt new instance - failing
//dev/sda9 - ext 4 - good ubuntu instance
//dev/sda7 - ext 4 - good ubuntu instance
//dev/sda8 - old swap

Did this a few times w/o problems.
Specify the partition manual
Choose sda10, ext4, format, use as /
Choose sda5, swap
forward, format, install, restart now, click button
sector error at .....(dont remember)....
restart
grub is fubar.
fix grub
sda10 instance is fubar

---

### Post by 73ckn797 on 2010-10-31
Install grub to sda1 or go into bios on boot up and change the boot drive to sda10.

---

