---
title: "GRUB2 not installing to external hard drive"
date: 2011-08-09
forum: Installation &amp; Upgrades
---

### Post by 1beerbaron on 2011-08-09
I tried doing a search and couldn't find anything relatively recent on the topic so here is my question.

I am fairly new to the linux world and am in the process of trying out a couple different distributions.  I am doing this by installing them to an external hard drive.  This allows me to test them out without affecting my main system in any way.  I have already tried openSUSE and it installed with no problems.  I am trying to install Ubuntu, however when the installation tries to install GRUB2 it fails asking me for a different location to install it to.

When installing I unhook all drives from the computer except for the dvd drive, usb drive I'm installing from, and the external hard drive I am trying to install Ubuntu to.  I'm not sure what else may be of use.

Thanks in advance.

---

### Post by zealibib slaughter on 2011-08-09
you need to specify your partitions manually (advanced mode). There you can specify where to install grub.

---

### Post by 1beerbaron on 2011-08-09
I did that and it still comes back with that error.

---

### Post by Basher101 on 2011-08-09
I got your solution, must make screens..

---

### Post by Basher101 on 2011-08-09
So, you start the installer and choose the something else.
Then you need to specify the Drive for the Bootloader like on screen 2.
Then you click on your hard drive /dev/sda at the bottom and select ***/dev/sdb*** for the bootloader (assuming ONLY your hard drive and USB drive are connected). That should install the bootloader to your usb drive.

---

### Post by 1beerbaron on 2011-08-09
That's what I'm doing.  I even unhooked my internal hard drive so that the only one attached is the external.  So there is only one hard drive for it to choose in the first place.

---

### Post by YesWeCan on 2011-08-10
You are trying all the right things. Work-around time.
Try installing grub to the root partition on the external drive, eg: sdc1
boot live cd
sudo mount /dev/sdc1
sudo grub-install --force --root-directory=/mnt /dev/sdc

then make the root partition active (bootable) in the MBR partition table
sudo sfdisk /dev/sdc -A1

then try booting the external drive
once booted into Ubuntu, try
sudo fdisk -l  to check the disk name, I'll assume it is still sdc
sudo grub-install /dev/sdc


See if that works.

---

### Post by Basher101 on 2011-08-10
must it not be /dev/sd***_b_*** ? Unless he has other drives it should be sdb.

---

### Post by YesWeCan on 2011-08-10
> **Basher101 said:**
> must it not be /dev/sd***_b_*** ? Unless he has other drives it should be sdb.
Yes, it could be. I dont have much confidence in what a particular bios will name an external disk. But you are probably right and I should have chosen sdb1 as a better example. Actually, as the OP only has the external connected it may well be sda.

sudo fdisk -l can be used to see the disk and partition numbers.

---

### Post by Basher101 on 2011-08-10
> **YesWeCan said:**
> Yes, it could be. I dont have much confidence in what a particular bios will name an external disk. But you are probably right and I should have chosen sdb1 as a better example. Actually, as the OP only has the external connected it may well be sda.

sudo fdisk -l can be used to see the disk and partition numbers.

exactly. I installed a backup live CD to a 4 gb usb stick and a whole installation on a 8 gb stick. I will mess around with my 8 gig stick at school tho >: )

---

