---
title: "&quot;The 'grub-efi-amd64-signed' package failed to install target&quot; in ubuntu 18.04.1"
date: 2018-07-27
forum: Installation &amp; Upgrades
---

### Post by habernir on 2018-07-27
i thought that they will fix it in ubuntu 18.04.1 BUT they don't.

---

### Post by oldfred on 2018-07-27
To install in UEFI boot mode, you must have an ESP - efi system partition on whatever is the first drive seen by Ubuntu/grub. If you do not partition in advance, it will create one. Drive(s) should be gpt partitioned for UEFI install.

Post this:
sudo gparted -l

---

### Post by habernir on 2018-07-28
thanks for your answer .

my first partition its nvme but i think  you mean to "sda" ?  (and i know i need EFI partition i already create it in my nvme)
my sda (my old ssd) its in use BUT i want to install efi in my nvme drive .

soo i moved back to ubuntu 16.04 until ubuntu team will create ubuntu installtion CD with this fix.

and even if i create EFI in my sda  i dont think it will solve this problem (from the many forums that i checks i'm not the only one) . this bug it's in the installation and i hope they will solve it soon

---

### Post by jeremy31 on 2018-07-28
Try installing without internet connection and see if it succeeds.  There have been endless bug reports filed about this issue since July 10

---

### Post by oldfred on 2018-07-28
All the users with NVMe drives, have grub installed to it. Grub seems to always think that is first drive.
I only have SATA drives and grub in UEFI mode always installs to ESP on sda.
Post this:
sudo parted -l

---

### Post by habernir on 2018-07-29
i try [COLOR=#000000]without internet connection and with [/COLOR][COLOR=#000000]without internet connection and still the same thing
[/COLOR]
and this is the [COLOR=#000000]output of "[/COLOR][COLOR=#000000]sudo parted -l" :[/COLOR]

```

Model: ATA Samsung SSD 850 (scsi)
Disk /dev/sda: 256GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End    Size   File system  Name  Flags
 1      1049kB  256GB  256GB  ext4 



Model: NVMe Device (nvme)
Disk /dev/nvme0n1: 512GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system     Name  Flags
 1      1049kB  512MB   511MB   fat32                 boot, esp
 2      512MB   33.3GB  32.8GB  linux-swap(v1)
 3      33.3GB  512GB   479GB   ext4




Model: NVMe Device (nvme)
Disk /dev/nvme1n1: 1024GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 


Number  Start   End     Size    File system  Name  Flags
 1      1049kB  1024GB  1024GB  ext4

```


when i install ubuntu 16.04 with this partitions schematic everything ok
but in ubuntu 18.04.1 the same error i also create EFI in my other nvme drive still the same .

the only solution that work its when the installation stop when grub fail  i can run "boor-repair" and its fix the boot BUT some of the packages installation are not finished and it create a mess  .

i hope they will fix it soon

---

### Post by oldfred on 2018-07-29
Just about everyone else with NVMe drive type, seem to install correctly to the ESP on the NVMe drive.
But I always put both an ESP & bios_grub on every drive, even larger flash drives. And I normally have a full install on every drive, even if just in a somewhat smaller partition for future emergency use.

---

### Post by cmjprous on 2018-07-30
there is a bios fix for the acer e-1 that 8.1 comes on  this will fix the modes from uefi to legacy, everyone needs to check on the makers site for a bios update to fix the uefi mode to legacy . i had problems running a boottable windows 7 tried everything to install all Ubuntu on my newer system it just won't work no mater what i tried... just looked today now running windows 7 install on the legacy mode to test the installing of it s ofar so good now all my systems will be powered by Ubuntu. think this is the wrong place to but this but opps, this should  solve AMD ad Intel issues one you update bios from makers of system acer was in deep trouble loosing customers  so they fixed it to where you can get the updated bio fix to legacy.


your welcome anytime [CMJ Pro US]([http://cmjprous.com](http://cmjprous.com) )

---

