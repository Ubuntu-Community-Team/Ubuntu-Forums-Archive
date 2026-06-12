---
title: "Unisnstall a Linux installation or change boot order"
date: 2012-06-03
forum: Installation &amp; Upgrades
---

### Post by desposti on 2012-06-03
Hello,
I have 2 huge disks and the following OS installed: Windows7, ubuntu 11.04 and recently installed12:04.
I deleted the partition where 12:04 was installed and I could not boot , gave me a grub error.
I had to reinstall and I am back to the problem : how can I safely uninstall Ubuntu 12:04 on sdb4 please?
Since I have a huge disk I max just consider changing the boot order because Ubuntu 12:04 is now first in order and I do not really use it,  it was installed just for testing.
This is my fdisk -l  output

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2189b0f5

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          26      203776    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              26       88558   711135232    7  HPFS/NTFS
/dev/sda3           88558       91189    21128192    7  HPFS/NTFS
/dev/sda4           91189       91202      105336    c  W95 FAT32 (LBA)

Disk /dev/sdb: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x160ec3b7

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        3188    25600000   83  Linux
/dev/sdb2            3188        5610    19456000   82  Linux swap / Solaris
/dev/sdb3            5610       87949   661391360   83  Linux
/dev/sdb4           87949       91202    26125312   83  Linux
diego@diego-HP-ENVY-17:~$

Thank you very much

---

### Post by drs305 on 2012-06-03
Boot into your 11.04 Ubuntu and run the following. Use the drive your BIOS looks at first (sda or sdb). Don't use the partition number.
```
sudo grub-install /dev/sdX
```
This will return control to 11.04 and put it first in the boot order.

Once you confirm it's booting 11.04 as the default you can do what you want with the other Ubuntu's partition.

---

### Post by darkod on 2012-06-03
First of all, you didn't had to reinstall. You could have booted into live mode with a 11.04 CD and install grub2 to the MBR which would be connected to your 11.04.

So, what is that you want to do? Keep 11.04 and windows?

In that case, simply boot the 11.04 and in terminal do:
sudo grub-install /dev/sdb

That will install your 11.04 grub2 on the MBR of /dev/sdb. Set in bios to boot from sdb and that's it.

After that you can delete the 12.04 partitions you don't need. Note that 11.04 will run out of support soon, so you better start thinking about using a LTS version like 12.04.

If the 12.04 still exists in the grub2 menu of 11.04 after deleting the partition, to update grub2 run:
sudo update-grub

---

### Post by desposti on 2012-06-03
> **darkod said:**
> First of all, you didn't had to reinstall. You could have booted into live mode with a 11.04 CD and install grub2 to the MBR which would be connected to your 11.04.

So, what is that you want to do? Keep 11.04 and windows?

In that case, simply boot the 11.04 and in terminal do:
sudo grub-install /dev/sdb

That will install your 11.04 grub2 on the MBR of /dev/sdb. Set in bios to boot from sdb and that's it.

After that you can delete the 12.04 partitions you don't need. Note that 11.04 will run out of support soon, so you better start thinking about using a LTS version like 12.04.

If the 12.04 still exists in the grub2 menu of 11.04 after deleting the partition, to update grub2 run:
sudo update-grub


Thanks . I did it but still doesn't look that 11.04 is the default or on top of the list. Nothing seem changed. I am a bit scared of deleting 12.04 in case I have the boot error again

---

### Post by drs305 on 2012-06-03
> **desposti said:**
> Thanks . I did it but still doesn't look that 11.04 is the default or on top of the list. Nothing seem changed. I am a bit scared of deleting 12.04 in case I have the boot error again

Is your BIOS booting sdb first? If it is booting sda first, you would want to run the grub-install command using sda. Or you can change the BIOS to boot sdb first.

*However*, if you set up grub so the Windows bootloader was still on sda (but not used because the system is booting off sdb), don't do the grub-install /dev/sda yet.

You might want to try the Boot Repair app. There is a link in my signature line. Install and run it from your 11.04 system.

---

### Post by desposti on 2012-06-03
> **drs305 said:**
> Is your BIOS booting sdb first? If it is booting sda first, you would want to run the grub-install command using sda. Or you can change the BIOS to boot sdb first.

*However*, if you set up grub so the Windows bootloader was still on sda (but not used because the system is booting off sdb), don't do the grub-install /dev/sda yet.

You might want to try the Boot Repair app. There is a link in my signature line. Install and run it from your 11.04 system.

Thank you. I tried the boot repair but gave an error. I restarted and I think nothing has changed. I am going to bed now  but thanve ks for the quick reply. I think I will have to install 12.04 as main anyway sooner or later so I will live with this boot order and then when I install 12.04 on the big partition I will be able to delete the other one I guess.

Thanks

---

