---
title: "3 problems installing"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by LostFarmer on 2011-04-07
In the past week have installed Ubuntu -10.10 and igolaware-2.0 both have the same 3 problems. I did get all fixed but wanted to post my problems.

I installed both from direct hdd install.  With below command in grub 2 menu.
```
menuentry "Boot Ubuntu 10.10 Live ISO" {
     set root=(hd0,3)
     loopback loop (hd0,3)/ubut/ubuntu-10.10-desktop-i386.iso
      linux (loop)/casper/vmlinuz boot=casper iso-scan/filename=/ubut/ubuntu-10.10-desktop-i386.iso file=(loop)/preseed/ubuntu.seed quiet splash --
       initrd (loop)/casper/initrd.lz
}
``` for igolaware path and names were changed.

Problem #1 after several aborted installs figured out at step titles "Who Are You ?" the user name must not be in CAPS or you will not get next to enable.  A warning needs to be added to that display.

problem #2  After install, needed to continue with live version to update my grub legacy menu.lst .  When I wanted to reboot the shut down icon at top right of display was missing , had to open terminal and use '/sbin/reboot' . A new user would have to do a hard power off, not to good.

problem #3  After reboot on both installs it had deleted **sda8**. Not a good thing to do. Recovered with 'testdisk'.  Posting a modifed fdisk-l output.

```
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1           16708       17982    10241437+  83  Linux [COLOR=Red]igolaware /[/COLOR]
/dev/sda2   *       17983       19895    15366172+  83  Linux  Mepis
/dev/sda3            7653       12752    40965750    f  W95 Ext'd (LBA)
/dev/sda4            5740        7652    15366172+  83  Linux
/dev/sda5            7653        9565    15366141    c  W95 FAT32 (LBA)
/dev/sda6            9566       11478    15366141    7  HPFS/NTFS
/dev/sda7           11479       11580      819283+  82  Linux swap / Solaris
/dev/sda8           11581       12752     9414058+  83  Linux  [COLOR=Red] igolaware /home[/COLOR]

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1         638     5124703+  12  Compaq diagnostics
/dev/sdb2             639        2354    13775769    f  W95 Ext'd (LBA)
/dev/sdb3            2354        2550     1582371   83  Linux  the used grub 2 for installing
/dev/sdb4            2551        4997    19655527+   c  W95 FAT32 (LBA)
/dev/sdb5             639        2353    13775706    7  HPFS/NTFS  XP


/dev/sdc1               1        1275    10241406    c  W95 FAT32 (LBA)
/dev/sdc2   *        3188       10995    62717729+   f  W95 Ext'd (LBA) XP
/dev/sdc5            3188        5735    20466778+   7  HPFS/NTFS
/dev/sdc6            5736        8923    25607578+  83  Linux
/dev/sdc7            8924        9178     2046976   82  Linux swap / Solaris
/dev/sdc8            9179       10995    14595021   83  Linux [COLOR=Red]Ubuntu / and /home[/COLOR]

```  sda and sdb has in the MBR 'PLOP' boot/partition manager and sdc has grub 2.

---

### Post by Hippytaff on 2011-04-07
Glad you sorted it - others will find your experiences useful :-)

---

### Post by srs5694 on 2011-05-15
FWIW, I just tried duplicating problem #3 and failed; however, there were a number of differences between the attempts, so strong conclusions can't be drawn.

I used VirtualBox to create duplicates of your /dev/sda and /dev/sdb partition layouts, but I didn't bother with /dev/sdc; instead, I installed Ubuntu's root (/) to /dev/sdb4 and used /dev/sdb3 as /boot (I assumed that's what the comment about GRUB 2 next to that partition meant). It's conceivable that the absence of /dev/sdc in my test was critical; however, a more likely issue is that the partitions got re-ordered when you restored them with TestDisk. For instance, perhaps they were out of order before and this triggered a bug.

Also, I didn't have an Ubuntu 10.10 handy, so I used 11.04 (the AMD64 version). FWIW, your problem #1 has been fixed in 11.04; if the username begins with a capital letter, the installer complains.

It's not clear if you did anything with /dev/sda during your install. (Ubuntu would presumably have detected the swap partition automatically.) For instance, if you set mount points for any of the existing Linux partitions there, that could be critical in understanding what happened. A mis-click in an attempt to set a mount point for /dev/sda8 could conceivably have resulted in a deletion, for instance; or adjusting partition sizes or adding or deleting other partitions might have triggered a bug that might have deleted /dev/sda8 unbidden.

Overall, I suspect that this was either user error (an accidental request to delete the partition) or it was triggered by something specific about your initial configuration that's not apparent now, after the fact. Either way it's an issue -- a user interface that permits accidental deletion of a partition without the user even realizing it is very poor; and silently deleting a partition because of an unusual or even a damaged partition table is also very bad.

---

### Post by LostFarmer on 2011-05-15
Problem was with Ubuntu,Xubuntu and igolaware, all 3 uses the same installer.

1) sdb3 'grub 2'  was used only to boot into the ISO file.
2) all partitioning was done with Mepis before installing.
3) installer wanted to unmount the swap partitions, I said NO.
4) sda7 was mounted as SWAP
5) sdc7 was not mounted as swap but some other mount point ( do not remember /name)
6) on all 3 installs / and /boot was on the same partition
7) on 2 installs / and /home was on same partition
8) on 1 install /home was on the deleted sda8 partition
9) When I installed igolaware /home was on sda8 and before reboot I ran 'fdsik' ,sda8 was listed but upon reboot it was deleted

