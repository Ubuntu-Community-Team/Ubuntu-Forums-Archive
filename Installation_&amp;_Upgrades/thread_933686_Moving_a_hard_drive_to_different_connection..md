---
title: "Moving a hard drive to different connection."
date: 2008-09-29
forum: Installation &amp; Upgrades
---

### Post by 73ckn797 on 2008-09-29
Would moving Hd0 with Hardy Heron from an IDE to SATA1 connection with an adapter for PATA-SATA be a no problem deal? I will not put any HDD back on the IDE channel but will still have a DVD burner on the IDE but moved to the master position.

I already have one drive using the PATA to SATA adapter with no problems. I would just move it down the chain, so to speak. Nothing currently loaded on this drive.

---

### Post by Patb on 2008-09-29
The idea seems okay. Presumably, you will just try it and see how it goes. 

If you strike any problems, especially with booting or mounting the drive, try booting from a live CD and then checking what partitions are recognisable and what their UUIDs are.
```
sudo fdisk -l
sudo blkid
```
Then make sure the relevant lines in your grub menu and fstab file have the correct partition identifiers and UUIDs as shown in the output of the above commands. Probably a good idea to back up each before editing:
```
sudo cp /boot/grub/menu.lst /boot/grub/menu.bk1 
sudo gedit /boot/grub/menu.lst
```
```
sudo cp /etc/fstab /etc/fstab.bk1 
sudo gedit /etc/fstab
```
Hope this helps. Cheers, Pat.

---

### Post by 73ckn797 on 2008-09-29
> **Patb said:**
> The idea seems okay. Presumably, you will just try it and see how it goes. 

Hope this helps. Cheers, Pat.

I am one who would see what happens. I have no problem doing a reinstall to a different drive or to the one being moved if that has to happen. I have read several posts that imply this will not be a problem. I will await a more definitive answer, if that is possible.

This is indirectly addressed here:
 			 			 			 			 			                         [COLOR=#980101]**[ubuntu]**[/COLOR] 			 			[TAKE NOTE: Grub writting incorrect drive into menu.lst]("http://ubuntuforums.org/showthread.php?t=932692")

---

### Post by 73ckn797 on 2008-10-01
I went ahead and did the following:

Removed the HDD from IDE master and connected to SATA1 connection using PATA to SATA adapter. The BIOS hangs when trying to read SATA drives (there is another 40GiB drive on SATA3 using the same type adapter and BIOS reads it prior to all of this). Removed drive completely and installed a new WD 160GiB drive to SATA1 that I have recently bought. BIOS reads drives after this. Probably does not like the adapted drive in that position (I guess). BIOS read the IDE channel first. I think that I can disable that once everything is on SATA connections.

When booting grub error 22 comes up after installing Ubuntu to the new drive. Ubuntu shows drives as:
sda1 = 160GiB = ext3
sdb1 = 160GiB = unformatted
sdc1 = 40GiB = NTFS (just a data drive)

This **is** the physical order of the HDD's.

Grub is writing the boot drive as hd0 but it is actually hd1. Shouldn't sda = hd0, ..... etc? The sdb drive is currently unformatted which I thought would have been hd1.

Would having a DVD/CD still on the IDE channel be the reason for this? I will probably get a SATA DVD drive (Good deal on one at MicroCenter).

I do not know the command right off the top of my head to see how the system is seeing things. I know I can find it in the forums.

Also: my Mobo is a Biostar TF560 A2+. It has 1 IDE channel and 4 SATA connections. The BIOS is set to IDE for the SATA connections. I have never used RAID but that is one of the BIOS options for the SATA. Should I leave that alone?  ACHI (I think that is correct) is another setting available.

Any suggestions? Or should I just use all available channels with my main drive on IDE master? I would then figure things out as the needs arise.

---

### Post by 73ckn797 on 2008-10-01
Here are the results for the commands you list:

**sudo fdisk -l**

Disk /dev/sda: 160.0 GB, 160041885696 bytes [COLOR=RoyalBlue](Ubuntu)[/COLOR]
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00076969

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       18701   150215751   83  Linux
/dev/sda2           18702       19457     6072570    5  Extended
/dev/sda5           18702       19457     6072538+  82  Linux swap / Solaris

Disk /dev/sdb: 160.0 GB, 160041885696 bytes   [COLOR=RoyalBlue] (not formatted)[/COLOR]
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System

Disk /dev/sdc: 40.0 GB, 40020664320 bytes
255 heads, 63 sectors/track, 4865 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x9b230d97

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1        4865    39078081    7  HPFS/NTFS  [COLOR=RoyalBlue](data files only, no OS)[/COLOR]


** sudo blkid**
/dev/sda1: UUID="32dd3252-53b9-4647-b538-95793e7a55e2" TYPE="ext3" 
/dev/sda5: TYPE="swap" UUID="21425560-9b29-4221-8f19-8cf5a45833b3" 
/dev/sdc1: UUID="30F70D6E790F4174" LABEL="Backups" TYPE="ntfs" 

**GRUB Menu:**
title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic (recovery mode)
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro single
initrd        /boot/initrd.img-2.6.24-19-generic

title        Ubuntu 8.04.1, memtest86+
root        (hd1,0)
kernel        /boot/memtest86+.bin
quiet


Grub menu is after I edited the "hd0" entries originally listed after install. The ID's are correct. I have checked those before.

---

### Post by Patb on 2008-10-02
> Grub is writing the boot drive as hd0 but it is actually hd1. Shouldn't sda = hd0, ..... etc?
No. Grub notation for partitions starts at 0. By contrast, notation for linux starts at "a" or 1. Thus, Grub's "(hd0,0)" refers to "/dev/sda1/". Edit your /boot/grub/menu.lst back to the original setting or (better), if you made a backup of the original, restore it. 

Extract from "info grub":
> 22 : No such partition
This error is returned if a partition is requested in the device part of a device- or full file name which isn't on the selected disk.

This suggests that perhaps you edited the menu.lst file before trying to boot. Going back to the original menu.lst should solve that. 

If you cannot boot with the corrected menu.lst, try reinstalling grub by following the instructions here: [http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351). 

Let us know how you go. 

Cheers, Pat.

---

### Post by vanadium on 2008-10-02
For the OS, there is not any problem when you used UUIDS in your /etc/fstab. These uniquely define a partition and obviously are persistent even if the device assignment changes.

It is different for grub: grub stage one must be on the first drive, and grub uses device assignment. You need to reinstall grub. It is a two minute operation that is not that difficult. Seach for "restore grub".

---

### Post by 73ckn797 on 2008-10-07
Ubuntu loads fine with drive set to hd1,0. Grub wrote it as hd0,0. I will leave it alone for the time being. I have looked at the link for the How-To on Grub and will follow that procedure.

title        Ubuntu 8.04.1, kernel 2.6.24-19-generic
root        (hd1,0)
kernel        /boot/vmlinuz-2.6.24-19-generic root=UUID=32dd3252-53b9-4647-b538-95793e7a55e2 ro quiet splash
initrd        /boot/initrd.img-2.6.24-19-generic
quiet

---

