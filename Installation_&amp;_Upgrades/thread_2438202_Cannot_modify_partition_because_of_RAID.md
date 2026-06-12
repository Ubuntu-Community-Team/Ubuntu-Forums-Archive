---
title: "Cannot modify partition because of RAID"
date: 2020-03-07
forum: Installation &amp; Upgrades
---

### Post by Eric_Lee on 2020-03-07
I'm installing 18.04 on a new machine and need to modify the partitioning of devices on which I installed software RAID.  Per [Want to Remove Software RAID]("https://ubuntuforums.org/showthread.php?t=1646982") (closed as solved) I have done this:
mdadm --stop /dev/md0
mdadm --stop /dev/md1
mdadm --zero-superblock /dev/sda1
mdadm --zero-superblock /dev/sda2
mdadm --zero-superblock /dev/sdb1
mdadm --zero-superblock /dev/sdb2

[FONT=tahoma]The installer no longer shows the RAID arrays but still sees the partitions as being RAID and won't allow them to be changed:

[FONT=courier new]No modifications can be made to partition #1 of device SCSI (0,0,0) (sda) for the following reasons:
In use by software RAID device md0.[/FONT]

But /dev/md0 no longer exists.

How can I  get back to where I can re-partition?
[/FONT]

---

### Post by TheFu on 2020-03-07
Did you remove the RAID tag on the partitions?
Try
```
sudo dd if=/dev/zero of=$DEVICE bs=512 seek=$(( $(blockdev --getsz $DEVICE) - 1024 )) count=1024
```
where DEVICE is the partition, something like /dev/sda1

---

### Post by lvm on 2020-03-08
Eric_Lee, RAID device has to be stopped AND removed (--remove) prior to zeroing superblocks, otherwise it will come back.

TheFu, the command you mention does exactly the same as --zero-superblock.

---

### Post by Eric_Lee on 2020-03-08
[Elsewhere]("https://askubuntu.com/questions/1215502/cannot-modify-partition-because-of-raid") it was suggested to use [FONT=lucida console]sudo fdisk /sda[/FONT], then probably [FONT=lucida console]g[/FONT] for my environment.  But I couldn't because the shell, [FONT=lucida console]ash[/FONT], in the Installer doesn't have [FONT=lucida console]fdisk[/FONT]. I don't know if the same would have applied to [FONT=lucida console]dd[/FONT].
                     
                                                        Instead of Aborting the Install I  unintentionally rebooted. No disaster. I started the Install again and  when I got to the Partitioning it still had them marked [FONT=lucida console]raid[/FONT] [(image)]("https://drive.google.com/file/d/1ILuFCIc1R4J3hfKujB8i9J9b3o9120cI/view")  but there was no more [FONT=lucida console]No modifications allowed[/FONT] message when I tried to re-partition.  Following [these instructions]("https://askubuntu.com/questions/1066028/install-ubuntu-18-04-desktop-with-raid-1-and-lvm-on-machine-with-uefi-bios") the Install went smoothly.

Thank you TheFu and lvm.  I ended up getting there a different way.

---

### Post by TheFu on 2020-03-09
Please mark the thread as "SOLVED" using the _thread tools_ button.  Help out the community.

---