10) If I remember correctly not only was sda8 deleted but the sda7 (swap) was also corrupted.

My other big complaint with the installer ,  after the install I then continued to use the OS to edit Mepis's grub menu.  When I wanted to reboot/shutdown the menus to do so was missing, had to get to root terminal and run '/sbin/reboot'.

---

### Post by srs5694 on 2011-05-15
> **LostFarmer said:**
> [noparse]8)[/noparse] on 1 install /home was on the deleted sda8 partition
9) When I installed igolaware /home was on sda8 and before reboot I ran 'fdsik' ,sda8 was listed but upon reboot it was deleted

10) If I remember correctly not only was sda8 deleted but the sda7 (swap) was also corrupted.

These three together are critically important. They strongly suggest that the installer did not actively delete /dev/sda8, but that some other bug or problem (such as a mis-sized /dev/sda7 or a bug in the swap code) caused the definition for /dev/sda8 to be overwritten. The reason I say this is that logical partitions are defined in a linked-list data structure. Specifically, each partition has associated with it a one-sector data structure known as an Extended Boot Record (EBR), which defines the partition's location on the disk *and* points to the next partition. The EBR normally appears immediately before the partition it defines. Thus, hypothetically, if /dev/sda7 and/or /dev/sda8 were created improperly so that they overlap, then /dev/sda8's EBR would be inside /dev/sda7, and subject to damage when the swap space was used. Thus, if you happened to get unlucky when preparing or using swap space, the EBR for /dev/sda8 would be overwritten and the partition would be effectively deleted. The same thing could theoretically happen if the swap space was prepared at a certain size, /dev/sda7 was shrunk without resizing the swap space it contained, and /dev/sda8 was then created so that it overlapped with the swap space (but not with the swap partition). I don't know, however, if the Linux kernel includes safety checks to prevent damage in these types of scenarios; if it does, then the problem shouldn't have occurred. Your observation that swap was corrupted could have occurred if swap was used and something subsequently tried to modify /dev/sda8; or it could be that a bug, memory corruption, or some other problem caused swap to be mis-written, perhaps exceeding the swap partition's (and swap space's size).

In any event, there are a number of possibilities along these lines. Some of them assume a partition table that was damaged going into the process; others rely on bugs, memory corruption, or damage to the swap data structures. Given that you've done a lot with the disk since the damage occurred, it's hard to distinguish between these possibilities, much less others that would involve bugs or other problems in the partitioning code. Still, you might want to run a couple of checks:


[list]
[*]Type "sudo fdisk -lu /dev/sda" to view your partitions with sector precision rather than the much less precise cylinder values in your original post. You can then check for overlap between /dev/sda7 and /dev/sda8.
[*]Type "swapon -s" to view the size of your swap space (in kilobytes). You can compare this to the size of your swap partition, as revealed by fdisk. If your swap space is larger than your swap partition, you should correct the problem immediately.
[/list]


Either of these tests could turn out OK now even if there was a problem in the past, and based on your description of what you did, I think it's unlikely you'll find problems. I suggest doing these things just to be 100% sure of that, since a problem could cause your /dev/sda8 to disappear again.

Your observation that on one installation, fdisk revealed /dev/sda8 to exist prior to a reboot, but that it was gone after the reboot, completely exonerates the installer's partitioning code; there's no way this could have happened if it was a bug in the partitioner. Instead, something happened between that fdisk call and your next check of it after the reboot to make it disappear. Since the kernel and system shutdown and startup scripts don't normally modify partitions, my hypothesis about corruption involving swap seems likely. I can think of some other possibilities, though, like a bad GRUB configuration (GRUB has the power to mess with partition tables) or an unusual system startup or shutdown configuration that calls sfdisk or some other partitioning tool.

---

### Post by LostFarmer on 2011-05-15
> Extended Boot Record (EBR) Not sure of the correct name, I normally call it the Extended Partition Table but reading your diffination it is one the the same. I will call it the EBR.

