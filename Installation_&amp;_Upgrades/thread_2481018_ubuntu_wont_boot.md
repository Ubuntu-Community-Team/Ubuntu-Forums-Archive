---
title: "ubuntu wont boot"
date: 2022-11-16
forum: Installation &amp; Upgrades
---

### Post by maytemur on 2022-11-16
after update windows boot menu to gpt and uefi ,Ubuntu won@t boot anymore?

here is the report

[https://pastebin.ubuntu.com/p/k782Cpp2SR/](https://pastebin.ubuntu.com/p/k782Cpp2SR/)

thanks in advance

---

### Post by yancek on 2022-11-17
How did you update windows boot menu to gpt and uefi?  Your boot repair output shows 4 drives with windows partitions and one drive (sdb) with Ubuntu.  Which drive did you change?  Are some of these drives just data partitions?  Where is the windows OS installed?  You don't have Grub installed to the MBR of sdb and you don't have an EFI partition on that drive.  You have an efi partition on sdd (sdd1), is that the windows drive, sdd?  THere are no Grub files on the efi partition (sdd1) for Ubuntu and no efi partition on the Ubuntu drive (sdb).

You seem to have a Legacy install of Ubuntu but do not have Grub in the MBR of its drive (sdb).  If you set sdb to first boot priority in the BIOS, does it boot?

---

### Post by tea for one on 2022-11-17
Line 6 - libparted MBR boot code is installed in the MBR of /dev/sdb
Line 20 - Ubuntu 20.04 on sdb1

libparted mbr boot code is somewhat unusual.
How was that introduced?

Nevertheless, as you have four disks, I would consider:-
Each OS installed in UEFI mode on separate disks.
Each disk  with GPT and ESP.
Boot from one-time boot menu (no need to worry about boot management).
Create a shared partition on one of your other disks

---

