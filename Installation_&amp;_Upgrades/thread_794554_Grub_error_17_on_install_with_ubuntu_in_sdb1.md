---
title: "Grub error 17 on install with ubuntu in sdb1"
date: 2008-05-14
forum: Installation &amp; Upgrades
---

### Post by sqbadyvr on 2008-05-14
After running Fedora for a few years, I decided to switch to Ubuntu,  I run an amd64 with 3 SATA drives and nvidia graphics.

I have tried installing from both the Live and alternative CD.  I can run from the live CD and see that the files appear to be installed correctly, but when I try to reboot, I get a grub error 17.  

Reading through the forums, some people have been able to fix by modifying BIOS setting, but my setting matched their suggested settings (and I booted Grub into Fedora previously with no issues).  

Can anyone direct me how to install grub such that it will properly boot my system.  Configuration of disks shown below.

Thanks in advance for your help.

/dev/sda has 2 partitions-->
sda1 -->  swap  1.5 GB
sdb2 -->  first disk of a RAID 5 array

/dev/sdb has 5 partitions
sdb1 -->  linux root directory (25GB)
sdb2 -->  linux boot directory (150MB)
sdb3 -->  swap 1.5 GB
sdb5 -->  LVM (200 GB or so) for backup/storage
sdb6 -->  2nd disk of the RAID 5 array

/dev/sdc has 2 partitions
sdc1 --> swap 1.5 GB
sdc2 --> 3rd disk of RAID 5 array

---

### Post by VMC on 2008-05-14
I don't have raid. Don't know anything about them, but which is your active partition?
If you boot using livecd and from terminal type sudo fdisk -l, under boot there should be a * indicating which partition is active.

---

### Post by sqbadyvr on 2008-05-14
2 partitions have a * in the boot column--1 is the swap file for sda and the other is my root partition.

---

### Post by VMC on 2008-05-14
> **sqbadyvr said:**
> 2 partitions have a * in the boot column--1 is the swap file for sda and the other is my root partition.
Get rid of the swap boot. That's whats causing your problem. Swap should never have boot enabled.

---

### Post by psusi on 2008-05-15
The active partition has absolutely no meaning... it's a red herring.

Which of the 3 disks is your bios configured to boot from, and what does your /boot/grub/menu.lst look like?

Since your /boot is on sdb, I assume that your bios is also configured to boot from that drive.  If that is the case, you will need to edit /boot/grub/device.map and make sure (hd0) points to /dev/sdb, NOT sda, then reinstall grub:

sudo grub
root (hd0,1)
setup (hd0)

If your bios boots from sda, then leave devce.map alone, and do this:

sudo grub
root (hd1,1)
setup (hd0)

And make sure /boot/grub/menu.lst uses (hd1,1) for the root, not hd0.

---

### Post by meierfra. on 2008-05-15
> you will need to edit /boot/grub/device.map and make sure (hd0) points to /dev/sdb, NOT sda, then reinstall grub:

sudo grub
root (hd0,1)
setup (hd0)

You have to use "sudo grub --device-map=/boot/grub/device.map"
otherwise grub will not use "device.map", but creates its own.

You also need to make sure menu.lst use "root (hd0,1)"

---