I edited the EBR  for sd7 and removed the SWAP partition entire but kepted the link to sd8's EBR. There by removing the swap and kept my HOME partition at sda8.  

Booted into the ubuntu ISO, it boots to the desktop where I can then select install.  After the install sda8 was not deleted.


I reedited sd7's EBR to redo swap and reformatted it. (downside all my /etc/fstab's are now wrong for swap UUID's)

1)Booted into a different grub2 and selected the ubuntu's ISO.
2) once booted to ubuntu's desktop , did a $swapoff /dev/sda7
3) selected install
4) upon reboot sd7 and sd8 were bad
Rebooted into a live cd, fdisk for sda
```
dev/sda1   *   268397955   288880829    10241437+  83  Linux
/dev/sda2       288880830   319613174    15366172+  83  Linux
/dev/sda3       122929380   204860879    40965750    f  W95 Ext'd (LBA)
/dev/sda5       122929443   153661724    15366141    c  W95 FAT32 (LBA)
/dev/sda6       153661788   184394069    15366141    7  HPFS/NTFS
/dev/sda7   ?  1267034307  1602644162   167804928    1  FAT12
```Upon more investigating found that EBR for sda6 did not point to sda7's EBR, there by messing up the links to sda7 and sda8.

after each failed install, the partitions were fixed with 'testdisk' and verified that all other installs of OS's work.

would try the newer version but I only have 256m memory.

---

### Post by srs5694 on 2011-05-16
That's very peculiar. I've never before heard of this type of corruption being caused by libparted (which is what the Ubuntu installer relies upon for doing the partitioning "dirty work"). Based on your description earlier of fdisk seeing the partitions correctly after the installation and prior to a reboot, I don't see how libparted could be doing the damage -- fdisk reads the data from the disk at the moment it's run, so it can't be using old data (unlike the kernel, which could be hanging on to old data until it reboots), and by that time libparted has long since finished its work.

Your latest data seems to implicate something writing beyond the end of /dev/sda5, if /dev/sda6's EBR is damaged. OTOH, it didn't seem to be having problems before. Your latest output shows no overlap between these two partitions.

This is getting weird enough that I'm going to pull out one of my rules of thumb: When problems are weird, suspect the hardware. Have you run any SMART tests on this drive? It's conceivable that it's got a bad sector or even a logic board problem that's manifesting in this peculiar way. If so, a SMART test will probably raise a red flag or two.

One more point: Rather than using TestDisk when doing such tests, I recommend you back up the partition table with sfdisk:

```
sudo sfdisk -d /dev/sda > parts.txt
```

Copy parts.txt to a safe location (like a USB flash drive). You should then be able to restore your partitions by doing the reverse operation:

```
sudo sfdisk -f /dev/sda < parts.txt
```

This is likely to be safer than using TestDisk, which is known to sometimes create flaky partition tables and is not guaranteed to find anything, particularly if a filesystem has been damaged.

---

### Post by LostFarmer on 2011-05-16
> Your latest data seems to implicate something writing beyond the end of /dev/sda5, if /dev/sda6's EBR is damaged.  Not so, should have posted the raw data from the EBR. The start sector for the next EBR (sda7's) only is being changed, it is not being overwritten with junk but is being rewritten during shutdown.

Will run a memory test.

output of bad EBR using 'dd xxx|hexdump'
```
00001b0 0000 0000 0000 0000 0000 0000 0000 fe00
00001c0 ffff fe07 ffff 003f 0000 effa 01d4 fe00
00001d0 ffff fe05 ffff **e035 03a9** 00e6 0019 0000
00001e0 0000 0000 0000 0000 0000 0000 0000 0000
00001f0 0000 0000 0000 0000 0000 0000 0000 aa55
```

correct EBR:
```
00001b0 0000 0000 0000 0000 0000 0000 0000 fe00
00001c0 ffff fe07 ffff 003f 0000 effa 01d4 fe00
00001d0 ffff fe05 ffff **e072 03a9** 00e6 0019 0000
00001e0 0000 0000 0000 0000 0000 0000 0000 0000
00001f0 0000 0000 0000 0000 0000 0000 0000 aa55

```

The start sector number is in **bold**, as you can see the last significant bits are changed.

I will run one other test by changing the sda7 from SWAP to an ext2 partition and see what happens.  Removeing the sda7 worked but being sure swap was turned off did not.

I do not know a thing when it comes to linux's programing.

Will use your 'sfdisk >txt'  for recovery.

Smart does have a hit for 'Current Pending Sector Count' of 6 sectors.

---

### Post by srs5694 on 2011-05-16
First, you haven't said when you collected these two EBRs. That's important in assessing the state of the disk. Most importantly, was the second one taken before or after rebooting the computer and seeing the damaged partition table?

