---
title: "Win 7 Boot Problem on Dual Boot (Because Partition Was Not Deleted?)"
date: 2012-06-19
forum: Installation &amp; Upgrades
---

### Post by partitionperson on 2012-06-19
Hi,

Im trying to install BackTrack 5 R2 (32bit, KDE) alongside Win 7 (dual boot, from internal HD).
 
 I successfully installed BackTrack, but my problem is that I cant boot Win 7 anymore.
 
 It boots for a while (showing the win logo animation, then going to a bluescreen.) I get this error message on the blue screen when trying to boot Win7: &quot;The Boot Selection failed because a required device is inaccessible.&quot; (Status: 0xc0000225)
 
 I think I have realized what is wrong. When running the BackTrack installation I deleted a partition I had recently created in Win 7 (F: with ca 60GB) and created two new ones, a swap of 3 GB and my Linux partition (ca 79GB).
 
 It seems like the old F: partition was not deleted, and I suspect I can correct the problem by deleting it.
 
 But I don't want to mess things up so I thought I'd ask here for advice first.
 
 When running fdisk -l
 I get this output:
 
 Disk /dev/sda: 320.1 GB, 320072933376 bytes 255 heads, 63 sectors/track, 38913 cylinders Units = cylinders of 16065 * 512 = 8225280 bytes Sector size (logical/physical): 512 bytes / 4096 bytes I/O size (minimum/optimal): 4096 bytes / 4096 bytes Disk identifier: ...   

    Device Boot      Start         End      Blocks   Id  System
 /dev/sda1               1           1         992+  42  SFS
 Partition 1 does not end on cylinder boundary.
 Partition 1 does not start on physical sector boundary.
 /dev/sda2   *           1          26      203776   42  SFS
 Partition 2 does not end on cylinder boundary.
 /dev/sda3              26       28824   231320576   42  SFS
 /dev/sda4           **28824       38914**    81043457    5  Extended
 Partition 4 does not start on physical sector boundary.
 /dev/sda5          **28824**       29189     2928640   82  Linux swap / Solaris
 /dev/sda6           29189       **38914**    78113792   83  Linux
 
 Looking at this it seems like my F: is still there, the /dev/sda4 of ca 80GB.
 
 **sda5 and 6 are using the same cylinders as sda4 it seems like.**
 
 And it seems like the boundaries of sda1 and sda2 are also a potential problem.
 
 When I bought the (HP) lap top it had my C: and two or three other partitions (I saw at least two in windows, but can't remember exactly, and then when managing the partitions in Linux I saw 3 in addition to my C:.(One partition is the backup, and one seems to be only 1 MB large).
 
 Another slightly weird thing is that the F: I created was 60GB but in Linux it seems to be 80GB.
 
 Ok, so my question is: How do I get my Win 7 to work again?
 
 Should I just delete /dev/sda4 ? (Do I need to rename sda5 and 6?)
 (a strange thing is, I should have to use my old F: to boot Win 7)
 
 Do I have to do anything about the boundaries of sda1 and sda2? I guess they were made like this by HP.
 
 I followed the installation instructions as far as I could, except I had to make the partitions. I also mounted C: as /windows (and I can access it from Ubuntu).
 My Linux partition is ext3, if I remember correctly.
 
 When searching for the error code I see suggestions of enabling the APIC, but after checking my partitions, that doesn't seem to be the problem.
 
 Thanks in advance for any advice!
 
 Hopefully asking here can help me save days tearing my hair trying to fix problems :)

---

### Post by darkod on 2012-06-19
/dev/sda4 is the extended partition which is a container for the logical partitions which are sda5 and sda6. So, the fact that sda5 and sda6 are inside sda4 is fine.

However, sda1-sda3 are type SFS which means Dynamic disk in windows. That is MS format and I'm not sure how good it plays with Backtrack. Ubuntu for example can't install on dynamic disk.

Your computer either came with dynamic disk, or your tried to create a fifth partition on it and MS did the wonderful job of converting it to dynamic disk.

Also, the boundaries of sda1 and sda2 doesn't seem to be an issue because sda1 is very small. In that case they can be on the same cylinder.

I'm not sure if you can run BT in live mode like ubuntu, and if it has parted included. If it does, you can easily check if you really have overlapping partitions by booting BT in live mode (or the BT installation if it works), open terminal and try to execute:
```
sudo parted /dev/sda unit s print
```

That should print the partitions on /dev/sda using sectors, not cylinders. At least that's what it does on ubuntu. In the list and the start/end sectors you can notice if there really are partitions overlapping.

---

### Post by partitionperson on 2012-06-19
Thanks Darko!
 
 My BackTrack installation works fine (using it now) and as I understand BackTrack is Ubuntu plus some additional programs installed.
 
 I did as you said and it seems like there is no overlap:
 
 Model: ATA WDC WD3200BPVT-6 (scsi)
 Disk /dev/sda: 625142448s
 Sector size (logical/physical): 512B/4096B
 Partition Table: msdos
 
 Number  Start       End         Size        Type      File system     Flags
  1      63s         2047s       1985s       primary
  2      2048s       409599s     407552s     primary   ntfs            boot
  3      409600s     463050751s  462641152s  primary   ntfs
  4      463052798s  625139711s  162086914s  extended
  5      463052800s  468910079s  5857280s    logical   linux-swap(v1)
  6      468912128s  625139711s  156227584s  logical   ext3
 
 Not sure what could be the problem...??
 
 Perhaps the fact that I mounted C: to /Windows?
 
 I did create a 5th partition in Win 7, my F:. Can't remember if I did it as Dynamic or not.
   Thanks for your answer, I learned something new (about container partitions).

---

### Post by darkod on 2012-06-19
I think the disk being dynamic is the problem. Not sure if you will need to delete the backtrack partitions, and then with only three partitions existing convert the disk back to Basic.

Google around for converting dynamic to basic disks, there are tools to do it without losing the data on it. But I don't have any links for that.

---

### Post by partitionperson on 2012-06-19
Ok, I'm trying TestDisk to convert my disk from dynamic to Basic.  Indeed, my windows partitions were Dynamic.  [http://www.cgsecurity.org/wiki/TestDisk](http://www.cgsecurity.org/wiki/TestDisk) [http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/](http://mypkb.wordpress.com/2007/03/28/how-to-non-destructively-convert-dynamic-disks-to-basic-disks/)  Let's see if it works. If you never hear from me again, it didn't....

---

