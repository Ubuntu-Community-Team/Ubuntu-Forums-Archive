---
title: "Partition Editor cannot see partitions on 1 of my 2 hdds"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by banjo man on 2008-11-03
I originally had an Ubuntu 8.10 beta/Vista dual boot with grub

I decided to drop vista for xp, no problems

now, I'm trying to reinstall grub (with no success)

```
grub> find /boot/grub/stage1
find /boot/grub/stage1
 (hd0,5)
grub> root (hd0,5)
root (hd0,5)
grub> setup (hd0)
setup (hd0)
 Checking if "/boot/grub/stage1" exists... yes
 Checking if "/boot/grub/stage2" exists... yes
 Checking if "/boot/grub/e2fs_stage1_5" exists... yes
 Running "embed /boot/grub/e2fs_stage1_5 (hd0)"...  16 sectors are embedded.
succeeded
 Running "install /boot/grub/stage1 (hd0) (hd0)1+16 p (hd0,5)/boot/grub/stage2 /boot/grub/menu.lst"... failed

Error 22: No such partition
grub>
```

so, I decided to install the new version (8.10)

boot into the live cd, run install script, and when the partition editor loads, it shows nothing on my first hdd (internal laptop, this hdd has a few partitions: windows, two for data, etc...) when I reboot, windows loads fine and everything is still where it should be...
(second internal hdd partitions show up fine)

I have tried the 64 bit version, 32 bit, as well as the 8.10 beta that I had installed before the windows xp install..



**_[COLOR="Red"]EDIT[/COLOR]_**: Solved it shortly after last post. Thanks Very Much, and sorry for taking so long to get back. College kicked in, and I got Very busy (almost too busy for video games ;)

---

### Post by caljohnsmith on 2008-11-03
Based on your HDD's symptoms, most likely you have a corrupted partition table. From your Live CD, how about posting:
```
sudo fdisk -l
```
Then make sure the Universe repository is enabled in System > Admin > Software Sources, and download and run testdisk with the following commands:
```
sudo apt-get install testdisk
sudo testdisk
```
After starting testdisk with the above command, choose "no log", select HDD and "proceed", "Intel", "Analyze", and see what it shows for your HDD and what errors it might give. Please post the output of that screen. Then do "proceed", Y/N depending on if you have any Vista partitions, hit enter, and select "search!" so it does a deeper search, which could take a while. Post the output of that screen too, and with all the above data, we should be able to tell if you have a problem with your partition table. :)

---

### Post by banjo man on 2008-11-03
```
ubuntu@ubuntu:~$ sudo fdisk -l
omitting empty partition (5)

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          12        1317    10485760    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1318       19582   146713612+   7  HPFS/NTFS
/dev/sda3           19583       30074    84276990    f  W95 Ext'd (LBA)
/dev/sda4           23476       30074    53006436    7  HPFS/NTFS
/dev/sda5           19583       23475    31270459+  83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0942df08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117218304    7  HPFS/NTFS
ubuntu@ubuntu:~$ 

```

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS             11  23 13  1316 129 29   20971520 [RECOVERY]
 2 P HPFS - NTFS           1317   0  1 19581 254 63  293427225
 3 E extended LBA         19582   0  1 30073 254 63  168553980
 4 P HPFS - NTFS          23475   1  1 30073 254 63  106012872 [Uber1]
Space conflict between the following two partitions
 3 E extended LBA         19582   0  1 30073 254 63  168553980
 4 P HPFS - NTFS          23475   1  1 30073 254 63  106012872 [Uber1]
   X extended             19582   0  2 23474 254 63   62541044
 5 L Linux                19582   2  1 23474 254 63   62540919





*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Quick Search]  [ Backup ]
                            Try to locate partition

```

doing the deeper search now...

---

### Post by caljohnsmith on 2008-11-03
> **banjo man said:**
> ```
ubuntu@ubuntu:~$ sudo fdisk -l
[COLOR="Red"]omitting empty partition (5)[/COLOR]

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          12        1317    10485760    7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sda2            1318       19582   146713612+   7  HPFS/NTFS
/dev/sda3           19583       30074    84276990    f  W95 Ext'd (LBA)
/dev/sda4           23476       30074    53006436    7  HPFS/NTFS
/dev/sda5           19583       23475    31270459+  83  Linux


```

```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30401 255 63
Current partition structure:
     Partition                  Start        End    Size in sectors

 1 * HPFS - NTFS             11  23 13  1316 129 29   20971520 [RECOVERY]
 2 P HPFS - NTFS           1317   0  1 19581 254 63  293427225
 3 E extended LBA         19582   0  1 30073 254 63  168553980
 4 P HPFS - NTFS          23475   1  1 30073 254 63  106012872 [Uber1]
[COLOR="Red"]Space conflict between the following two partitions[/COLOR]
 3 E extended LBA         19582   0  1 30073 254 63  168553980
 4 P HPFS - NTFS          23475   1  1 30073 254 63  106012872 [Uber1]
   X extended             19582   0  2 23474 254 63   62541044
 5 L Linux                19582   2  1 23474 254 63   62540919


```

Unfortunately it looks like my suspicions were correct; you definitely have some problems with your partition table. Once you are done with the deep search we can try to piece it back to together, as it looks like it shouldn't be a problem.

---

### Post by banjo man on 2008-11-03
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
P FAT32 LBA               11   0  1  4188 254 63   67119570 [NO NAME]
P Linux                19582   1  1 23228 254 63   58588992
L Linux Swap           23229   1  1 23474 254 40    3951904
L HPFS - NTFS          23475   1  1 30073 254 63  106012872 [Uber1]
L FAT32 LBA            30074 239 54 30401  42 41    5240832 [MEDIADIRECT]







Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue

```