Second, as a matter of information, this is clearly the EBR for the first logical partition (/dev/sda5).

Third, your "correct" output indicates that the next EBR begins at sector 184,394,070 -- 0x03a9e072 plus the location of the referencing EBR (that is, the start of the extended partition). This is both reasonable and unreasonable, given the fdisk output you showed in post #6, since it's the sector after /dev/sda6. Was /dev/sda6 defined (as shown by fdisk) at this point, as shown in your earlier fdisk output? If so, that's extremely strange, since it means that the EBR was defining a partition that came *before* it on the disk. I've never heard of this happening, and in fact I believe it's illegal. Thus, I suspect that you've deleted the original /dev/sda6 before you produced this output. If not, please clarify.

If you *have* deleted the original /dev/sda6, then the change in the EBR reference for the next EBR is not invalid, since AFAIK there's no standard for where to place EBRs, except that they must reside between the partition they define and the next-earlier partition on the disk. Thus, with the original /dev/sda6 gone, as far as the partitioning software is concerned, it can place the EBR for the new /dev/sda6 (the former /dev/sda7) within the space that was previously consumed by /dev/sda6. In fact, partitioning software might make such a change because of changes in partition alignment policies. In the past, partitions were aligned on cylinder boundaries, and I note that your "correct" EBR is so aligned. The new policy aligns partitions on 1 MiB boundaries. Although the changed EBR doesn't seem to be aligned for that, I'm not sure what algorithms might have generated this value; perhaps it's just a quirk of those algorithms.

In any event, the real test of the validity of these data structures is whether the EBR points to a valid following EBR. You can trace this out manually, if you like, but of course that's what a partitioning tool like fdisk is for. Doing it by hand can easily produce confusion. (Believe me, I've done it -- and written software that does it! The EBR sector references can be pretty confusing.)

If you care to move forward with a sector editor, I recommend you look at *all* the EBRs at three points in time: Before installation, after installation but before rebooting, and after rebooting. Since it's not clear which of these points you sampled, it's hard to interpret your results; and the lack of a look at the following (/dev/sda6) EBR also makes it difficult to interpret your results.

---

### Post by LostFarmer on 2011-05-16
> output of bad EBR using 'dd xxx|hexdump' was from reboot after install but before fixing with 'testdisk'

> correct EBR: after fixing with 'testdisk'

ran memory test-- all good

sudo sfdisk -d /dev/sda > parts.txtafter looking at parts.txt, will NOT be using that command to fix.  With the information outputted there is no way for it to fix EBR with bad links to the next EBR, it can only fix bad partition information in the EBR's (so it would seem).

Below is data from the hdd in working condition. Will try to do a install tomorrow for the , right before reboot and after reboot but before repair data.

NOTE: it should not matter but PLOP is installed in the MBR where I can select just which partitions to put in the MBR and in what order, I have 12 primary partitions. Only the ones I put in the MBR will be seen and the other will just be free space.  I expect you noticed that most of the hdd seems to be not  partitioned, but it is.

```

 cfdisk /dev/sda
Partition Table for /dev/sda

               First       Last
 # Type       Sector      Sector   Offset    Length   Filesystem Type (ID) Flag
-- ------- ----------- ----------- ------ ----------- -------------------- ----
   Pri/Log           0   122929379      0#  122929380 Free Space           None
 3 Primary   122929380   204860879      0    81931500 W95 Ext'd (LBA) (0F) None
 5 Logical   122929380   153661724     63    30732345 W95 FAT32 (LBA) (0C) None
 6 Logical   153661725   184394069     63    30732345 HPFS/NTFS (07)       None
 7 Logical   184394070   186032699     63     1638630 Linux swap / So (82) None
 8 Logical   186032700   204860879     63    18828180 Linux (83)           None
   Pri/Log   204860880   268397954      0    63537075 Free Space           None
 1 Primary   268397955   288880829      0    20482875 Linux (83)           Boot
 2 Primary   288880830   319613174      0    30732345 Linux (83)           None
   Primary   319613175   488392064      0   168778890 Free Space           None

fdisk /dev/sda
/dev/sda1   *   268397955   288880829    10241437+  83  Linux
/dev/sda2       288880830   319613174    15366172+  83  Linux
/dev/sda3       122929380   204860879    40965750    f  W95 Ext'd (LBA)
/dev/sda5       122929443   153661724    15366141    c  W95 FAT32 (LBA)
/dev/sda6       153661788   184394069    15366141    7  HPFS/NTFS
/dev/sda7       184394133   186032699      819283+  82  Linux swap / Solaris
/dev/sda8       186032763   204860879     9414058+  83  Linux

RAW data from fdisk -x -d  NOTE: the output data is slightly different if 'dd |hexdump' is used.
MBR: 
80 00
0x1C0: C1 FF 83 FE FF FF 83 6D FF 0F 3B 8B 38 01 00 00
0x1D0: C1 FF 83 FE FF FF BE F8 37 11 39 F0 D4 01 00 00
0x1E0: C1 FF 0F FE FF FF E4 C0 53 07 EC 2C E2 04 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

1st EBR: sector 122929380 
00 FE
0x1C0: FF FF 0C FE FF FF 3F 00 00 00 FA EF D4 01 00 FE
0x1D0: FF FF 05 FE FF FF 39 F0 D4 01 39 F0 D4 01 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

2nd EBR: sector 153661725  (This is the EBR listed before but using dd |hexdump)
00 FE
0x1C0: FF FF 07 FE FF FF 3F 00 00 00 FA EF D4 01 00 FE
0x1D0: FF FF 05 FE FF FF 72 E0 A9 03 E6 00 19 00 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

3rd EBR: sector 184394070
 00 FE
0x1C0: FF FF 82 FE FF FF 3F 00 00 00 A7 00 19 00 00 FE
0x1D0: FF FF 05 FE FF FF 58 E1 C2 03 94 4B 1F 01 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

4th EBR: sector 186032700
00 FE
0x1C0: FF FF 83 FE FF FF 3F 00 00 00 55 4B 1F 01 00 00
0x1D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA



```
did check sda6's VBR 'NTFS' to see if its 'total sector'  was 1 less the the partition size, as it should be.

