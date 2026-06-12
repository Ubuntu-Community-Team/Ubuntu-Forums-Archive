---
title: "No grub screen after Microssoft update boots straight to windows 10"
date: 2016-09-26
forum: Installation &amp; Upgrades
---

### Post by jammydodger2 on 2016-09-26
Hi All 
Have Ubuntu Mate and Windows 10 on dual boot all was working well until Windows Update (some kind of micro-soft account synch)
Lost grub boot screen, now laptop boots straight into Windows 10 (fast boot off ,secure boot off)
Tried boot repair disc from Live Mate CD and tried repair no luck 
Gparted from live CD

Any help appreciated as dont wont dont make anything worse
 Pastebin Boot Repair[URL="http://paste2.org/PI8UamMJ"] 
[/URL][http://paste2.org/PI8UamMJ](http://paste2.org/PI8UamMJ)

---

### Post by kc1di on 2016-09-26
hi jammydodger2, 
Windows update must have written over the boot file.  you should be able to restore in by running boot-repair. 
you can find out about it here. 
[https://help.ubuntu.com/community/Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")
good luck

---

### Post by oldfred on 2016-09-26
Your sda1, now says it is a bios_grub partition. But it also says it is FAT32 formatted.

The bios_grub partition is used only by Linux for BIOS booting on gpt partitioned systems.
UEFI boots from a FAT32 formatted partition that must be flagged as boot if using parted or gparted. Or if using gdisk you use code ef00 (bios_grub is ef02).

So somehow your ESP - efi system partition which is sda1 has the wrong flag. Use gparted and change flag to boot with right click on that partition.
Also your fstab says it is the efi partition.

---

