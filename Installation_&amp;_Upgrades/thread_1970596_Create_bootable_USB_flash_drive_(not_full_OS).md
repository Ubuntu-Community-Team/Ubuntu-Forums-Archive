---
title: "Create bootable USB flash drive (not full OS)"
date: 2012-05-01
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2012-05-01
I'm having trouble creating a bootable USB flash drive.  I don't want to change the MBR or the boot process on the hard drive which is mostly Windows, but I want to be able to access the Ubuntu partitions by just booting from USB.

I managed to set up a larger flash drive, but I'd like to use one of my older drives - 125M.  But I think I've messed up formatting and partitioning.

Is there a HowTo for this?  All I can find is instructions to set up the entire OS on a flash drive, or to use the USB for booting on a reinstall.  That's the way I set up the larger drive, but it didn't work on the smaller one - I think because it wasn't formatted correctly in the first place.

I'd also like to be able to do this without reinstalling the OS.  That must be possible too.

Thanks!

---

### Post by darkod on 2012-05-01
I don't understand what do you want to do. You basically stated all possible options and said you don't want any of them.

You can either prepare a usb stick as a bootable install media, which can also run in live mode.
Or you can install onto a disk, usb or sata.

That's it. So what is it that you actually want?

---

### Post by 5circles on 2012-05-01
@darkod - sorry if I'm not being clear.

I want to create a bootable USB drive that _doesn'_t include the OS. 

Although I managed to do this once, I have not been able to repeat it with a different (smaller but still enough space) USB drive.  And I'd like to do it from a running system rather than reinstall.

I don't know if the drive is formatted correctly, and if so how can I format properly.

---

### Post by darkod on 2012-05-01
So, we are talking about a bootable usb that you can run in live mode (Try Ubuntu) or install with it on any computer?

---

### Post by 5circles on 2012-05-01
> **darkod said:**
> So, we are talking about a bootable usb that you can run in live mode (Try Ubuntu) or install with it on any computer?

No, that's not it:

Bootable - yes
Live mode - no
Install to another computer - no

I have Ubuntu installed, but don't want to mess with any of the other partitions or the MBR.  [Maybe later, but not until I get through with Dell support to figure out if there is a hardware issue.]

---

### Post by darkod on 2012-05-01
So you only want to put the grub2 bootloader on another disk, sata or usb doesn't matter? And that grub2 will need to boot existing ubuntu?

You now have ubuntu installation without grub2?

---

### Post by 5circles on 2012-05-01
> **darkod said:**
> So you only want to put the grub2 bootloader on another disk, sata or usb doesn't matter? And that grub2 will need to boot existing ubuntu?

USB.  I want to plug in the USB, reboot, and have the default boot order take care of boot up through the USB, then the main partition.

> **darkod said:**
> You now have ubuntu installation without grub2?

The USB has the /boot partition, with /boot/grub as well

---

### Post by darkod on 2012-05-01
OK. Plug in all the disks you want to use, boot ubuntu into live mode and in terminal post the results of:
sudo fdisk -l (small L)

Below them, explain which is the root partition of your ubuntu installation, which is the /boot partition, and on which disk you want the bootloader.

Also, when you say you already have /boot on the usb, is it the same /boot from your installation or something that was created during one of your attempts. Because if that's not the /boot partition of your ubuntu installation, it's irrelevant. It can't be used as a /boot partition.

PS. Also tell us which version of ubuntu you have installed.

---

### Post by oldfred on 2012-05-01
I use grub2 installed to a flash drive to boot ISOs loopmounted. That is just grub2 installed to flash, and I have to manually create a grub.cfg as the rest of grub that auto creates grub.cfg is missing. I usually add a boot stanza or two to also boot one or more of my installs on the hard drives just as  a backup. I have installed grub2 to FAT32, Ext4 (without journal) and NTFS, it works on all formats.

[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB_USB)
Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM](http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM)

---

### Post by 5circles on 2012-05-01
I'm running Ubuntu 12.04. Main hard drive:
```
Disk /dev/sda: 500.1 GB, 500107862016 bytes
255 heads, 63 sectors/track, 60801 cylinders, total 976773168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xcee47556

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63       80324       40131   de  Dell Utility
/dev/sda2   *       81920    79736831    39827456    7  HPFS/NTFS/exFAT
/dev/sda3        79736832   935811119   428037144    7  HPFS/NTFS/exFAT
/dev/sda4       935813118   976771071    20478977    5  Extended
/dev/sda5       935813120   955342847     9764864   83  Linux
/dev/sda6       955344896   976771071    10713088   82  Linux swap / Solaris
```
/dev/sda5 is the main Ubuntu partition.