> If so, that's extremely strange, since it means that the EBR was defining a partition that came *before* it on the disk. I've never heard of this happening, and in fact I believe it's illegal If 'fdisk' says that the partition are not in order, then if one looks at the EBR's and its partition , they will be all messed up.

On sda all logical volumes start 0x3f '63' after its EBR, normal.

---

### Post by LostFarmer on 2011-05-17
One important thing that slipped my mind.  When I boot to the first hdd, sda , it has PLOP boot manager that will change the Master Partition Table to what it has stored in its partition table information.  In my case that means if the Extended Partition entire is changed by the OS it will be put back to stored correct data.

I installed onto sda2 and grub on same and sdc was removed.

The main problem that I know see is that sda3 start address is changed, when that is done the other EBR links for proper linking must also be modified.  But when I reboot, Plop changes sda3 back to original start sector there by the other EBR's linking are now wrong.

So the main question is why does the installer (?) change sda3 start sector from  **122929380 to** **122929441**?  That is the root of problem.

I will post the outputs of cfdisk and fdisk with no modification by me.  

Before install as seen from 'try it'.


```
fdisk
  Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   268397955   288880829    10241437+  83  Linux
/dev/sda2       288880830   319613174    15366172+  83  Linux
/dev/sda3       **122929380**   204860879    40965750    f  W95 Ext'd (LBA)
/dev/sda5       122929443   153661724    15366141    c  W95 FAT32 (LBA)
/dev/sda6       153661788   184394069    15366141    7  HPFS/NTFS
/dev/sda7       184394133   186032699      819283+  82  Linux swap / Solaris
/dev/sda8       186032763   204860879     9414058+  83  Linux
```


