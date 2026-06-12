---
title: "Partitions problem"
date: 2006-09-16
forum: Installation &amp; Upgrades
---

### Post by cybermatthieu on 2006-09-16
Hi,
I recently crashed my system. :'(

Here's way I did it, I installed OpenOffice and after installing it my system was hanging/reely slow. So I did a hard shutdown and rebooted. The system wasn't able to reboot. So I removed the hd from the system and pluged it in a usb caddy to do a fsck.ext3. This process always endeding up the same message:
Unable to recover journal.

So then I came to realise that the data wasn't goin to recuperable. So I tried to erase all the partition to reformat. When I was in fdisk, it was telling that the Partition 1 (Windows NTFS) does not end on cylinder boundary. Here's what fdisk showed me:
```
Disk /dev/sdb: 30.0 GB, 30005821440 bytes
255 heads, 63 sectors/track, 3648 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        2371    19043608+   7  HPFS/NTFS
Partition 1 does not end on cylinder boundary.
/dev/sdb2            2372        2402      249007+  83  Linux
/dev/sdb3            2403        2464      498015   82  Linux swap / Solaris
/dev/sdb4            2465        3648     9510480   83  Linux

```

Then I tryed to delete all the partition, after telling fdisk to write the modifications to the drive, I wasn't able to access the drive. So I unplugged the usb (after the drive had no activity) and plugged it back. Whent back in fdisk and all the partitions were still there. I then tried the same procedure with cfdisk and sfdisk and even gparted ending all with the same results.

I googled around to find post about the "Partition 1 does not end on cylinder boundary." message and I found a post telling how to remove the mbr from a drive with the dd command. So I tried it:
```
dd if=/dev/zero of=/dev/sdb bs=512 count=1
```

After the commend ran, the drive was still accesable. So thought that I could format the entire drive with dd. (I think that this was one big mistake now) so I then did this command :
```
dd if=/dev/zero of=/dev/sdb bs=512 count=16065
```

It told me that the copy was successful, but it was saying that it copied only ~8.5 gb (the drive is a 30gb).

So here I'm, I can't delete the partitions with fdisk,cfdisk,sfdisk,gparted or enven Windows. Is the drive recurable? (it's a laptop drive so it's more expensive than the regular drives) What can I do?](*,) 

Thanks,
Cyb

---

### Post by whizbaby on 2006-09-16
You could run testdisk on your drive (sudo apt-get install testdisk):
[B]sudo testdisk */debug /dev/hdb* 
[/B]
(if your drive is located at /dev/hdb)
Before you type this, make your terminal fullscreen (testdisk needs a couple of lines for it's display and won't start if terminal not big enough)

---

### Post by cybermatthieu on 2006-09-16
Thanks for the reply! :)

Here's the results after running testdisk /debug /dev/sdb -> analyse :
```
TestDisk 6.1, Data Recovery Utility, October 2005
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 28615 MB - CHS 3648 255 63
Check current partition structure
     Partition                  Start        End    Size in sectors
Invalid NTFS boot
 1 * HPFS - NTFS              0   1  1  2370 209 63   38087217
 1 * HPFS - NTFS              0   1  1  2370 209 63   38087217
No EXT2, JFS, Reiser, cramfs or XFS marker
 2 P Linux                 2371   0  1  2401 254 63     498015
 2 P Linux                 2371   0  1  2401 254 63     498015
 3 P Linux Swap            2402   0  1  2463 254 63     996030
No EXT2, JFS, Reiser, cramfs or XFS marker
 4 P Linux                 2464   0  1  3647 254 63   19020960
 4 P Linux                 2464   0  1  3647 254 63   19020960




*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
[Proceed ]  [  Save  ]

                            Try to locate partition
```
After proceeding:
```
TestDisk 6.1, Data Recovery Utility, October 2005
Christophe GRENIER <grenier@cgsecurity.org>
http://www.cgsecurity.org

Disk /dev/sdb - 28615 MB - CHS 3648 255 63
     Partition               Start        End    Size in sectors
L HFS                    132   2  1   132 254 63      15939 [&#65533;&#65533;&#65533;&#65533;^U+&#65533;&#65533;~RI)&#65533;&#65533;&#65533;]
* Linux Swap            2402   0  1  2463 254 63     996030












Structure: Ok.  Use arrow keys to change partition characteristics:
*=Primary bootable  P=Primary  L=Logical  E=Extended  D=Deleted
Keys A: add partition, L: load backup, T: change type,
     ENTER: to continue
HFS, 7 MB
```

I rebooted and testdisk shows the same info...

What's next?

Thanks again,
Cyb

---

### Post by whizbaby on 2006-09-16
Due to *matthieu* and *recuperable* you may be able to read this (unfortunately I don't know one in english, if you can't read it I'll try to translate)
[http://astuce.linux.free.fr/Les_systemes_de_fichier/R%E9paration%20du%20syst%E8me%20de%20fichier.html](http://astuce.linux.free.fr/Les_systemes_de_fichier/R%E9paration%20du%20syst%E8me%20de%20fichier.html)
Though it doesn't deal with *ntfs* it might be helpful.

---

### Post by cybermatthieu on 2006-09-17
I tried what was on the web page... still no success.

Thanks again,
Cyb

---