USB flash drive that is booted from
```
Disk /dev/sdb: 1006 MB, 1006632960 bytes
31 heads, 62 sectors/track, 1022 cylinders, total 1966080 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xc3072e18

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *       16065      208844       96390    6  FAT16
/dev/sdb2          208845      413695      102425+  83  Linux
```

/dev/sdb2 is /boot, with /boot/grub.
```

The USB Flash drive I want to have as the boot source:
Disk /dev/sdc: 131 MB, 131072000 bytes
5 heads, 50 sectors/track, 1024 cylinders, total 256000 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000c6f91

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1            2048       20479        9216    1  FAT12
/dev/sdc2           22526      253951      115713    5  Extended
/dev/sdc5           22528      253951      115712   83  Linux
```


I think I have totally messed up this second, smaller, drive.  I don't need anything on it.

Does that help?

---

### Post by darkod on 2012-05-01
OK. Lets try first without involving sdb2 since I am not sure it's the /boot partition for sda5 or just separate.

Boot the 12.04 cd in live mode and try:
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sdc

That will install grub2 to the MBR of /dev/sdc telling it that its root partition is /dev/sda5.

That's what you want, right?

Try booting from /dev/sdc. Does it work?

---

### Post by 5circles on 2012-05-01
Some progress, but not quite there.

```
Error: File not found.
Grub rescue>
```

It took a lot to even get the USB to boot.  Low level format with dd, another format, new partitions.

---

### Post by 5circles on 2012-05-01
Tried again, and this time got to the Grub> prompt.

---

### Post by oldfred on 2012-05-01
If you install grub from install, it should work. 

Post paste-bin link from Boot-Info

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by 5circles on 2012-05-02
@oldfred - I did create the first (working) USB flash from the install.  I'm trying to create a second boot on a smaller drive.  It might make sense to try again now that I have a drive almost working - and before it will be too difficult to install 12.04 again from scratch.

I'll look at this, and the utility, tomorrow.

Thanks

---

### Post by darkod on 2012-05-02
The above commands were assuming sdb2 is not your /boot partition. Because to me it is still unclear. But if it really is, you will need to modify them like this:
```
sudo mount /dev/sda5 /mnt
sudo mount /dev/sdb2 /mnt/boot
sudo grub-install --boot-directory=/mnt/boot /dev/sdc
```See if that helps. The grub rescue might be because of missing files and if sdb2 is your /boot then the files would really be missing by not mounting it too.

Also if sdb2 is your /boot, don't forget that you can't remove /dev/sdb from the system or delete the sdb2 partition. You always need to keep it.

---

### Post by 5circles on 2012-05-02
Now I got a different message:

```
error: no such device: 34bd0522- etc.
grub-rescue>

```

The device code is the automatically generated ID for the USB flash that I'm trying to write.

---

### Post by 5circles on 2012-05-02
I'm admitting defeat, or moving to a smarter approach depending on your point of view.

I reinstalled 12.04, using the same approach as on the larger drive, but now on a smaller drive that had been able to boot even if I couldn't complete the boot sequence correctly.  This was with /boot on the flash drive.  It worked fine.

Then I installed one more time, but now just with the boot on this drive.  /boot is on the main partition.  It worked fine too.

I also tried again with the other drive of the same size that I'd tried previously.  I tried dd to make a complete copy, reformatting in various configurations.  But although I can use it for storage, I can't get it to boot.  I'm concluding that this is an old / incompatible drive.

Thanks for all the help and suggestions.

---

### Post by darkod on 2012-05-02
Do you know for sure you can boot with this usb flash? Sometimes the computer doesn't detect it fast enough to find it for boot. That would explain why it would report the UUID not found.

From live mode you can check all UUIDs with:
sudo blkid

If the UUID is correct, something is stopping it being detected on time.

---

### Post by 5circles on 2012-05-02
It's probably moot, but I checked the drives on a different system.

The drive that won't boot:
```
/dev/sdg1: SEC_TYPE="msdos" UUID="35D7-E408" TYPE="vfat" 
/dev/sdg2: UUID="313fd71d-b328-43ab-8f85-2fb197653ab6" TYPE="ext2" 

```
 
I see the same exactly from the drive that is working.  That's probably because of the earlier dd to copy.

It looks like your latest message overlapped my wrap up.  We should just close the thread, as I'm done.  Your and @oldfred's help is great - I don't know if there is much for others to learn from apart from old USB flash drives can be bad.

Mike

---