cfdisk-raw data
Disk Drive: /dev/sda
```
Sector 0:
0x000: B8 00 20 8E C0 8E D0 BC 00 7C 0E 1F FC FA 33 C0
0x010: CD 13 BF 04 00 B8 23 02 B9 04 00 BA 80 00 BB 00
0x020: 01 57 CD 13 5F 73 05 4F 75 EB EB 03 06 53 CB B8
0x030: 00 B8 8E C0 B8 03 00 CD 10 BE 48 01 33 FF B4 07
0x040: AC 0A C0 74 FE AB EB F8 44 69 73 6B 20 72 65 61
0x050: 64 20 65 72 72 6F 72 21 20 53 79 73 74 65 6D 20
0x060: 68 61 6C 74 65 64 2E 2E 2E 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 80 30 34 07
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 3F AA 0B EF 00 00 80 FE
0x1C0: FF FF 83 FE FF FF 83 6D FF 0F 3B 8B 38 01 00 FE
0x1D0: FF FF 83 FE FF FF BE F8 37 11 39 F0 D4 01 00 FE
0x1E0: FF FF 0F FE FF FF E4 C0 53 07 EC 2C E2 04 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

Sector **122929380:**
0x000: EB 63 90 00 00 00 00 00 00 00 00 00 00 00 00 00
0x010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 80 3F 16 C7 00
0x060: 00 00 00 00 FF FA 90 90 F6 C2 80 75 02 B2 80 EA
0x070: 74 7C 00 00 31 C0 8E D8 8E D0 BC 00 20 FB A0 64
0x080: 7C 3C FF 74 02 88 C2 52 BB 17 04 80 27 03 74 06
0x090: BE 88 7D E8 1C 01 BE 05 7C F6 C2 80 74 48 B4 41
0x0A0: BB AA 55 CD 13 5A 52 72 3D 81 FB 55 AA 75 37 83
0x0B0: E1 01 74 32 31 C0 89 44 04 40 88 44 FF 89 44 02
0x0C0: C7 04 10 00 66 8B 1E 5C 7C 66 89 5C 08 66 8B 1E
0x0D0: 60 7C 66 89 5C 0C C7 44 06 00 70 B4 42 CD 13 72
0x0E0: 05 BB 00 70 EB 76 B4 08 CD 13 73 0D F6 C2 80 0F
0x0F0: 84 D0 00 BE 93 7D E9 82 00 66 0F B6 C6 88 64 FF
0x100: 40 66 89 44 04 0F B6 D1 C1 E2 02 88 E8 88 F4 40
0x110: 89 44 08 0F B6 C2 C0 E8 02 66 89 04 66 A1 60 7C
0x120: 66 09 C0 75 4E 66 A1 5C 7C 66 31 D2 66 F7 34 88
0x130: D1 31 D2 66 F7 74 04 3B 44 08 7D 37 FE C1 88 C5
0x140: 30 C0 C1 E8 02 08 C1 88 D0 5A 88 C6 BB 00 70 8E
0x150: C3 31 DB B8 01 02 CD 13 72 1E 8C C3 60 1E B9 00
0x160: 01 8E DB 31 F6 BF 00 80 8E C6 FC F3 A5 1F 61 FF
0x170: 26 5A 7C BE 8E 7D EB 03 BE 9D 7D E8 34 00 BE A2
0x180: 7D E8 2E 00 CD 18 EB FE 47 52 55 42 20 00 47 65
0x190: 6F 6D 00 48 61 72 64 20 44 69 73 6B 00 52 65 61
0x1A0: 64 00 20 45 72 72 6F 72 0D 0A 00 BB 01 00 B4 0E
0x1B0: CD 10 AC 3C 00 75 F4 C3 00 00 00 00 00 00 00 FE
0x1C0: FF FF 0C FE FF FF 3F 00 00 00 FA EF D4 01 00 FE
0x1D0: FF FF 05 FE FF FF 39 F0 D4 01 39 F0 D4 01 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

Sector 153661725:
0x000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FE
0x1C0: FF FF 07 FE FF FF 3F 00 00 00 FA EF D4 01 00 FE
0x1D0: FF FF 05 FE FF FF 72 E0 A9 03 E6 00 19 00 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

Sector 184394070:
0x000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FE
0x1C0: FF FF 82 FE FF FF 3F 00 00 00 A7 00 19 00 00 FE
0x1D0: FF FF 05 FE FF FF 58 E1 C2 03 94 4B 1F 01 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

Sector 186032700:
0x000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FE
0x1C0: FF FF 83 FE FF FF 3F 00 00 00 55 4B 1F 01 00 00
0x1D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

```

Sector 122929380 has grub legacy stage1 (could be cause of problem ?)
I did zero out sector 12292441 (by booting into XP) before the last install attempt but the sda3 was still put on that same start sector.

after install before reboot and correction by PLOP.

```
fdisk
   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *   268397955   288880829    10241437+  83  Linux
/dev/sda2       288880830   319613174    15366172+  83  Linux
/dev/sda3       **122929441**   204860879    40965719+   f  W95 Ext'd (LBA)
/dev/sda5       122929443   153661724    15366141    c  W95 FAT32 (LBA)
/dev/sda6       153661788   184394069    15366141    7  HPFS/NTFS
/dev/sda7       184394133   186032699      819283+  82  Linux swap / Solaris
/dev/sda8       186032763   204860879     9414058+  83  Linux

```


