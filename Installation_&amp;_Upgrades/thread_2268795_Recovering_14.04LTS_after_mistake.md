---
title: "Recovering 14.04LTS after mistake"
date: 2015-03-11
forum: Installation &amp; Upgrades
---

### Post by dtree46 on 2015-03-11
My mistake.
There are 2 HD's on my pc. An 80gb and 1tb. 80 had W7 at one time; now blank. 1tb has Ubuntu.
Decided to use the 80 to install pc-bsd. Used 'gparted' to partition it while downloading pc-bsd.
While booting up this am, after the HP flash, a 'Non-System disk or disk error' appears and it stops.
Ubuntu is backed up on the 1tb using the stock backup.
I'm thinking I screwd 'grub' up.

Any ideas on how to solve this.

dl

---

### Post by oldfred on 2015-03-11
If 80GB drive was default in BIOS or was seen as sda when installing Ubuntu, it may have had grub installed to its MBR.

Many suggest disconnecting a drive if not sure, but you need to always use Something Else when installing with more than one drive, so you can control which drive grub2's boot loader is installed into.

Post link to summary report:
 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by dtree46 on 2015-03-11
Thanks for replying.

First 2 attempts did not work. Maybe the third will.
Used the second option. The instructions are rather different than suggested.
Will let you know.

dlw

---

### Post by dtree46 on 2015-03-11
No luck. 
[http://paste.ubuntu.com/10581053/](http://paste.ubuntu.com/10581053/)

---

### Post by oldfred on 2015-03-11
I do not know LVM which is what you have on sdb.

But the problem on sda, may be interfering with grub startup. Grub uses two ways to find boot partition. One is the set command and the other a search by UUID. The search will overide the set command if UUID partition is different, so you can still boot if drive order is different.

But to do search it has to review the other drive. And you have a corrupt partition table on sda.

 ```
/dev/sda4 ends after the last sector of /dev/sda
```

If no data to recover, you may just need to zero out MBR and then use gparted to create a partition.

      
 Zero out MBR only of sda, this erases any boot loaders and partition table in first sector of drive sda, but doubly sure you have correct drive. 
sudo dd if=/dev/zero of=/dev/sdX bs=512 count=1

---

