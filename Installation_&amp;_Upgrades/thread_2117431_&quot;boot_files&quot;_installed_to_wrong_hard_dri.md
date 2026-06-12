---
title: "&quot;boot files&quot; installed to wrong hard drive"
date: 2013-02-18
forum: Installation &amp; Upgrades
---

### Post by apkatt on 2013-02-18
Hi,

I have just installed Ubuntu Server 12.04LTS on new hardware. The operating system (/) and swap was placed on a 60GB SSD while two WD RE4 2TB drives were configured in RAID1 for /home.

When I restarted after installation, the system refused to boot and I got a blinking line. I restarted again and choose the first SATA disk which is one of the WD hard drives, the system booted as it should.

So, for some reason, the installation placed some boot files (GRUB?) on the SATA1 drive rather than the SSD where / is located.

SATA1 connector: HDD1 (software RAID1 with /home)
SATA2 connector: HDD2 (software RAID1 with /home)
SATA3 connector: SSD (with swap and /)

Why does this happen and what do I need to do in order for the system to boot from the SSD right away. Now, I manually have to go into bios and select the HDD. Off course, I don't want the boot to be dependent on one of the hard drives in the RAID setup.

---

### Post by oldfred on 2013-02-18
Not sure about server installer, but desktop always defaults to sda. But during install at partitioning stage you should get the option on which drive to install grub2's boot loader.

If you can boot you can just install grub to any drive.

       sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb

    
if sdc use that instead. And then in BIOS boot from that drive.
Did you use gpt partitioning on SSD? To install correctly with gpt it also need a bios_grub partition if booting in BIOS mode.

---

### Post by apkatt on 2013-02-18
> **oldfred said:**
> Not sure about server installer, but desktop always defaults to sda. But during install at partitioning stage you should get the option on which drive to install grub2's boot loader.

If you can boot you can just install grub to any drive.

       sudo fdisk -l
#if it's "/dev/sdb"  then just run:
sudo grub-install /dev/sdb

    
if sdc use that instead. And then in BIOS boot from that drive.
Did you use gpt partitioning on SSD? To install correctly with gpt it also need a bios_grub partition if booting in BIOS mode.

Well, I used the built in partitioning function in the installer, the one that is blue and yellow :)

I can boot just fine from sda which happens to be disk 1 in my RAID1 array. The computer tries to boot from sdc since that's where / is (I guess) but nothing happens since GRUB apparently installed to sda.

So if I do the sudo grub-install /dev/sd**c** GRUB should install on my SSD (given that this is sdc) as an identical copy of whatever GRUB is on sda currently?

```
Disk /dev/sda: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0003b28c

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048  3907028991  1953513472   fd  Linux raid autodetect

Disk /dev/sdb: 2000.4 GB, 2000398934016 bytes
255 heads, 63 sectors/track, 243201 cylinders, total 3907029168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0006e3d1

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1            2048  3907028991  1953513472   fd  Linux raid autodetect

Disk /dev/sdc: 60.0 GB, 60022480896 bytes
255 heads, 63 sectors/track, 7297 cylinders, total 117231408 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0009a110

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *        2048    85938175    42968064   83  Linux
/dev/sdc2        85938176   117229567    15645696   82  Linux swap / Solaris

Disk /dev/md0: 2000.3 GB, 2000263380992 bytes
2 heads, 4 sectors/track, 488345552 cylinders, total 3906764416 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x00000000

Disk /dev/md0 doesn't contain a valid partition table
```

---

### Post by darkod on 2013-02-18
Yes, it will be identical. You can have grub2 on as many as you want MBRs.

Run the command, set the 60GB first in boot order, and you're good to go.

---

### Post by apkatt on 2013-02-18
> **darkod said:**
> Yes, it will be identical. You can have grub2 on as many as you want MBRs.

Run the command, set the 60GB first in boot order, and you're good to go.

Ok! By boot order, you are referring to boot priority in UEFI/BIOS?

EDIT: Also, why is there an asterisk under the "BOOT" column on both sda and sdc?

---

### Post by oldfred on 2013-02-18
The * is the boot flag. But grub does not use boot flag. Windows (lilo, syslinux, maybe others) have to have boot flag to know which PBR - partition boot sector has more boot code. Grub does not normally use PBR.

But a few BIOS (Intel for sure) have to see a boot flag on a primary partition or they will not let you boot. So still best to have a boot flag. Only one per drive, on a primary partition or the NTFS Windows boot partition if dual booting with Windows.

---

### Post by apkatt on 2013-02-18
> **oldfred said:**
> The * is the boot flag. But grub does not use boot flag. Windows (lilo, syslinux, maybe others) have to have boot flag to know which PBR - partition boot sector has more boot code. Grub does not normally use PBR.

But a few BIOS (Intel for sure) have to see a boot flag on a primary partition or they will not let you boot. So still best to have a boot flag. Only one per drive, on a primary partition or the NTFS Windows boot partition if dual booting with Windows.

Ok, thanks. I hope this works now, cannot restart now since people are using the server.

EDIT: It worked! Thanks!

---

