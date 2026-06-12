---
title: "To move Ubuntu from 1st to 3rd partition?"
date: 2010-10-25
forum: Installation &amp; Upgrades
---

### Post by DRNewcomb on 2010-10-25
I have Ubuntu installed on my 1st HD partition and working pretty much the way I like. I need to convert this to a dual-boot system with Windows. Windows really wants to be on the first partition on the first drive, so I think I need to move Ubuntu to the 3rd partition, behind the swap partition. 

I could do a complete reinstall but that would take forever. Is it reasonable to just copy the present /dev/sd0a partition to /dev/sd0c, install Windows, then run the Ubuntu CD to reinstall GRUB?

I guess I could just use dd for this but it's been so long that I've forgotten the correct method for moving a whole filesystem.

Can someone help me with the best way to solve the overall problem.

Thanks!

---

### Post by srs5694 on 2010-10-25
In my experience, Windows will install to something other than the first partition; it just needs to install to a *primary* partition. Thus, I'd suggest trying to install to /dev/sda3. (The partition identifiers you used aren't normal Linux partition identifiers.) If you have problems, you could try juggling partition IDs by typing "sudo fdisk -u /dev/sda", typing "p" to see the current partitions, deleting the current Linux partition, and re-creating it as something other than /dev/sda1. You can then create a new /dev/sda1 for Windows. Note that the "-u" option to fdisk is critical; that causes fdisk to switch its units from cylinders to sectors. You *must* recreate the Linux partition with sector-precise values for the new partition to be valid.

Recreating partitions like this is admittedly risky, so try it only if you're comfortable with that sort of thing. Copying the partition as you suggest should work, too, but will take longer. I believe that GParted includes a partition-copying feature that would work well for this sort of thing.

---

### Post by bcbc on 2010-10-25
I also think XP should be ok on the third partition. My xp is running on the second partition. (As long as you are using a primary partition). So you probably don't need to do anything (other than reinstall grub from a live CD after you are done).

But in any case, this is how you can do it...
1. format /dev/sda3 to ext4 (or ext3... whatever you are using)
2. mount /dev/sda3 on /mnt
3. copy files to new partition
```
sudo rsync -av  --exclude=/mnt/* --exclude=/home/*/.gvfs --exclude=/media/*/* --exclude=/tmp/* --exclude=/proc/* --exclude=/sys/* / /mnt
```
4. edit fstab and update the / mount to the new partition with uuid or to /dev/sda3
```
gksu gedit /mnt/etc/fstab
```
5. chroot to /mnt, update-initramfs -u, update grub, install grub
```
for i in dev proc sys dev/pts; do sudo mount --bind /$i /mnt/$i; done
sudo chroot /mnt
dpkg-divert --local --rename --add /sbin/initctl
ln -s /bin/true /sbin/initctl
update-initramfs -u
update-grub
grub-install /dev/sda
rm /sbin/initctl
dpkg-divert --local --rename --remove /sbin/initctl
exit
for i in dev/pts dev proc sys; do sudo umount /mnt/$i; done
```

Something like that. I have a script somewhere that does most of that and it hasn't failed me yet ;)

Caveat - I believe the above is correct, but use at own risk. Backup beforehand. (Standard disclaimer)

Update-initramfs may not be necessary - but usually I change the swap partition when I run it so I need to do this to support hibernation. It won't hurt to run it anyway.

---

### Post by Herman on 2010-10-25
Windows can be in any partition number and in any location on a hard disk, even a logical partition providing it has the boot flag. (At least that's the case in my computers). 
Grub can only set the boot flag in primary partitions, but GParted or any partition editor can set the boot flag in a logical partition.
That has been my experience anyway, and I spent some time experimenting and testing that, although there are always be many who will disagree.
Their computers are apparently different than mine, I wasn't aware I was purchasing special computers. I must be just lucky I guess. :)

---

### Post by DRNewcomb on 2010-10-25
> **srs5694 said:**
> (The partition identifiers you used aren't normal Linux partition identifiers.)

Sorry 'bout that. I did Unix/Linux sysadmin work until '96 when I got reassigned and have done only a little admin since then. Some things are a bit rusty.

The only available Windows license I have is an old Win2K Pro which is otherwise unused. It should be adequate for the purpose. I tried putting Windows on the second HD but that install has given me constant problems. (As I now understand it should.)

An additional hitch is that it seems that the primary hard drive is partitioned with a 2GB primary partion and a 202 GB extended partition. The extended partition has three subpartitions for ext3 (Ubuntu), swap and Fat32 (unused). 

I can't recall why I set the disk up that way when I installed Ubuntu. I assume I had some reason.
 
Based on the responses I've had so far, it seems that the best course of action may be to either just start over or back-up Ubuntu to the 2nd drive, install Windows to a primary partition on the 1st drive then recopy Ubuntu back to a partition on the 1st drive.

---