Cfdisk Raw Data
Disk Drive: /dev/sda
```
Sector 0:
0x000: B8 00 20 8E C0 8E D0 BC 00 7C 0E 1F FC FA 33 C0
0x010: CD 13 BF 04 00 B8 23 02 B9 04 00 BA 80 00 BB 00
0x020: 01 57 CD 13 5F 73 05 4F 75 EB EB 03 06 53 CB B8
0x030: 00 B8 8E C0 B8 03 00 CD 10 BE 48 01 33 FF B4 07
0x040: AC 0A C0 74 FE AB EB F8 44 69 73 6B 20 72 65 61
0x050: 64 20 65 72 72 6F 72 21 20 53 79 73 74 65 6D 20
0x060: 68 61 6C 74 65 64 2E 2E 2E 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 80 30 34 07
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 3F AA 0B EF 00 00 80 FE
0x1C0: FF FF 83 FE FF FF 83 6D FF 0F 3B 8B 38 01 00 FE
0x1D0: FF FF 83 FE FF FF BE F8 37 11 39 F0 D4 01 00 FE
0x1E0: FF FF 0F FE FF FF 21 C1 53 07 AF 2C E2 04 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

Sector **122929441**:
0x000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FE
0x1C0: FF FF 0C FE FF FF 02 00 00 00 FA EF D4 01 00 FE
0x1D0: FF FF 05 FE FF FF FC EF D4 01 39 F0 D4 01 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

Sector 153661725:
0x000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FE
0x1C0: FF FF 07 FE FF FF 3F 00 00 00 FA EF D4 01 00 FE
0x1D0: FF FF 05 FE FF FF 35 E0 A9 03 E6 00 19 00 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

Sector 184394070:
0x000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FE
0x1C0: FF FF 82 FE FF FF 3F 00 00 00 A7 00 19 00 00 FE
0x1D0: FF FF 05 FE FF FF 1B E1 C2 03 94 4B 1F 01 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA

Sector 186032700:
0x000: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x010: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x020: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x030: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x040: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x050: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x060: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x070: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x080: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x090: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0C0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x0F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x100: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x110: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x120: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x130: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x140: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x150: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x160: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x170: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x180: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x190: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1A0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1B0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 FE
0x1C0: FF FF 83 FE FF FF 3F 00 00 00 55 4B 1F 01 00 00
0x1D0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1E0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00 00
0x1F0: 00 00 00 00 00 00 00 00 00 00 00 00 00 00 55 AA


```

hope  all is clear on just what is going on.

---

### Post by srs5694 on 2011-05-18
> **LostFarmer said:**
> One important thing that slipped my mind.  When I boot to the first hdd, sda , it has PLOP boot manager that will change the Master Partition Table to what it has stored in its partition table information.  In my case that means if the Extended Partition entire is changed by the OS it will be put back to stored correct data.

Well, *that's* the problem, then!

