---
title: "Re-installing windows without removing linux distros (Tri-Boot)"
date: 2014-06-04
forum: Installation &amp; Upgrades
---

### Post by ajroxx16 on 2014-06-04
Hello, i am planning to re-install windows 8 in my laptop. I have xubuntu x64  and Elementry x64 (Ubuntu Base) installed too along with windows. 
Will re-installing windows and repairing xubuntu help in retaining my current boot order, i.e Elementry>windows>ubuntu ?

---

### Post by oldfred on 2014-06-04
UEFI or BIOS?

May be best to see details and good backups are always suggested.
Post link to BootInfo report:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by ajroxx16 on 2014-06-05
Uefi

---

### Post by oldfred on 2014-06-05
Do not know if Windows will overwrite efi partition. And Windows often likes to ignore Linux partitions when rewriting partition table.
So backup efi partition and partition table. If you change partition table at all then you cannot restore the backup of the partition table.
Have the Ubuntu live installer handy to make various fixes if necessary, just like you have a Windows repair flash drive handy to fix Windows issues.

Use gdisk & cgdisk or sgdisk to make backup of gpt partition table.
 [http://www.rodsbooks.com/gdisk/](http://www.rodsbooks.com/gdisk/)

[http://www.rodsbooks.com/gdisk/cgdisk-walkthrough.html](http://www.rodsbooks.com/gdisk/cgdisk-walkthrough.html)

---