---

### Post by caljohnsmith on 2008-11-03
OK, on that last screen you posted, press "enter" to proceed, then select the "search!" so testdisk does its deep search, which will take a while. Please post the output of that screen.

---

### Post by banjo man on 2008-11-03
```
TestDisk 6.9, Data Recovery Utility, February 2008
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
* FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
D FAT32 LBA               11   0  1  4188 254 63   67119570 [NO NAME]
D HPFS - NTFS             11  23 13  1316 129 29   20971520 [RECOVERY]
D HPFS - NTFS           1316 129 30 19581 194  5  293431296
D HPFS - NTFS           1317   0  1 19581 254 63  293427225
D Linux                19582   1  1 23228 254 63   58588992
D Linux                19582   2  1 23474 254 56   62540912
D Linux Swap           23229   1  1 23474 254 40    3951904
P HPFS - NTFS          23475   1  1 30073 254 63  106012872 [Uber1]
P FAT32 LBA            30074 239 54 30401  42 41    5240832 [MEDIADIRECT]



Structure: Ok.  Use Up/Down Arrow keys to select partition.
Use Left/Right Arrow keys to CHANGE partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type, P: list files,
     Enter: to continue
FAT16, 90 MB / 86 MiB

```

sorry for the long wait...and thanks for the help

---

### Post by caljohnsmith on 2008-11-03
OK, I think I have your partition table figured out, but there is one ambiguity that I need to ask you about: did you have a swap partition, or did you delete it? If you had a swap partition, then I believe your partitions should be marked as I have below:
```

Disk /dev/sda - 250 GB / 232 GiB - CHS 30402 255 63
     Partition               Start        End    Size in sectors
[COLOR="Red"]D[/COLOR] FAT16 >32M               0   1  1    10 254 63     176652 [DellUtility]
[COLOR="Red"]D[/COLOR] FAT32 LBA               11   0  1  4188 254 63   67119570 [NO NAME]
[COLOR="Red"]P[/COLOR] HPFS - NTFS             11  23 13  1316 129 29   20971520 [RECOVERY]
[COLOR="Red"]D[/COLOR] HPFS - NTFS           1316 129 30 19581 194  5  293431296
[COLOR="Red"]*[/COLOR] HPFS - NTFS           1317   0  1 19581 254 63  293427225
[COLOR="Red"]L Linux                19582   1  1 23228 254 63   58588992
[COLOR="Red"]D[/COLOR] Linux                19582   2  1 23474 254 56   62540912[/COLOR]
[COLOR="Red"]L[/COLOR] Linux Swap           23229   1  1 23474 254 40    3951904
[COLOR="Red"]P[/COLOR] HPFS - NTFS          23475   1  1 30073 254 63  106012872 [Uber1]
[COLOR="Red"]D[/COLOR] FAT32 LBA            30074 239 54 30401  42 41    5240832 [MEDIADIRECT]

```
The way you can probably find out for sure is to select that first Linux entry above that's in red, and press "p" to list its root directory. If that works, then I think the above partition table changes are most likely correct. If testdisk gives you an error though when you try and list the directory, then instead select the second linux partition in red above, and try "p" again to list its directory. If that works instead, you should mark that partition as "L" and the previous linux partition as "D", and also mark the swap partition as "D". 

Once you have all the above partitions marked correctly, then press enter, and on the next screen I think it should give you an option to "write" the new partition table. Once you do that, reboot, and you might have to do the same Grub steps you did in your original post to reinstall Grub. If you have any problems, be sure to post the new output of (after rebooting):
```
sudo fdisk -l
```
And we can work from there. :)

---

### Post by banjo man on 2008-11-04
ok, so I did what you suggested, and now I have ubuntu installed...

but, now it shows my windows partition as unformatted/not there...

at grub it still shows windows xp, but when I try to load, windows gives an error (can't find something)..so, grub is fine, now the windows partition is mussed...

```
banjo@volo:~$ sudo fdisk -l
[sudo] password for banjo: 

Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326    6  FAT16
/dev/sda2              12       23475   188474580    f  W95 Ext'd (LBA)
/dev/sda3           23476       30074    53006436    7  HPFS/NTFS
/dev/sda4   *       30075       30402     2620416    c  W95 FAT32 (LBA)
/dev/sda5           19583       23475    31270456   83  Linux

Disk /dev/sdb: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x0942df08

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1       14594   117218304    7  HPFS/NTFS
banjo@volo:~$ 

```

---

### Post by caljohnsmith on 2008-11-04
> **banjo man said:**
> 
```
Disk /dev/sda: 250.0 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x40000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326    6  FAT16
/dev/sda2              12       23475   188474580    f  W95 Ext'd (LBA)
/dev/sda3           23476       30074    53006436    7  HPFS/NTFS
/dev/sda4   *       30075       30402     2620416    c  W95 FAT32 (LBA)
/dev/sda5           19583       23475    31270456   83  Linux

```

Are you sure you marked the partitions as I recommended in my last post? You have to use the up/down arrow keys to first select a partition, and then use the right/left arrow keys to change whether it is marked "D", "P", "*", or "L" like I showed in my last post. Unfortunately your partition table above doesn't look anything like what I suggested in my last post, except for the linux partition which is right. If you haven't written any data to the disk in the partitions other than the linux partition, you might be able to use testdisk again to do the deep search and find the partitions you showed in post #7. If you can get that far, I would try marking them as given in my last post, because I think that is your correct partition table. Let me know how it goes or if you run into problems again.

---

### Post by banjo man on 2008-11-04
ok...I think I may have only changed the two linux partitions :(

I'll try test disk again.. (this time paying attention)

thanks...

---

