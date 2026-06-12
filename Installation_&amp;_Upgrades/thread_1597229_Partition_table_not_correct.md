---
title: "Partition table not correct"
date: 2010-10-15
forum: Installation &amp; Upgrades
---

### Post by RD1945 on 2010-10-15
Hi all,

I'm trying to install Ubuntu Netbook 10.10 to an Asus EeePC 1000H (160GB HDD). (I know it will be slow because of Mutter/i945).
The usb stick boots just fine but when it comes to the partition part it goes wrong.

I have 3 partitions:
[LIST=1]
[*]Windows 7 (50GB)
[*]This will be Ubuntu Netbook (50GB)
[*]DATA (60GB)
[/LIST]

But the partition manager just shows 160GB of unallocated space.

I have tried to reboot and create the partitions with other software (even with GParted LiveCD) but the result is the same.

Please help as I can't install Ubuntu now.

---

### Post by srs5694 on 2010-10-15
Check [this page](http://www.rodsbooks.com/missing-parts/) I wrote on this symptom. You might or might not have the same cause. If you need more help, please post the output of "sudo fdisk -lu", typed at a Linux shell prompt (Terminal window). Please post the output between a [noparse]```
[/noparse] string and a [noparse]
```[/noparse] string for legibility.

Note, however, that I've been seeing reports recently of the same symptoms on drives that seem to be perfectly OK. It could be that something else is going on. I don't yet know the cause of the problems in these cases.

---

