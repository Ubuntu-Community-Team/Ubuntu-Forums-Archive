---
title: "Clone the second HD to a third HD"
date: 2005-05-29
forum: Installation &amp; Upgrades
---

### Post by baraider on 2005-05-29
First post, so please let me know if i post in the right forum.

i have a Thinkpad T23 (2647-9lu)

First (internal HD ) is a 7k60 that i have XP on it
Second HD (on the ultrabay drive) is a 40gb drive

I have setup ubuntu on the second HD and I installed GRUB on hdc1 (second hd)....all is well...i can dualboot by press F12 at boot to select which OS.

Is there anyway i can clone the second hd (40gb 4200) into a 7k60, put it in the second bay and boot as normal?

I tried to log in winxp, using acronis true image to make a image of the ubuntu hd, take it off, put the new hd in , restore the image to that hd and boot from the second HD but i have Error loading operating message.


I guess it didn't copy the grub into the new HD

Then after reading around on google, i read that if you use copy image, it will only copy the partition but not hidden files....to make it to copy every bit, including the boot, hidden file, you need to do clone HD


So i look at Acronis true image 8 software again, there is a "Clone Disk" option. I click on clone disk but there is no way to clone it because it only can clone from the internal to the one in ultrabay or vice versa.....

I want to "clone" the second HD to an image and save on the first HD, the take it out, pop in the 7k60, copy the image to it and boot normally..



     This is just like make an image but i want to have the exact bit-by-bit...with the GRUB. There is no way i can have 3 HD connected at the same time...

  thanks for the help

---

### Post by baraider on 2005-05-30
anyone please help this poor guy ](*,)

---

### Post by mingus on 2005-05-30
You may actually be close to your solution.

If I understand you correctly, I suspect you have copied the drive as you wanted, and that this has nothing to do with "hidden files" but rather with the boot loader.

