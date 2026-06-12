---
title: "cannot add a mountpoint to my partition table"
date: 2015-10-24
forum: MINT
---

### Post by thane1 on 2015-10-24
New instl'n of linux mint 17 (Rebecca) with a 3TB gpt hdd used for backups, which has four ext4 partitions.  Of the four the 1.7TiB second partition will not auto mount like the other 3 and I'd like it to do so.  On booting I get a I(gnore), S(kip) and M(anual recovery) prompt.  After pressing S and finishing the bootup a check of my partition table file with gparted shows all four partitions with the identical entries other than the partition names, mountpoint names and UUIDs, except that partition #2 doesn't show a mountpoint.  So far I've been unable to add it to the second entry.  I should mention that commenting out the /dev/sdd2 UUID line in my fstab file will then let the system boot up with no hesitation.

I can mount the partition manually.  I've checked the UUIDs for this partition in the /dev/disk/by-uuid folder and by using both parted and a Gparted-live disc.  All are identical.  I've taken ownership with read and write priviledges including files inside of all four folders, where these partitions are mounted to.  I've tried to fix the problem using sudo vim on my /etc/fstab file with no success.  Still no /mountlocationname showing up for the second partition, when I check with gparted after S(kipping) on bootup.  If I do a manual mount and then check in gparted the mountpoint does show up.  So there's nothing wrong with my gparted program.  All four partitions have the following attributes in my fstab file (/backuphome partition used here):

UUID=xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx /backuphome  ext4  defaults  0  2

I've also tried my gparted-live and knoppix dvds to gain access to add the mountpoint to the unmounted partition to no avail.  Is there a method I haven't thought of to do this?  I'm hoping not to have to delete partitions 2, 3 and 4 and redo them.  Many thanks.

---

### Post by SeijiSensei on 2015-10-25
A mount point is just a directory you create to attach a device to.  It's not created automatically by anything.

Do you mean that the mount point exists, but the device is not mounted to it?  Have you run
```
sudo fsck /dev/sdd2
```
since it stopped mounting at boot to make sure the filesystem has no errors?  Usually the error message you report means that Linux has detected errors in the partition.  If you hit Skip, it will remain unmounted until you do so manually. Mounting a partition with errors can lead to data loss.

---

### Post by howefield on 2015-10-25
Thread moved to the "*MINT*" forum.

---

### Post by thane1 on 2015-10-25
Thanks SeijiSensei,     I tried the fsck command route and found, that the swap seemed to be bad.  Deleted and remade the swap.  Rebooted and still got the i, s and m prompts.  Once back in I checked partitions with gparted again and found that for some reason my /home and /backup sdd2 partitions seemed to both be mounted and/or linked to /home for some reason.  Maybe that's somehow partly due to when I was preparing to redo the system I had copied my /home directory to the sdd2 partition via gparted-live.  I finally decided that since this was a brand new installation and I had all data backed up onto my 4 backup partitions, that I'd just do a clean total installation of Mint Rebecca without automounting the backup partitions on startup.  Once that was done I manually mounted them and copied all required data into the new installation.  All done.  Thank you so much for pointing me in the right direction.  I had never used the fsck command before.  Note to self.  cheers

---

