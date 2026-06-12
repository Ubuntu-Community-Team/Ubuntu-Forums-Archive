---
title: "Ran boot-repair PC still doesn't boot"
date: 2012-10-10
forum: Installation &amp; Upgrades
---

### Post by ngahiker on 2012-10-10
Mythbuntu 12.04 - I attempted to move one data drive to a different sata  port, now the system doesn't boot (all drives are back to the original  sata ports).

I ran boot-repair (using 12.04 live CD, ran the recommended repair) No change, the system doesn't boot.

I can boot the system off a rescue CD, choosing to boot off the correct boot drive. It then runs normally.

From boot-repair:  [http://paste.ubuntu.com/1272150/](http://paste.ubuntu.com/1272150/)

boot-repair reports:
"The boot files of [Ubuntu 12.04.1 LTS] are far from the start of the disk"

Do I have to create a new boot partition (at the start of the disk) to resolve this?

Thanks

---

### Post by Bashing-om on 2012-10-10
How bout this as only required to re-install grub:
If Ubuntu is operating normally, boot into the working installation and run the following command from a terminal.  

[LIST]
[*]***X*** is the *drive* (letter) on which you want GRUB to write the boot information. Normally users should **not**  include a partition number, which would produce an error message as the  command would attempt to write the information to a partition.  
sudo grub-install /dev/sdX  # Example: sudo grub-install /dev/sda
[/LIST]
This  will rewrite the MBR information to point to the current installation  and rewrite some GRUB 2 files (which are already working). Since it  isn't done during execution of the previous command, running sudo update-grub after the install will ensure GRUB 2's menu is up-to-date. 
 
**[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)**

Links on this howto for additional help. Post back if additional help needed.

[INDENT]regards <==BDQ


[/INDENT]

---

### Post by oldfred on 2012-10-11
We seem to be seeing this type of issue on very large / (root) partitions. Yann in Boot repair highlights it and one solution is a separate small /boot within the first 100GB. 

But I normally install with the entire / in a 25GB partition and have not had any real issues. It also may be related to BIOS issues but we cannot seem to tell. Is BIOS in AHCI, IDE, or LBA or large or whatever your BIOS may call it. If IDE it may be emulating the old IDE drives that can only boot from the first 137GB of a drive.

I have often suggested just shrinking / to 100GB or less and for many that seems to have worked. You can then use rest of drive as /home or for data partitions.
```
=================== sdb1: Location of files loaded by Grub: ====================

           GiB - GB             File                                 Fragment(s)

 872.167018890 = [COLOR=Red]936.482205696 [/COLOR] boot/grub/core.img                             1
 872.186882019 = 936.503533568  boot/grub/grub.cfg                             1
   0.907226562 = 0.974127104    boot/initrd.img-3.2.0-23-generic               2
   1.875976562 = 2.014314496    boot/initrd.img-3.2.0-29-generic               2
   9.555664062 = 10.260316160   boot/initrd.img-3.2.0-30-generic               2
  10.157226562 = [COLOR=Red]10.906238976[/COLOR]   boot/initrd.img-3.2.0-31-generic               2
```

---

### Post by ngahiker on 2012-10-11
Update - no progress so far. 

BIOS is set to use AHCI

I shrunk sdb1 to 99 GB, then ran boot-repair. No luck. Tried boot-repair again selecting "ATA disk support (solves the [out of disk] error)" - ouch that made it worse. Grub couldn't see the drive.  Recovered back to where the system will boot if I boot using the System Rescue CD.

With the system running tried (no errors reported by grub):
update-grub
grub-install /dev/sdb
grub-install --recheck /dev/sdb

I still see the same issue: stuck at a flashing curser at boot
The last Boot repair run: [http://paste.ubuntu.com/1274025](http://paste.ubuntu.com/1274025)

---

### Post by oldfred on 2012-10-11
Script now looks normal to me. All boot files are close together.

There was another thread where the user could not boot because of an issue on another drive. I do believe grub still scans drives on a boot. And issues on other drives may be a problem. 

Since you have xfs as the format of the other drives, I wonder if grub has an issue?

This is just an experiment on my part. 
I might try adding the xfs.mod file to the grub configuration even though grub should not need it.

mount /dev/sdb1 /mnt
gksu gedit /mnt/boot/grub/grub.cfg
#May have to do this first as it is write protected also:
sudo chmod +w /mnt/boot/grub/grub.cfg
#Or even this first:
sudo chmod 777 /mnt/boot/grub/grub.cfg

at line 161 you have this:
insmod ext2
#add this just before or after
insmod xfs

My hope is that the search then may work. 

Another alternative is just add a # before all the search lines. 

Grub uses the set root line to know what drive, partition to use, but if drive order 
has changed uses the search to correct it. If it cannot search the xfs the search fails.

  set root='([COLOR=Red]hd1[/COLOR],msdos1)'
  search --no-floppy --fs-uuid --set=root b91a2f25-fd72-46dd-8e8f-c6018bca78bb

If you are using BIOS to boot from sdb the above entry also should be hd0. Boot drive in BIOS is always hd0. Search then should correct it but again if it cannot search xfs it fails.

Another way to boot. This can bypass grub.
[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)
[http://www.supergrubdisk.org/wiki/Main_Page](http://www.supergrubdisk.org/wiki/Main_Page)

---

### Post by YannBuntu on 2012-10-12
hi
> **ngahiker said:**
> selecting "ATA disk support (solves the [out of disk] error)" - ouch that made it worse.

for information, this option can easily be reverted by using B-R again without this option. Now you don't use it any more, so don't worry about it.

The BootInfo seems ok to me. Sorry i can't help on this. Please follow Oldfred's advice.

---

### Post by ngahiker on 2012-10-12
XFS issue - interesting - I tried a quick test. Booted the PC with just the ext4 boot drive connected. PC booted normally. 

update-grub
grub-install /dev/sda
grub-install --recheck /dev/sda

Shut down PC then plugged in the two xfs drives.

PC rebooted normally. 

Ran boot-repair (just create a boot info summary option) [http://paste.ubuntu.com/1275971](http://paste.ubuntu.com/1275971)

Sounds like I was lucky it ever booted...

---

### Post by oldfred on 2012-10-12
So it now works? Very strange.

I still think the original issue somehow related to the xfs drives but then issue should have reappeared when you reinstalled those drives. Computers are always so consistent. :)

---