The boot sector is not a "hidden file" in the sense that is used in what you were reading.  Hidden files that cannot be copied are busy OS system files.  Even so, I believe Acronis uses the same technique as the new Ghost, a kernel service which can copy bits when files are open, so this should work (I've done it).  But this is a Windows thing anyway.

Instead, it sounds like a boot loader linkage is broken.  You might try this:

Note:  This assumes you have a floppy drive and can boot from floppy.  Otherwise, see note at msg below.

Boot from a Linux CD and get into a bash shell as root.  Also, you may need access to a text editor from the shell like nano or pico.  I don't know if the Ubuntu CD can do this like other install CD's, but if it can't, Knoppix or Kanotix will do fine.

In the RAM image created, you will have a /mnt directory.  Mount the new HDD into that directory.   (If you setup more than one partition, you will need to create a directory structure in /mnt and mount the partitions accordingly.)

Now chroot into /mnt.  When you do an ls, you should see your new drive's Ubuntu.  /mnt is now effectively the root directory.

Now cd to ./boot/grub and double-check that menu.lst is correctly configured and that device.map shows the floppy.  You should now be able to execute the command "grub-install /dev/fd0" which will install the boot loader on the floppy.  While you are at it, I'd suggest a chain loader section in menu.lst so you can also boot to XP from this floppy.

Now boot from the floppy, log into Ubuntu, and make sure everything is there.  If you are satisfied, you can run grub-install again to install the loader in the MBR or on hdb using chain loader to boot XP.  When I do this kind of thing, I hold off and use the floppy for a while until I'm positive everything is right.  You can do it the other way from XP's boot.ini, but it requires more fiddling about.

One last caution:  It's not hard to accidentally mess up the MBR.  If the above is not your fix, or you run into trouble otherwise, you want to be sure you can still boot into XP.  If your MBR gets hosed, you won't be able to.  To repair this, all you need is an XP or W2K install CD; if you don't have one, create a DOS recovery diskette before you start.  Boot into that, make your way to a command prompt, and then do >fixmbr.  This will restore the XP boot sector to the MBR.

If you do not have a floppy or cannot boot from floppy, you can do the above using the MBR.  Just be extra sure you have the Windows boot media first so that you can repair it if necessary.

Hope this helps.

---

### Post by mingus on 2005-05-30
Quick P.S. to my previous reply . . .

You can use the Ubuntu install CD to do this, but it's a bit tricky.  You have to use "rescue" at the initial boot prompt.  Then go thru the hardware detection, but then hit escape to get to the expert install menu.  There will be a selection to go into a shell.  From there you will need to mount the drive and chroot into that directory.  If you go all the way thru the rescue sequence until it mounts the partition, the shell it drops you into is not the same and nano will not be available should you need it.

But you can do it this way.  I just test it and it worked.

--mingus

---

### Post by baraider on 2005-05-30
Thanks mingus,

I will either try to make the cloned drive active from winxp or do the same as you show.

---

### Post by mingus on 2005-05-30
If by "making the cloned drive active from XP" you mean using the XP boot loader to point to hdb, that won't work unless you've successfully loaded grub into the hdb boot partition.  What XP is doing is the same thing that grub chain loader does.

If you mean changing the hdb partition to the "active" partition with a tool like PartitionMagic, again you must have the boot sector installed or there won't be anything there for the BIOS to hand off to.

You might check out the wiki howto on dual booting for pointers.

--mingus

---

### Post by baraider on 2005-05-31
Mingus,
Thanks for all your time and advice. finally got it to work...this time, the only thing different i did is in xp, using acronis to make an image from the old 40g, take it out, put the 60g in, restore the image, and select that 60g as an active partition (primary). By default, acronis will make it logical partition.

Reboot and voila, it work...

   Now, because the 60gb is bigger, i have an 20gb unclaim. Do you know how i can add it to the end of my boot partition?

Disk /dev/hda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7751    58597528+   7  HPFS/NTFS

Disk /dev/hdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4676    37559938+  83  Linux
/dev/hdc2            4677        7296    21045150    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hdc5            4677        4864     1510078+  82  Linux swap / Solaris
/dev/hdc6            4865        7296    19535008+   b  W95 FAT32
andy@kubuntu:~$

---

### Post by mingus on 2005-05-31
[QUOTE=baraider]Mingus,
Thanks for all your time and advice. finally got it to work...this time, the only thing different i did is in xp, using acronis to make an image from the old 40g, take it out, put the 60g in, restore the image, and select that 60g as an active partition (primary). By default, acronis will make it logical partition.

Reboot and voila, it work...

   Now, because the 60gb is bigger, i have an 20gb unclaim. Do you know how i can add it to the end of my boot partition?

Disk /dev/hda: 60.0 GB, 60011642880 bytes
240 heads, 63 sectors/track, 7752 cylinders
Units = cylinders of 15120 * 512 = 7741440 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hda1   *           1        7751    58597528+   7  HPFS/NTFS

Disk /dev/hdc: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/hdc1   *           1        4676    37559938+  83  Linux
/dev/hdc2            4677        7296    21045150    f  W95 Ext'd (LBA)
Partition 2 does not end on cylinder boundary.
/dev/hdc5            4677        4864     1510078+  82  Linux swap / Solaris
/dev/hdc6            4865        7296    19535008+   b  W95 FAT32
andy@kubuntu:~$[/QUOTE]
 You mean add to hdc1, right?

May I ask why you want to do this rather than just adding a 20GB partition at the end?  That would be *much* easier - and safer.

You can add the 20GB to hdc1, but it is risky.  The problem is that different file systems go about calculating disk geometries differently, and treat this data differently.  Some Linux file systems don't care.  But Windows does, and in fact, FAT and NTFS even go about it differently.  Furthermore, how partitions get moved and partition tables managed can vary between tools.  It can be quite dangerous to use the Windows Disk Manager, Partition Manager, and say fdisk or cfdisk on the same drive.  It is best to create and thereafter manage the partitions with the same tool.

What you want to do involves moving the data, and requires the partition table to be rebuilt.  Also btw, moving the FAT partition without first doing a chkdsk and defrag, only adds to the risk.  If the partitioner runs into an unmarked bad block, you're hosed.

As far as a tool to do this, Acronis has Director, haven't used it.  I've used PartitionMagic, but it cannot handle reiserfs as can Director.  In Linux land, many partitioners cannot actually move, they can only create.  As I recall, QTParted is supposed to be able to move partitions, but I haven't tried it.

It occurs to me that you still have the 40GB Acronis image?  What about rebuilding the partitions from scratch, and then *selectively* reloading from the image what you want on each of the partitions?  This technique doesn't copy the image as a bitmap whole, it pulls out the files to the filesystem on the partition.   I use DriveImage/Ghost, and I'm pretty sure it can do this.  Or you could tar what is on each partition, rebuild the disk partitions, and restore the tar's.  This is one backup technique used in Linux land.

Hope this helps.

--mingus

---

### Post by baraider on 2005-06-01
Yeah, i mean add the 20gb to hdc1.

I still have the 40gb image...i remember doing this before, copy a 120g image to a 200g hd and then just claim the 80g back...but it's xp image.

 I think i can either make the 20g extra a fat32 so i can share it between xp and linux....how do i do this..

 Or i can backup the home and /etc directory....install ubuntu to the 60g after format it to full 60gb....and then copy the /etc/ and /home back..

 Which one you think is correct/better?

thanks

---

### Post by mingus on 2005-06-01
First, a question . . . I'm assuing that Ubuntu created hdc1.  What was used to create the extended partition with its swap and vfat logicals?

---

