---
title: "erased boot partition for multiboot system during hardy install"
date: 2008-09-27
forum: Installation &amp; Upgrades
---

### Post by streamsanddragonflies on 2008-09-27
Hello,

I have a multiboot multi drive system and during this recent installation of open suse 11.0, followed by Ubuntu Studio hardy, I messed up close to the end! I had gotten parts of the solution answered in an earlier thread, but I want to be sure of all right steps before I make things worse.

I have /boot in 1st primary partition of first hd (IDE) set in bios, I have suse, suse/home, data, ntfs data, swap and gutsy in following logical partitions.
On sdb (1st SCSI) I have Windows XP and /home for hardy partitions.
On sdc (2cnd SCSI) I have hardy / and swap partitions.

I installed Suse's grub to /boot partition correctly and Suse as always, only boots itself succesfully.
Then I installed Hardy manually, but I erased the /boot partition!!!!! and I believe that I should have just used(as opposed to do not use choices in the ubuntu partitionner) it as /boot without erasing or formatting-is that correct? It was already flagged as bootable so all I had to do was to install grub to it in order to have ubuntu's grub as the master bootloader/bootlist (as I did with gutsy install).

Now I have no boot/active access to gutsy and suse, only windows. I had a backup of the /boot folder for gutsy and I already attempted to edit grub/menu.lst to include the gutsy entry but of course the initrd and vmlinuz files are still missing... ( I have made a copy of both hardy and gutsy /boot files now onto a USB drive and the data partition).

I plan on re-installing suse with the more stable kde desktop version anyways, but I want ubuntu's grub to remain "master".
So after the suse install, I should backup suses /boot files not erase /boot again! Re-install ubuntu grub via the live cd:   Can I do it graphically via gksudo nautilus,copying the hardy and gutsy boot backup files (that includes the kernel and initrd files minus the older grub folder used to load gutsy) into the appropriate /boot folders in each OS filesystem partition and making sure all the OS are entered correctly in the hardy grub/menu/lst? Or do I have to reinstall hardy as well and just add the gutsy boot files?
I am supposed to end up with only one grub folder, in the hardy filesystem, right, or should each OS have the same copy of the updated grub list?
These details are where I loose confidence and I already mucked up my hardy login now trying to solve this issue....
 
One more question, why does the ubuntu partitionner see my drives as: scsi 1 (0,0,0) sda,
       scsi 3 (0,0,0) sdb,
       scsi 3 (0,1,0) sdc
is there an error in how its seeing my drives and was this a problem?
(the varying notations with suse, grub, and ubuntu can be quite confusing).
I know there is a solution ...thanks in advance

---

### Post by zzzzz1 on 2008-09-27
I have a similar problem though it dosent involve new installation of the OS itself

here is my original thread [http://ubuntuforums.org/showthread.php?t=931861](http://ubuntuforums.org/showthread.php?t=931861) ( unfortunately i did not really get any help yet )

this is my current status:

[PHP]root@ubuntu:~# mkdir /mnt/root
root@ubuntu:~# mount -t reiserfs /dev/sdc4 /mnt/root
root@ubuntu:~# mount -t reiserfs /dev/sdc4 /mnt/root/boot
root@ubuntu:~# sudo grub-install --root-directory=/mnt/root /dev/sdc4
Due to a bug in xfs_freeze, the following command might produce a segmentation
fault when /mnt/root/boot/grub is not in an XFS filesystem. This error is harmless and
can be ignored.
xfs_freeze: specified file ["/mnt/root/boot/grub"] is not on an XFS filesystem
Installation finished. No error reported.
This is the contents of the device map /mnt/root/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda
(hd1)	/dev/sdb
(hd2)	/dev/sdc
[/PHP]

but i still get grub error 22 @ boot

---

