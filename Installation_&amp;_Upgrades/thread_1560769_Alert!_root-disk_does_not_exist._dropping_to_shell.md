---
title: "Alert! root-disk does not exist. dropping to shell. initramfs"
date: 2010-08-25
forum: Installation &amp; Upgrades
---

### Post by dekinstoke on 2010-08-25
[FONT="Arial"]Ok this is driving me mad:(. I have a Wubi install of Ubuntu 10.04 on an IDE hard drive(/dev/sdc1) on this machine.
When I go to boot it normally it goes to the above error message and can't find root-disk although it is defo there lol. If I use Recovery Mode I can usually get to a text based log-in and then run "startx" to get to the Desktop. Well "quelle surprise", root-disk must be there after all;)
Having done some reading up on this this, the most common cause seems to be that the Windows file system (NTFS) is marked as "dirty" .I have run chkdsk /r on the drive in Windows so many times ... and it seems ok.
I tried moving the ubuntu folder and wubi.mbr and the other config file onto another drive, deleting the partition and formatting /dev/sdc1 and then moving moving the Wubi stuff back thinking that anything "dirty" would now be washed snow white, but no :(...still the same problem.
There has to be an answer to this somewhere, but I am stumped. Any suggestions? [/FONT]

---

### Post by dekinstoke on 2010-08-25
[B][FONT="Arial"]Ok ...bit of an update. After wiping and reformatting the disk containing Wubi the error on start up has changed. i now get :
error: device does not exist (string of numbers)
error: cannot find C/H/S values

Then it boots normally (so far). Possibly by deleting the partition I have changed the volume ID? But the fact that it can't find the C/H/S values is a bit concerning. Possibly the hard drive has some serious errors? SMART doesn't show anything ...[/FONT][/B]

---

### Post by lechien73 on 2010-08-25
It may be nothing to worry about - there is a documented Grub bug regarding this.

Maybe if you could post the output of:

```
sudo fdisk -l
cat /etc/fstab

```
As well as the actual string of numbers produced by the error message, it might help to clear things up.

Thanks

---

### Post by dekinstoke on 2010-08-26
[FONT="Arial"][B]Ok ... still getting in to Ubuntu using recovery mode and startx (pain). Here's the outputs from the two scripts requested earlier:

output of fdisk -l (relevant to /dev/sdc1)

Disk /dev/sdc: 250.1 GB, 250059350016 bytes
255 heads, 63 sectors/track, 30401 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x000d1877

output of cat /etc/ftab

# /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/host/ubuntu/disks/root.disk /               ext4    loop,errors=remount-ro 0       1
/host/ubuntu/disks/swap.disk none            swap    loop,sw         0       0


[/B][/FONT]

---

