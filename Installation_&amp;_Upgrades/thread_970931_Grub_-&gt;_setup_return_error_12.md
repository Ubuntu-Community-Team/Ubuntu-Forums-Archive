---
title: "Grub -&gt; setup return error 12"
date: 2008-11-04
forum: Installation &amp; Upgrades
---

### Post by hasanatkazmi on 2008-11-04
Hello
I have upgraded my Ubuntu from 8.04 to 8.10 and then installed XP on other partition, then as usuall, I found grub eaten up by XP's bootloader.
then I did what is written here:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

but, it didnt solve my problem

every thing goes fine upto root (hd0,5) but when i do setup (hd0,5), followin g is printed and process fails:
#
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "embed /boot/grub/e2fs_stage1_5 (hd0,5)"... failed (this is not fatal)
 Running "install /boot/grub/stage1 (hd0,5) /boot/grub/stage2 p /boot/grub/menu.lst "... failed

Error 12: Invalid device requested

#
I have one harddisk and ubuntu is installed in 5th partition

---

### Post by unutbu on 2008-11-04
Please post the output of 
```

sudo fdisk -lu
```

---

### Post by caljohnsmith on 2008-11-04
If you want to replace Windows boot loader code in the MBR (Master Boot Record) with Grub so you can get Grub on start up, you should use:
```
sudo grub
grub> root (hd0,5)
grub> setup (hd0)
grub quit

```
If you use "setup (hd0,5)" like you did, it installs Grub to the boot sector of the sda6 partition, not the HDD's MBR. 

But the fact that Grub failed to install to the boot sector of sda6 is not a good sign; that often results from a corrupted partition table. How about booting your Live CD, open a terminal (applications > accessories > terminal), and post the output of:
```
sudo fdisk -l
```
And then to check your partition table, first make sure the Universe repository is enabled in System > Admin > Software Sources, and then download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen and we can work from there. :)

---

### Post by hasanatkazmi on 2008-11-04
well, thanks for such interest

running fdisk -l returned:

[HTML]
omitting empty partition (5)

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cd314f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1       38912   312560608+   5  Extended
/dev/sda2   *        6375       16573    81923436    7  HPFS/NTFS
/dev/sda5               1        6322    50781370+  83  Linux
/dev/sda6            6323        6374      417658+  82  Linux swap / Solaris
/dev/sda7   *       16574       26772    81923436   af  Unknown
/dev/sda8           26773       38912    97514518+   7  HPFS/NTFS


[/HTML]

and running TestDisk gave me this :

[HTML]

TestDisk 6.6, Data Recovery Utility, February 2007
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63

     Partition                  Start        End    Size in sectors

 1 E extended LBA          6322   0  1 38911 254 63  523558350
 5 L Linux Swap            6322   1  1  6373 254 63     835317
 6 L HPFS - NTFS           6374   1  1 16572 254 63  163846872
 7 L HFS                  16573   1  1 26771 254 63  163846872
 8 L HPFS - NTFS          26772   1  1 38911 254 63  195029037


[/HTML]

is this what you asked me for??

---

### Post by caljohnsmith on 2008-11-04
> **hasanatkazmi said:**
> 
```
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x5cd314f7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               [COLOR="Red"]1       38912[/COLOR]   312560608+   5  Extended
/dev/sda2   *        [COLOR="Red"]6375       16573[/COLOR]    81923436    7  HPFS/NTFS
/dev/sda5               1        6322    50781370+  83  Linux
/dev/sda6            6323        6374      417658+  82  Linux swap / Solaris
/dev/sda7   *       16574       26772    81923436   af  Unknown
/dev/sda8           26773       38912    97514518+   7  HPFS/NTFS
```

You definitely have a problem with your HDD's partition table, because fdisk first claims sda5 is an empty partition, and also sda2, which is a primary partition, is inside of the sda1 extended partition. Also, although this is not as important, you should only have one partition on the HDD marked as bootable, and at the moment both sda7 and sda2 are marked as bootable.

If you want help repairing your partition table, then start testdisk again, and go through these steps: choose "no log", select HDD and "proceed", "Intel", "Analyze", then "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen if you would like help fixing your partition table.

---

### Post by hasanatkazmi on 2008-11-04
well , after doing what you have said, I get this

```


Disk /dev/sda - 320 GB / 298 GiB - CHS 38913 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 E extended                 0   1  1 38911 254 63  625121217
 2 * HPFS - NTFS           6374   1  1 16572 254 63  163846872
Space conflict between the following two partitions
 1 E extended                 0   1  1 38911 254 63  625121217
 2 * HPFS - NTFS           6374   1  1 16572 254 63  163846872







```

What's this? this thing gone bad?

---

