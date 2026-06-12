---
title: "MBR Problems on Linux Install"
date: 2006-10-13
forum: Installation &amp; Upgrades
---

### Post by Afelah on 2006-10-13
I just finished installing Linux on my desktop box, in (what was supposed to be) a dual-boot configuration with my pre-existing WinXP install.  After the installation completed, I rebooted and entered the GRUB menu to see that my Windows partition is listed simply as "Other".  When it's selected, the two GRUB OS loading commands appear as text on a black background, but nothing else happens afterward.

Now, the details.  The Linux partition and the Windows partition reside on the same physical drive.  When I installed GRUB I had it install to the MBR, which I'm given to understand from subsequent research might not have been the best choice.  But I do know that the GRUB installation wasn't what caused the problem:  just prior to the Linux installation, I had dismantled a RAID 0 array that--for some reason unbeknownst to me--formerly held the MBR.  Windows wouldn't boot after I dismantled the array and reformatted the drives individually, but I had figured that when GRUB was installed it would be able to handle booting to Windows despite the MBR erasure.  Apparently not.

So I suppose my question is:  what should I do in order to make my Windows partition boot up properly under GRUB (or another OS loader)?  Also, I'm planning on installing the latest Debian Testing release on a third partition of the same physical drive in the near future:  when I do, is there anything I should be particularly careful of to make sure that I can boot all three OSes properly?

Thanks!

---

### Post by Kateikyoushi on 2006-10-13
You have to edit your menu.lst. It is located in /boot/grub/menu.lst.

You need to know your partition layout. This will list it.

```
sudo fdisk -l
```

Then backup your grub menu.lst

```
sudo cp /boot/grub/menu.lst /boot/grub/menu.lst_old
```

Now to the editing. 

```
gksudo gedit /boot/grub/menu.lst
```

You have to add this to the end but modify the root (hd0,0) according to your own configuration. 

The first number after the (hd is the number of the hard drive, the second is the partition.

```
title		Microsoft Windows
root		(hd0,0)
savedefault
makeactive
chainloader	+1
```


Save it and you are set.
When you install debian you can install it's bootloader and hope it will recognise all your OSes or you can skip it and add deb to your ubuntu's grub menu.

---

### Post by Afelah on 2006-10-14
Okay, I tried the edit that you mentioned:  that entailed changing the title of the OS in the boot menu, changing "rootnoverify" to "root", and adding "savedefault".  I'm still getting the same thing:

```

   Booting 'Windows XP Professional'

root (hd1,0)
 Filesystem type unknown, partition type 0x7
savedefault
chainloader +1

```

I notice the "Filesystem type unknown" error.  Does that mean that I need to specify the type of filesystem in the GRUB menu.lst file?

---

### Post by Kateikyoushi on 2006-10-14
I think the root(1,0) is not correct.

Please give us the output of the following command.

```
sudo fdisk -l
```

---

### Post by Afelah on 2006-10-14
Okay, here's the output:

```

Disk /dev/hdc: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1       30401   244196001   83  Linux

Disk /dev/hde: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hde1   *           1        3824    30716248+   7  HPFS/NTFS
/dev/hde2            3825        6692    23037210   83  Linux
/dev/hde3            6693        9560    23037210   83  Linux
/dev/hde4            9561        9729     1357492+  82  Linux swap / Solaris

Disk /dev/hdg: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdg1   *           1       14593   117218241   83  Linux

Disk /dev/hdh: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdh1   *           1       14593   117218241   83  Linux

Disk /dev/sda: 20.0 GB, 20000267776 bytes
255 heads, 63 sectors/track, 2431 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1           5       40131    0  Empty
/dev/sda2               6        2431    19486845    b  W95 FAT32

```

/dev/hde1, as you can probably gather, is holding the Windows partition.  The Linux install is on /dev/hde2.  The rest of the drives are ext3-formatted storage, with the exception of /dev/sda2--which is my iPod.

Thing is, I can't figure out how to translate the alphabetical hde2 to the numerical root(n,n).

Thanks; I appreciate the help.

---

