---
title: "Partition issues"
date: 2008-05-06
forum: Installation &amp; Upgrades
---

### Post by Moriartie on 2008-05-06
Trying to install 8.04 from the live CD.

I have a 500GB Sata2 Hard-drive partitioned as follows:
2GB - FAT 32 - Win 98 installed
10GB - NTFS - Win XP installed
10GB - NTFS
10GB - FAT 32
100GB - NTFS
300GB - NTFS
33GB - Unpartitioned (to be used by a linux distro)

I get as far as the "partition" section, and see that the automatic thing wants to split up my 300GB partition and install ubuntu onto a 140GB affair.
So I select manual, it scans my hard-drives and....
It is only listing the middle five partitions of the list above (not the Win98 partition or the unpartitioned space).
It lists them as sda5 through sda9 (when did it become SDA anyway? I'm sure it always used to be HDA).

So why did it not find the 33GB of unpartitioned space? Windows can find it. I'm currently logged into XP and have just formatted the 33GB to NTFS, hopefully ubuntu will find it this time.

---

### Post by Moriartie on 2008-05-07
Tried again, and this time the installer still didn't find the 2gb win98 partition, but did see the 33gb ntfs partition. I deleted this partition and then the installer managed to find the win98 partition too. Strange.

But after installation the ubuntu installer appears to have killed the ntldr file that is on the boot partition because windows couldn't find it and thus couldn't boot, so I had to re-install XP. Strange because no previous versions of linux I've tried have messed with that file.

---

### Post by Pumalite on 2008-05-07
Did you ever see Grub on reboot after the installation of Ubuntu?

---

### Post by az on 2008-05-07
> **Moriartie said:**
> Tried again, and this time the installer still didn't find the 2gb win98 partition, but did see the 33gb ntfs partition. I deleted this partition and then the installer managed to find the win98 partition too. Strange.

But after installation the ubuntu installer appears to have killed the ntldr file that is on the boot partition because windows couldn't find it and thus couldn't boot, so I had to re-install XP. Strange because no previous versions of linux I've tried have messed with that file.

It's possible that some windows tools created a non-standard partition table.  In which case you can get funny results.  When parted tries to manage such a non-standard partition table, you can end up with odd results.

If XP couldn't boot, it's more likely that the partition table was incorrect and that's why XP couldn't find its ntldr.

Take a look at your current partition table using cfdisk and see if it complains.

As for your devices being called sda instead of hda, that's irrelevant.  Depending on your motherboard, your ide drive may be handled by a sata driver.  Ubuntu uses filesystem UUIDs instead of device mapping anyway.

---

### Post by knitmom on 2008-05-07
nope.  It is like grub doesn't exist.  Though it found all the stages and it said it was working fine in terminal mode.

Also, I have a an ide hard drive and a sata HD.  I noticed it calls the sata drive "sd" and my regular hard drive "hd"

I had this issue with grub awhile back when I upgraded my other all linux machine.  I had to edit the grub to reflect the changed name of the drive.  But I can't even get to that point on this machine.  It is like it vanished.  

I had 7.10 dual booted with Vista and it worked, though the grub had two vista loaders listed.  Now I tried to upgrade to 8.04 and the grub file is gone and get error 22 no such partition.  I'm not sure where anything went.  I manually partitioned the hd with a live cd, maybe I'm forgetting something.  Was I also suppose to make a boot partion too? Or is all of that handled in the ext3 partition?  I don't know.  Very frustrating.  I even tried to reinstall 8.04, but no luck.  Very messed up.

knitmom

---

### Post by Pumalite on 2008-05-07
Post:
sudo fdisk -l
cat /boot/gfrub/menu.lst

---

### Post by knitmom on 2008-05-08
I tried it and it didn't work.

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xf7008d0d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1        1275    10240000   27  Unknown
/dev/sda2   *        1275        6374    40958131    7  HPFS/NTFS
/dev/sda3            6375        9729    26949037+   5  Extended
/dev/sda5            6375        6617     1951866   82  Linux swap / Solaris
/dev/sda6            6618        9049    19535008+  83  Linux
/dev/sda7            9050        9729     5462068+  83  Linux

Disk /dev/sdb: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0xc349d8d5

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           1        1216     9767488+   c  W95 FAT32 (LBA)
/dev/sdb2            1217        9730    68381696    7  HPFS/NTFS
ubuntu@ubuntu:~$ cat /boot/grub/menu.lst
cat: /boot/grub/menu.lst: No such file or directory
ubuntu@ubuntu:~$ 



I even tried > cat /boot/gfrub/menu.lst but I it looked like a typo for grub.

When I mount the root dir with the partition etc, it will install grub with no errors.  It finds all of the stages.  When I go to reboot it either hangs up or I get a partition 22 error.  Which in the past I edited the grub menu.lst file and it worked. (I can see the grub dir listed, but the menu.lst isn't in there for some reason.  therefore I can't edit it. Could it be somewhere else? Is this when I should use the super grub disk?) 
The dual boot I'm working with is Ubuntu and Vista.

Thanks,
Knitmom

PS:  Ubuntu is installed on sda6 and my home directory is on sda7.  should I make a separate boot directory?

---

### Post by Pumalite on 2008-05-08
/boot/grub/menu.lst should be in sda6

---

### Post by knitmom on 2008-05-08
I fixed it.  

I reinstalled 8.04 and while I was in step 7 of the install, I clicked on advance and had the boot loader start from disk sda.  It loaded Ubuntu.  Now I need to see if it will load vista.

Now I just need to fix the screen.  I'm using a wide screen monitor and have the horizontal all the way to the left and I'm still missing the right portion of the desktop.  Oh well!

Thanks again,
Knitmom

---

### Post by knitmom on 2008-05-08
On a roll, the screen is fixed now!  Wahoo!  I think I'm going to like Hardy Heron!!!!

---

### Post by Malibyte on 2008-05-10
Upgraded three machines thus far: one from 7.10 to 8.04 and two from 6.06LTS to 8.04.

Two of the machines have both SATA and IDE hard drives.  On one, the IDE device changed from hda to sde (I have a RAID array on that box comprising sdb, sdc, and sdd - all SATA drives).  I had no problems with that machine because the device designator for the boot drive, /dev/sda, didn't change.

However, the other one has a SATA drive as the boot disk and a removable IDE drive.  When I did the upgrade, only the SATA drive was running.  Now, if I put the IDE drive back in, grub finds the SATA boot drive, but once it begins to boot, sda becomes sdb and the IDE drive becomes sda - so, therefore, it can't find the root partition (was sda5, all of a sudden became sdb5, but it's still looking for the root partition on sda5, so obviously it's a no-go).  In a nutshell, I can no longer use my removable IDE drive.

Is there any way to prevent this from happening?  And what's the logic behind changing the device mapping....?  Having IDE drives mapped as /dev/hdx worked fine before.

Otherwise, things have gone pretty well.  All three of the machines are running OK otherwise.  

Thanks
Bob

---

### Post by Pumalite on 2008-05-10
Something to read:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

---

### Post by Malibyte on 2008-05-10
> **Pumalite said:**
> Something to read:
[http://ubuntuforums.org/showthread.php?t=567907](http://ubuntuforums.org/showthread.php?t=567907)

[http://ubuntuforums.org/showthread.php?t=593615&page=2](http://ubuntuforums.org/showthread.php?t=593615&page=2)

Hmmm...this isn't quite on point for what I need.

On this box, I simply need the SATA drive to remain as /dev/sda whether or not the IDE removable drive is present.  I have set this to be the case in BIOS already, but Ubuntu seems to ignore that setup.

Doing the map switch hd0 <-> hd1 I suspect will cause the system to puke if the IDE drive isn't there.

???

Thanks

---

### Post by Pumalite on 2008-05-10
If you are dual booting; the solution is to have both OS's in the first drive (SATA?)

---

### Post by Malibyte on 2008-05-10
The system does have more than one OS on it (kids still use Winbloze) and both are on the SATA drive.  The IDE drive just has data/storage partitions on it.

Again, everything's fine when the IDE drive isn't installed (it's in one of those removable drive bays that uses the IDE controller on the motherboard, NOT an external USB or Firewire drive).  If I put the IDE drive in, grub comes up OK, boots the kernel off of the SATA drive, but somewhere during that time the device designations change - the IDE drive becomes sda, the SATA drive becomes sdb...when the system tries to read stuff on the root partition (originally sda5, now sdb5; the "new" sda5 is a 30G data partition (currently empty) on the IDE drive).  I get the "hit control-D" prompt at that point; doing so shows me that none of the system binaries are there (as would be expected).

Thanks
Bob

---

### Post by Pumalite on 2008-05-10
It sounds like a problem of BIOS configuration.

---

### Post by Malibyte on 2008-05-10
> **Pumalite said:**
> It sounds like a problem of BIOS configuration.

I don't think so, because the hard-drive order in the BIOS is as it should be.

To top this all off - I just fired up one of my other machines a few minutes ago (the one with the RAID array mentioned in my first post) - it's now doing the same thing.  Won't boot; sda is now sdc; sdb -> sdd are now sdd -> sdf.  The only thing I did while the box was up last time was to pull some pics off of my camera.  Disconnecting the camera didn't solve it.  The hard-drive order in BIOS on that box is as it should be, also.  It also has a removable IDE drive as well as an old LS-120 floppy and a DVD-RW drive on the IDE channels.

I have also noticed, from a it and a third machine that I'm trying to install on (but can't because of issues with X and the ATI video card in that machine), this kernel seems to assign EVERYTHING to a /dev/sdX, and seems to always assign REMOVABLE drives BEFORE hard disks...I have a USB card reader in that box, and the hard drives came up as sdf and sdg until I disconnected the card reader (even though there were no memory cards in it)...then they came back to sda and sdb.  

WTF??

---

### Post by Pumalite on 2008-05-10
Your solution might well be to have your OS in the IDE and use the SATA as storage.

---

### Post by Malibyte on 2008-05-10
> **Pumalite said:**
> Your solution might well be to have your OS in the IDE and use the SATA as storage.

I should not have to do that.  Everything worked fine under Dapper, Feisty and Gutsy.  I shouldn't have to reconfigure all of my Ubuntu machines because of this new....feature.

:confused:

---

### Post by Pumalite on 2008-05-11
As far as I can remember it has always been better to have all SATA or all IDE.

---

### Post by Malibyte on 2008-05-11
> **Pumalite said:**
> As far as I can remember it has always been better to have all SATA or all IDE.

Probably true.  However, everything worked fine before....it should still work now.  Hardy obviously has problems with these types of configurations, and I'm quite sure I'm NOT the only one out here with mixed SATA/IDE boxes.

EDIT:  I figured out a fix for it: [http://ubuntuforums.org/showthread.php?p=4934976#post4934976](http://ubuntuforums.org/showthread.php?p=4934976#post4934976).  I still like the old way better; "/dev/sda5" is a lot easier to deal with than the UUID designators.  And I still think that it should map hard drives ahead of removable media.  But at least the machines boot up now.

---

