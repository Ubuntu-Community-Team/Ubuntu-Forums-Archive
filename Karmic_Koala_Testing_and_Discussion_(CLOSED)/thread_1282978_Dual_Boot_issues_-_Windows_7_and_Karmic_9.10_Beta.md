---
title: "Dual Boot issues - Windows 7 and Karmic 9.10 Beta"
date: 2009-10-05
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by jojo786 on 2009-10-05
Hi guys,

I have (had) a working Windows 7 installation, only a single 120GB laptop. I installed the 9.10 beta, making it a dual boot system. 9.10 can now boot successfully from grub, but Windows now wont work. I get a Windows Boot Manager screen, and the error is that a device/resource is inaccessible.

Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x6823d7ed

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13        5100    40857600    7  HPFS/NTFS
/dev/sda3            5100       10199    40960000    6  FAT16
/dev/sda4           10200       14593    35294805    5  Extended
/dev/sda5           10200       10442     1951866   82  Linux swap / Solaris
/dev/sda6           10443       11415     7815591   83  Linux
/dev/sda7           11416       14593    25527253+  83  Linux

I think that issue is perhaps to do with that 100MB 'boot' partition that Windows 7 installed (sda1). Is it perhaps related to the new version of grub?

Can anybody give pointers as to how I can restore Windows to a working condition?

---

### Post by Mark Phelps on 2009-10-05
It's likely that if you let Ubuntu configure it by default, it doesn't know how to handle the 100MB Windows 7 BOOT partition and set up the menu stanza incorrectly.

Can't help without you posting the contents of your menu.lst file.

---

### Post by jojo786 on 2009-10-07
Theres no menu.1st file, only a grub.cfg (this is grub2, the grub-pc package.)

It seems Ubuntu might not have been the direct culprit, although I am not sure, as I still have'nt got Windows to boot yet. I used the Windows 7 Install DVD to boot into repair mode, and used the bcdedit commands to try to fix the Windows Boot Manager.
No luck though.

---

### Post by Mark Phelps on 2009-10-07
Sorry, didn't notice the GRUB2 part.  Was going to look at the menu.lst file to see what Ubuntu entered for your Windows 7 stanza -- hoping that it would be a simple fix to change that to point to the correct partition.  But, can't help you with GRUB2.

Instead of using BCDEdit, why not just run Startup Repair from the Windows 7 disk?  Did you try that and it didn't work, too?

---

### Post by jojo786 on 2009-10-08
I tried that, no luck.

---

### Post by madsc89 on 2009-10-08
I am running Karmic and W7 dualboot on a 80 GB SSD. No problems. havent done anything other than installing ubuntu to make it work...

---

### Post by MacUntu on 2009-10-08
What's the output of ```
sudo os-prober
```?

Do you have any boot related files on /dev/sda2 (like a folder 'Boot' and a file 'bootmgr')?

---

### Post by jojo786 on 2009-10-08
> **madsc89 said:**
> I am running Karmic and W7 dualboot on a 80 GB SSD. No problems. havent done anything other than installing ubuntu to make it work...

The problem comes in with the 100MB Boot partition that Windows creates at install time. In my case, it created it. Other guys ii the office also installed Win 7 and no extra Boot partition was created.

Now the Windows Manager lives in this 100MB partition, or else lives with Windows normally. Now when I installed Karmic and created various new partitions, the Windows Boot manager must have must have had the listing of its drive changed, which broke booting Windows. No amount of me cajooling it with bcdedit could change that.

---

### Post by jojo786 on 2009-10-08
This seems to be what happened:

[http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/](http://www.mydigitallife.info/2009/01/09/how-to-avoid-200mb-hidden-system-partition-from-been-created-during-windows-7-installation/)

I had a clean disk when I started the Win 7 install.

---

### Post by seamuso on 2009-10-08
Here's what os-prober setup for my win7 in grub.cfg

```

### BEGIN /etc/grub.d/30_os-prober ###
menuentry "Windows 7 (loader) (on /dev/sda1)" {
	insmod ntfs
	set root=(hd0,1)
	search --no-floppy --fs-uuid --set 2ae000d2e000a663
	chainloader +1
}
### END /etc/grub.d/30_os-prober ###
```

Please note, My win7 is on a seperate drive, but I do have the 100MB utility partition and have had grub2 rewrite my MBR on that drive a couple of times. When I have the win7 drive set as the boot drive, the grub2 installed to the drives MBR will correctly boot win7 with the grub.cfg entry listed above.

And a little fdisk -l for the win7 drive ..

```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9f9d1ac7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1          13      102400    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2              13       60802   488282112    7  HPFS/NTFS
```

Compare my os-prober section with yours and if they are different (excluding uuid), try copying my os-prober section into your grub.cfg (make sure you change the uuid to match what yours needs to be) and see if that gets your win7 to start correctly.

On further consideration, I'm also going to add the grub.cfg entry I use to boot my netbook ..
```

### BEGIN /etc/grub.d/21_winxp ###
menuentry "Windows XP" {
       insmod ntfs
       set root=(hd0,1)
       search --no-floppy --fs-uuid --set a2f48f73f48f490d
       drivemap -s (hd0) ${root}
       chainloader +1
}

### END /etc/grub.d/21_winxp ###
```

because it uses a drivemap command that you should probably also have in your grub.cfg ..

and the fdisk -l
```
Disk /dev/sda: 160.0 GB, 160041885696 bytes
214 heads, 54 sectors/track, 27049 cylinders
Units = cylinders of 11556 * 512 = 5916672 bytes
Disk identifier: 0x9358c633

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       17988   103934637    7  HPFS/NTFS
/dev/sda2           26156       27042     5125086   1c  Hidden W95 FAT32 (LBA)
/dev/sda3           27043       27049       40446   ef  EFI (FAT-12/16/32)
/dev/sda4           17989       26155    47188926    5  Extended
/dev/sda5           17989       25813    45212823   83  Linux
/dev/sda6           25814       26155     1976049   82  Linux swap / Solaris
```

Go you have - 
```

drivemap -s (hd0) ${root}

```
or similiar in your win7 grub.cfg entry?

---

