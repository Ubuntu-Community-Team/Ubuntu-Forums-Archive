---
title: "help partionting!!!!!"
date: 2008-01-08
forum: Installation &amp; Upgrades
---

### Post by DV8shredder on 2008-01-08
No root file system is defined.

Please correct this from the partitioning menu

what do i do!!?? i keep getting this message no matter what i do and it just becomes an endless loop. btw, this is my sole os, i do not have any version of windows on my hdd if this helps. any help would be greatly appreciated!! thank you!!!

---

### Post by chewearn on 2008-01-08
> **DV8shredder said:**
> No root file system is defined.

Please correct this from the partitioning menu

what do i do!!?? i keep getting this message no matter what i do and it just becomes an endless loop. btw, this is my sole os, i do not have any version of windows on my hdd if this helps. any help would be greatly appreciated!! thank you!!!

Are you installing ubuntu, or trying to recover from crash?

---

### Post by Sef on 2008-01-08
Are you using the Live CD or the alternate cd?

---

### Post by Partyboi2 on 2008-01-08
If you are manually partitioning you need to define a /root partition
Highlight the partition you want to be /root and at the bottom of the screen on the left click on "edit partition" and then choose "Mount Point" and select / then click on ok.
See screenshot

---

### Post by DV8shredder on 2008-01-08
> **Partyboi2 said:**
> If you are manually partitioning you need to define a /root partition
Highlight the partition you want to be /root and at the bottom of the screen on the left click on "edit partition" and then choose "Mount Point" and select / then click on ok.
See screenshot

ok, that appeared to work, it went through the entire install process, however now upon startup i get a message that says loading grub menu error 18, and it does nothing. any ideas? thanks again guys.

---

### Post by Partyboi2 on 2008-01-08
You can try updating you bios to see if that works. 
If that does not work you can try reducing the size of the linux partition or you can create a /boot partition
see here for more info on grub error
[http://users.bigpond.net.au/hermanzone/p15.htm#18](http://users.bigpond.net.au/hermanzone/p15.htm#18)

---

### Post by DV8shredder on 2008-01-08
does everything here look ok..... i think i fixed that problem but im getting error 17 now

Disk /dev/hda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x1d161d15

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1          12       96358+  83  Linux
/dev/hda2           12159       12531     2996122+  82  Linux swap / Solaris
/dev/hda3              13       12158    97562745   83  Linux

Partition table entries are not in disk order

---

### Post by Partyboi2 on 2008-01-08
Make sure your hard disks are properly detected in your bios and set to auto, not lba, large or normal.
Another option is to use  supergrub 
[http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by DV8shredder on 2008-01-09
i set the hdd to auto, and all is working great! but when i startup it still wants a bootdisc for some apparent reason and ive now installed xp :( and the only way this works is if i have the ubuntu disc in and  i tell it to run hard disc for first time. can anyone tell me what the heck is going on!? this is so frustrating.

---

### Post by Partyboi2 on 2008-01-09
Is this the message you are getting?
> disk boot failure, insert system disk and press enter

---

### Post by DV8shredder on 2008-01-09
yes, thats the exact message im getting

---

### Post by Partyboi2 on 2008-01-09
See if this helps
[http://users.bigpond.net.au/hermanzone/p15.htm#DISK_BOOT_FAILURE_INSERT_SYSTEM_DISK](http://users.bigpond.net.au/hermanzone/p15.htm#DISK_BOOT_FAILURE_INSERT_SYSTEM_DISK)

---

