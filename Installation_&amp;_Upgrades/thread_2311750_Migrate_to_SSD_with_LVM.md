---
title: "Migrate to SSD with LVM"
date: 2016-01-29
forum: Installation &amp; Upgrades
---

### Post by Trebacz on 2016-01-29
My plan is to upgrade my ubuntu server from a 400 GB harddrive to an SSD.

The system currently looks like this:
[FONT=Fixedsys]```
sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL
NAME                                                      FSTYPE                  SIZE                     MOUNTPOINT                 LABEL                              
sda                                                                                          465.8G                            
&#9500;&#9472;sda1                                                   ext2                            243M                            
&#9500;&#9472;sda2                                                                                     1K                            
&#9492;&#9472;sda5                                                   LVM2_member       465.5G                            
  &#9500;&#9472;Rackable2013--vg-root (dm-0)        ext4                         449.5G                   /                          
  &#9492;&#9472;Rackable2013--vg-swap_1 (dm-1) swap                             16G                  [SWAP]                     
sdb                                                                                         2.7T                            
&#9492;&#9472;sdb1                                                  linux_raid_member       2.7T                 Rackable2013:0
  &#9492;&#9472;md0                                                 LVM2_member             2.7T                            
    &#9492;&#9472;volgrp-logical_1 (dm-2)                 ext4                               2.7T                 /home/david/mnt/Raid_Array 
sdc                                                                                               2.7T                            
&#9492;&#9472;sdc1                                                  linux_raid_member       2.7T                  Rackable2013:0
  &#9492;&#9472;md0                                                 LVM2_member             2.7T                            
    &#9492;&#9472;volgrp-logical_1 (dm-2)                 ext4                               2.7T                 /home/david/mnt/Raid_Array 
sdd                                                                                          232.9G                            
&#9500;&#9472;sdd1                                                  ext2                             250M                  /boot                      
&#9500;&#9472;sdd2                                                  ext4                           214.9G                 /mnt/ssd                               root
&#9492;&#9472;sdd3                                                  swap                           15.6G                                                              swap

```[/FONT]

sda is the current drive with boot, root and swap (root and swap are on an LVM). sdd is my SSD drive that is set up with three partitions. I have:

1. Used clonezilla to synchronize the boot partition
2. Used rsync to synchronize the root partition (avoiding the lvm)
3. Edited the fstab entries with the proper new UID's for (sdd2 and sdd3)
4. Did a grub-install on sdd

When I try and boot with the sda drive removed the boot process gets in an infinite loop not finding my md0 raid array (sdb and sdc). Am I going about this the right way? Is there something simpler?

---

### Post by oldfred on 2016-01-30
I do not know RAID nor LVM.
But with my standard data partitions or a swap that is missing in fstab when booting it just gives an error that I can bypass. Only if / (root) has issues then it does not work.

 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by MAFoElffen on 2016-01-31
I can help with LVM and RAID. But your RAID members are on /dev/sdb and /dev/sdc, so they are not a concern at the moment. That is because you said you just need to replace your LVM root drive.


Before you do anything, please post the resluts of 
```

sudo blkid
sudo fdisk -l
sudo pvdisplay
sudo pvscan
sudo lvs --all
sudo vgs --all
sudo pvs --all
cat /etc/mdadm/mdadm.conf
cat /proc/mdstat

```
That will document what you have and how it is laid out


I'm seeing /dev/sda as your original LVM root drive, and I am assuming that the /dev/sdd that I see in your output is the new drive, right? (Please confirm)


Take a break. Back up & Start over. There is seversl ways to go about this.
- Recreate partitions on your new drive. Mount new drive's boot partition in /mnt. dd copy the contents of the old bot to new. add the extent of the new LVM partition, Move the extent to the new drive. That out the old extent. Reboot offline from a LiveCD, chroot it and install grub to new drive. Mod the fstab. Reboot and try.
- Netx method is to mount the new drive live. Create the boot on the new drive from mkboot. Mirror the logical drive to the new drive from within LVM. Take out the old logical extent.
- Third way is to shrink the filesystem, lv,vg, pv ... and the partion of... to copy over the disk image to the smaller disk image). Replace the old with the new. Then extend the reverse order on the new.


I was taught with the first of those three, so i sort of lean back towards that recipe.

Post the things I asked for. Then think about which way you might feel more comfortable with. With your output and that decision, we can help you from there. There are many other methods, but those are the three I feel comfortable most about leading someone else through. Each of those, you still have the old drive to boot off of in a pinch.

---

