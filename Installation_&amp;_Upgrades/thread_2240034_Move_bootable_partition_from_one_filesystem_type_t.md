---
title: "Move bootable partition from one filesystem type to another"
date: 2014-08-17
forum: Installation &amp; Upgrades
---

### Post by BatteryKing on 2014-08-17
OS: Ubuntu 14.04 64-bit - Upgraded from 12.04 64-bit and upgraded a number of times before that.
Partition table type - GPT (too big for MBR)

Little at a time I have been moving partitions off of Reiserfs and onto Ext4.  I am down to just one bootable partition on one computer on Reiserfs and I have been trying to avoid a re-install as there is just too much crap on this system.  However my attempts at moving the bootable root partition have gone badly.

So far the closest I have gotten is grabbing pieces out of a few different posts culminating in:

1. Boot off of install disk and switch to command line - Ctrl+Alt+F1
2. Assume root - `sudo su -`
2. Mount backup drive - `mkdir /media/backup`; `mount /dev/sdX /media/backup`
3. DD root partition to backup drive - `dd if=/dev/sda1 of=/media/backup/[folder]/root.img`
4. Reformat root partition to Ext4 - `mkfs.ext4 /dev/sda1`
5. Make mount point for old root - `mkdir /media/rootbk`
6. Mount DD image - `mount /media/backup/[folder]/root.img /media/rootbk`
7. Mount new root - `mount /dev/sda1 /mnt`
8. Copy contents of the old root to the new root (something in this procedure is wrong, but I don't know the right way) - `cp -ax /media/rootbk/. /mnt`
9. Change fstab to point to the new partition UUID:
    a. Get UUID of sda1 - `blkid`
    b. Change fstab - `vi /mnt/etc/fstab`
10. Change Grub to point to new bootable and root partition.  (Note there is both the UUID field and the root partition field for each entry):
    a. Get UUID of sda1 - `blkid`
    b. Change menu.lst - `vi /mnt/boot/grub/menu.lst`
11. Install new bootloader:
    a. Mount new root (done in step #7, so not needed here) - `mount /dev/sda1 /mnt`
    b. Bind /dev - `mount --bind /dev /mnt/dev`
    c. Bind /proc - `mount --bind /proc /mnt/proc`
    d. Bind /sys - `mount --bind /sys /mnt/sys`
    e. Change root - `chroot /mnt`
    f. Install grub - `grub-install /dev/sdX`
    g. Update grub - `update-grub`
12. Unmount and prepare for reboot
    a. Exit chroot - `exit`
    b. Clear /dev binding - `umount /mnt/dev`
    c. Clear /proc binding - `umount /mnt/proc`
    d. Clear /sys binding - `umount /sys
    e. Unmount new root - `umount /mnt`
    f. Unmount old root - `umount /media/rootbk`
    g. Unmount backup - `umount /media/backup`
13. Reboot - `sync`; `reboot`

This procedure gets me to the point where the system starts to boot, but then I get an error that the boot partition has errors and I get the option to drop into a busybox shell.  I can't seem to do anything from here.  Even doing a rw remount fails `mount -o remount,rw /`.  If I fsck the root partition, there are no errors.  If I take out the create new filesystem steps and just DD the old root image back and re-install Grub, everything boots up after and I am good.  However I am still on Reiserfs, which makes me feel like I just went in a big circle for no reason.

Does anybody know the right way to move a root partition from one filesystem type to another?

---

### Post by ubfan1 on 2014-08-17
Just use tar, (assume the new root partition is ext4 and mounted at /mnt/new, 
cd /
sudo tar -cf - * |(cd /mnt/new; sudo tar -xpBf -)
Then fix up the files fstab and grub.cfg like above.
dd just copies the reiserfs back over the ext4, not the right way to move the files.

---

### Post by oldfred on 2014-08-17
Also not supposed to use dd with gpt  partitions. Ok with entire drive.

The gpt partitions have more internal data and need GUIDs also updated if copied as duplicates not allowed. Becomes major work to update all internals if copied. May be possible with gdisk.

 Do not use dd to copy partition with gpt due to unique guids & UUIDs post #12
[http://ubuntuforums.org/showthread.php?t=1680929](http://ubuntuforums.org/showthread.php?t=1680929)
      
 But do not use dd for copies from MBR to gpt partitioned drives, can use cp -a
[https://wiki.archlinux.org/index.php/Disk_Cloning](https://wiki.archlinux.org/index.php/Disk_Cloning)

---

### Post by BatteryKing on 2014-11-01
Using tar instead of cp seemed to fix the problem ubfan1, thanks.  One other thing I did this time around (and I got distracted for a while, so I don't clearly recall all of what I did last time now) is I used sed to replace all instances of the old UUID in /boot/grub/menu.lst.  As I don't recall the method I used before, I thought it would be useful to point out it is good to use a programmatic method such as `sed s/<old uuid>/<new uuid>/g menu.list > menu.lst.output` and then copy back the output file as this ensures every instance of the old UUID in grub gets replaced.

Oldfred, thanks for the heads up about GPT partitions, I will keep that in mind.  I suppose dd worked in my case because I was just using it as a fallback plan in case the copy command did not work as intended, which it did not and at that I was copying to the same place on the same physical drive.

Well I am Reiserfs free now.  Woopi!

---

### Post by oldfred on 2014-11-02
You have to edit fstab with new UUIDs and now with grub2 it is grub.cfg which normally we do not edit. This is the exception. But you really only have to edit the first boot stanza and then use that one entry to boot. A sudo update-grub will then update all UUIDs to be correct.

If a copy you also need to make sure some other settings are correct.
Grub2 remembers which hard drive to reinstall into on major update:
       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

      
 #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

Also check this:

 clean install advantages: swap UUID used for hibernation:
 cat /etc/initramfs-tools/conf.d/resume

 if you recreate a swap partition don't forget to update /etc/initramfs-tools/conf.d/resume with the new uuid

---

### Post by BatteryKing on 2015-01-02
I have had a chance to revisit this thread.  In particular the last of the original mechanical drives in my old hardware RAID 5 array off my 3Ware 9650 controller was replaced with a slightly larger drive after raking up too many remapped sectors for my tastes.  However with all larger drives now, I could not find an easy way to to expand the array size to account for the same number of disks, but just all bigger now with the ancient 3Ware controller after slow attrition of disks over the years.  In case anybody is curious about specifics, about 6 years ago I had a not so great idea to load up with Seagate Barracuda 7200.11 (ST31500341AS) drives; just redo the firmware on them.  The first firmware flash for my test case did not go well and that drive crashed while in testing and the drive was RMA'd.  Then Seagate came out with another firmware update and this seemed to be holding, so I switched over.  The problem I found out is all of these drives start to really rake up the errors over time, but amazingly one drive went a whole 6 years before I gave up on it.  Now the array is mostly WD Se drives.  So far very clean SMART data on those Western Digital Se line drives.

Anywho, here are the specifics that I came up with for moving over to a new array (or drive seeing the 3Ware controller presents the array as one drive).  I considered all of the posts on here and found while some of the information was useful, other information did not seem to pan out when I tried it.  Below is the revised procedure.  (My full system procedure was a bit more complicated because I moved around multiple partitions and had to spread the data across multiple backup drives, but those extra steps can be easily discerned from this.  Also I had other 3Ware specific procedures for destroying and recreating the array and I used Gparted to create the new partition table because it makes creating a GPT partition table and partitions easy.):

1. Boot off of install disk, select "Try Ubuntu", and then open a terminal Window.  (Click on the top left Ubuntu icon and type in terminal in the search box.)
2. Assume root - `sudo su -`
2. Mount backup drive - `mkdir /media/backup`; `mount /dev/sd[X] /media/backup`
3. Mount root partition - `mount /dev/sd[X][Y] /mnt`
4. Tar root partition to backup drive - `cd /mnt; tar -c . -f /media/backup/[folder]/sd[X][Y].tar`
5. Unmount drive - `cd /; umount /mnt`
6. Reformat root partition to Ext4 - `mkfs.ext4 /dev/sd[X][Y]`
7. Mount new root - `mount /dev/sd[X][Y] /mnt`
8. Restore contents - `cd /mnt; tar -xf /media/backup/[folder]/sd[X][Y].tar`
9. Change fstab to point to the new partition(s) UUID:
    a. Get UUID of sd[X][Y] (and any other partitions) - `blkid`
    b. Change fstab - `vi /mnt/etc/fstab`
10. Change Grub to point to new bootable and root partition. (Note there is both the UUID field and the root partition field for each entry):
    a. Get UUID of sda1 - `blkid`
    b. Change menu.lst:
        i. Grub directory - `cd /mnt/boot/grub`
        ii. Change out all instances of old UUID (some people say nay on changing all entries, but I was having issues and this works so...) - `sed s/[old UUID from menu.lst]/[new UUID from blkid]/g menu.lst > menu.lst.output`
        iii. Check output - `less menu.lst.output`
        iv. Commit changes - `cp menu.lst.output menu.lst`
11. Install new bootloader:
    a. Mount new root (done in step #7, so not needed here) - `mount /dev/sd[X][Y] /mnt`
    b. Bind /dev - `mount --bind /dev /mnt/dev`
    c. Bind /proc - `mount --bind /proc /mnt/proc`
    d. Bind /sys - `mount --bind /sys /mnt/sys`
    e. Change root - `chroot /mnt`
    f. Install grub - `grub-install /dev/sd[X]`
    g. Update grub - `update-grub`
12. Unmount and prepare for reboot
    a. Exit chroot - `exit`
    b. Clear /dev binding - `umount /mnt/dev`
    c. Clear /proc binding - `umount /mnt/proc`
    d. Clear /sys binding - `umount /mnt/sys`
    e. Unmount new root - `umount /mnt`
    f. Unmount old root - `umount /media/rootbk`
    g. Unmount backup - `umount /media/backup`
13. Reboot - `sync`; `reboot`

After all of this (well really a more involved version of this as I did a full system backup and restore) I am back up and running and currently typing this up on the computer I ran the procedure on.  I suppose the one oddity that I saw both times I redid my root partition is on the first boot I saw the package manager warning about the language packs not being right on the first boot, but when I look, everything seems right.  Besides the initial warning message everything seems to be good and at least the first time around with switching over to EXT4 the warning message went away after a reboot (and standard updates).  Unless someone tells me otherwise, I figure as long as I don't see any actual error message and things are working, I should be good, right?  (Anyways if something does turn out to be off and at least the system fully boots, just re-install the package in question if deemed necessary.)

---

### Post by MAFoElffen on 2015-01-02
This is the logical basics of how I move a root drive (with a separate /boot partition) to a larger GPT disk (non-RAID):
Boot off a LiveCD.
Layout the new root disk partitions-- boot_bios, boot and root, filesystems to boot and root
Create a /mnt/boot
Create a /mnt/root
Mount the old /boot to /mnt/root
Temporarily mount the new /boot to /mnt/root
Use rsync or dump between the old and new /boot partitions to create the backup of.
Umount the old boot
Mount the root to /mnt/root
chroot into the system
Take the UUID from the filesytem on the new /boot (blkid) and update that to the /boot line in the fsatb
Install grub to the new root drive
Reboot with the new root drive (the old is still intact as a fallback)
Move the root to wherever...

---

