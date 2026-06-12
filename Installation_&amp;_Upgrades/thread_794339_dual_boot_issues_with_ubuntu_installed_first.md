---
title: "dual boot issues with ubuntu installed first"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by BigFatPapa on 2008-05-14
A little background first. I have a full boot on Unbuntu, this was done by my granddaughter without my knowledge or assistance. I could not get Vista back no partitioning was done prior to the Ubuntu install. I had to get the recover/install disks from the manufacturer of my laptop. In the mean time I have grown quite fond of Ubuntu, but need the dual boot with Windows on the laptop for both work and school. I tried booting the Vista recover disks and received an error that there was no partition. So I googled and found this site

[http://apcmag.com/how_to_dualboot_vi..._installed.htm](http://apcmag.com/how_to_dualboot_vi..._installed.htm)

Perfect! I followed the directions, created a partition for the windows and when I went to install Vista, I got the same error message that there is no partition. I went as far as trying to name the partition as described after the Vista install, I got and error message that there is no folder/file for this.
I am beginning to think that this for a fresh out of the box version of Vista.

Can anyone help?

Thanks, Tom

---

### Post by dstew on 2008-05-14
In Ubuntu, open a terminal window (Applications --> Accessories --> Terminal) and enter the command```
sudo fdisk -l
```Post the result to the forum.

---

### Post by BigFatPapa on 2008-05-15
This is what is shows.  



Disk /dev/sda: 160.0 GB, 160041885696 bytes
255 heads, 63 sectors/track, 19457 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x61c6b961

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       10226       18796    68846557+  83  Linux
/dev/sda2           18797       19457     5309482+   5  Extended
/dev/sda5           18797       19457     5309451   82  Linux swap / Solaris

---

### Post by dstew on 2008-05-15
You probably need to create a partition for Vista to install to. You currently have unallocated space at the front of the drive, but no partition.

I am not sure if Vista will be happy with a partition created by a Linux tool, but try it anyway. You can create a partition using the Gnome Partition Editor from an Ubuntu Live CD boot, or maybe even from your current Ubuntu system. You can also use a [GParted Live CD]("http://gparted.sourceforge.net/livecd.php").

Create a new partition out of the unallocated space at the start of the drive. I seem to recall that Vista wants to see at least 1 Mb cushions of unallocated space before and after its partition. I think it would be best not to format the new partition. Just create an unformatted partition, then quit the partitioner and try to install Vista. If you have to format the partition, format it as NTFS or VFAT.

After you create the new partition, Ubuntu will probably not be able to boot. Certainly if you are successful in installing Vista, Ubuntu will not boot. You will have to re-install the grub boot loader to get a dual-boot system working.

---