A boot loader that juggles partitions around like this is a dangerous hack. Note there's no "IMHO" in that statement. I feel justified in omitting it because I'm the author of a family of Linux partitioning software ([GPT fdisk,](http://www.rodsbooks.com/gdisk/) consisting of gdisk, sgdisk, and FixParts), which gives me a deeper understanding of the issues involved than most possess.

> The main problem that I know see is that sda3 start address is changed, when that is done the other EBR links for proper linking must also be modified.  But when I reboot, Plop changes sda3 back to original start sector there by the other EBR's linking are now wrong.

So the main question is why does the installer (?) change sda3 start sector from  **122929380 to** **122929441**?  That is the root of problem.

It's a partitioning utility's job to change the way partitions are defined, and most OS installers include partitioning utilities and run them as a matter of course. Such a utility will do so as it sees fit, and if some other utility (like a boot loader) makes assumptions about data structures not changing when a partitioning utility runs, then it's the other utility's fault when problems occur. I commented earlier that, AFAIK, there's no standard for where EBRs are to be placed -- or for that matter where an extended partition should begin, relative to the first logical partition it contains. These things can and do change when you run a partitioning utility. Note also that the recent change from alignment on "cylinder" boundaries to alignment on 1 MiB boundaries has resulted in changes in how partitioning utilities compute where to place EBRs, and hence where to begin extended partitions.

I recommend you figure out some other way to do whatever you're doing with PLOP, or at least disable its partition-hiding features so that it stops causing you problems. I note that the partition table you showed earlier has Linux consuming at least two primary partitions. This isn't necessary. Using standard partitioning, you can fit three Windows installations on primary partitions on a single disk, and put Linux entirely in logical partitions, if that's what you need. You also apparently have two other disks on your system, so you can have up to nine permanent primary partitions, plus logicals on all disks. If you're juggling partitions around for some other reason and can't figure out another way to do it, please describe why. There may be a better solution than using software that juggles partition tables around.

From my perspective, the original problem that prompted me to participate in this thread is now solved. In your original post, you wrote:

> problem #3  After reboot on both installs it had deleted **sda8**. Not a good thing to do. Recovered with 'testdisk'.  Posting a modifed fdisk-l output.

Ubuntu's installer did *not* delete /dev/sda8; PLOP did!

---

### Post by LostFarmer on 2011-05-18
> Ubuntu's installer did *not* delete /dev/sda8; PLOP did! 	

I have been using PLOP for 15 years with no problems with MS, SuSe, Mepis.

 If I do not tell linux installer to change partitions then it should not do so. If I change partition then I will tell PLOP to update, no problems.

> I commented earlier that, AFAIK, there's no standard for where EBRs are to be placed in that case why would a installer fill free to mess with partitions on it own, when there is no need. One complaint about MS , must have it there way or else.

> It's a partitioning utility's job to change the way partitions are defined, only if I tell it to, otherwise it should leave it alone. It should not be changing partitions just because some programmer fills like its his/her job to cause problems.  I say leave my partitions alone unless I tell it to make a change or finds an error and reports it to me.

When duel booting with MS , people do put linux on a logical volume but keep MS's MBR and put grub legacy to the extended partition, made active.  Then if they install ubuntu and put grub 2 into '/', then they might have a non operating system due to it's installer deciding on its own to move predefined partitions around.  They will be forced to reinstall grub ( if they can figure out how )  to the MBR and some times cause problems with MS updates (so I have read for vista and 7).  

BTY - thanks for your help, I now know what the problem is.

> I feel justified in omitting it because I'm the author of a family of Linux partitioning software ([GPT fdisk,]("http://www.rodsbooks.com/gdisk/") consisting of gdisk, sgdisk, and FixParts), which gives me a deeper understanding of the issues involved than most possess. I do accept your knowledge.  I'm just a end user and do not understand all the requirments of partitions but if there is a true need for a installer to make changes then it should at least ask/tell me.

---

### Post by srs5694 on 2011-05-19
> **LostFarmer said:**
> I have been using PLOP for 15 years with no problems with MS, SuSe, Mepis.

That's not really relevant; what PLOP is doing is still extremely dangerous. The fact that you haven't been burned until now just means you got lucky.

> If I do not tell linux installer to change partitions then it should not do so.

I agree with you in principle; however, as a practical matter you can *not* make the assumption that a partitioner in an OS installer will make no changes to the partition table. In fact, if you modified any logical partition types (by creating new filesystems) the partitioner will have to make changes. In such a case it might be easier, and probably safer, for the program to rewrite all of an extended partition's EBRs in its own way rather than try to modify just the one EBR that was changed. I wrote "and probably safer" because trying to record and duplicate the precise way that an existing partition table wrote its EBRs would complicate the code, thus introducing the possibility of creating new bugs. I haven't checked the libparted code to see what it does, but it might just be recording the start and end points of the partitions and discarding precise EBR locations, since they're theoretically irrelevant.

> One complaint about MS , must have it there way or else.

If you're referring to the shift from cylinder alignment to 1 MiB alignment, although Microsoft led Linux on this shift by a wide margin, Microsoft didn't make this change arbitrarily. Cylinder alignment has been pointless for at least fifteen or twenty years. It's just clung to life because very old software has required it. Today, though, several types of disk (Advanced Format drives, some types of RAID arrays, and SSDs) suffer performance degradation if they aren't aligned to boundaries ranging from 4 KiB to 256 KiB or so, all on power-of-2 values. Kicking it up to 1 MiB gives a little extra safety margin. Thus, 1 MiB alignment is quite sensible.

 FWIW, it's conceivable that OS installers have been rewriting your  partition tables for years and you've never noticed because they've happened to be rewriting them on cylinder  boundaries and placing EBRs in the same locations by sheer luck. With  the change to 1 MiB alignment, this practice has come into conflict with PLOP's risky design.

 > When duel booting with MS , people do put linux on a logical volume but keep MS's MBR and put grub legacy to the extended partition, made active.  Then if they install ubuntu and put grub 2 into '/', then they might have a non operating system due to it's installer deciding on its own to move predefined partitions around.

Installing GRUB in the extended partition (note that's extended, not logical) is foolhardy; you could easily overwrite an EBR and lose all of your logical partitions that way. It's likely you could get away with it with some configurations, but it's playing Russian Roulette with your partitions.

As a side note, the whole MBR partitioning scheme is a messy hack. There's no standards document that defines what everything is supposed to look like; it's just slowly evolved through stages as something that kind-of/sort-of/usually works. Boot loader authors have also engaged in risky practices related to MBR data structures, such as stuffing data in-between the MBR and the first partition. This unallocated space isn't guaranteed to be any particular size, and if two utilities try to use this same space, one will clobber the other.

I for one won't miss MBR when it goes riding off into the sunset, to be replaced by GPT. GPT's got its own problems, but at least it's got a clearly defined standards document and fewer messy hacks to make it work.

---

### Post by LostFarmer on 2011-05-19
[srs5694]("http://ubuntuforums.org/member.php?u=1032238")  I want to thank you and all other people that give free time to do opensource programing.

[QUOTE what PLOP is doing is still extremely dangerous][/QUOTE] I need to correct that with information.  I was using a old version that only checked the 1st and 2nd partition for changes ( did not know that till now) , the new version test all 4 entries for a change and gives a warring to the user and gives an option to use the old data or update with that current data in the MBR. That function does make it 'safer' to use but not fool prof.  Just ask !

I do agree that if one has no knowledge of partitions it should not be used.

---

