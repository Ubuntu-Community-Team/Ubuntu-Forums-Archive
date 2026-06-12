---
title: "Can't install grub2"
date: 2012-05-25
forum: Installation &amp; Upgrades
---

### Post by eekie on 2012-05-25
I recently bought an Asus sabertooth 990fx mobo and amd bullozer 8150 processor. With 2x2 ocz SSD's and 1x2 HDD's striping and two sata  optical drives I have used all the internal sata connectors. I have one e-sata 2 TB external disk for back-up.
As an IDE port is missing and the external disk is quite slow  it is obvious I want to use the fake raid disks for installing the o.s.'s. On my previous mobo (msi 790fx-gd70) it has never been a problem to install grub2 on the raid arrays, but with the present configuration it is impossible to install grub2 be it ubuntu, fedora or kororaa. I will confine myself to ubuntu 12.04/12.10 d.b. x64.  
The 12.04 live usb (made with unetbootin) does not install at all (internal errors) The alternate cd gets jammed on grub2 installation just like the live usb of 12.10 d.b.. When I enter the bootloader location during installation f.i. : /dev/mapper/pdc_bagbffcdig and it reaches the stage of creating the bootloader it says: can't install in /dev/sda. This is understandable because I don't have sda (the external disk is named sdg). If I then re-enter the fake raid disk it keeps saying fatal error and lets my choose between quitting and installing without bootloader. Manual installation of grub2 using the live usb is no success either.
I have not found a manual yet focussed on installing grub2 on striping arrays.
Has anybody got an idea how to solve this problem?

---

### Post by zSeries on 2012-05-25
Have you booted from a Live CD to install grub

Mount the partion of the drive you want to boot
sudo mount /dev/sdXY /mnt

Install in MBR and create /boot folder
sudo grub-install --root-directory=/mnt /dev/sdX

Create the grub.cfg file on the bootable partition 
sudo update-grub

---

### Post by zSeries on 2012-05-25
I forgot to mention you can also try removing software "dmraid" using Syaptic after booting from the live cd and before installing grub.

---

### Post by darkod on 2012-05-25
> **zSeries said:**
> I forgot to mention you can also try removing software "dmraid" using Syaptic after booting from the live cd and before installing grub.

And why would he want to remove dmraid since he wants to run fakeraid? That would made the array invisible to ubuntu.

When you tried to install grub2 to /dev/mapper/blah_blah did you make sure you entered the array device correctly and without any partition numbers? Because it should be on the MBR of the device, not on any partition.

If you told it to install on /dev/mapper/.... the message it can't install on /dev/sda doesn't make much sense.

When you say the manual installation using live mode didn't work, did you try the full chroot procedure or only mounting the root partition and trying to install grub2 to the MBR of the array?

---

### Post by eekie on 2012-05-27
The grub2 install instruction in howtoubuntu.org worked well for manual install although it only finds the ubuntu entry (cannot find list of partitions (Try mounting /sys.)). Once the installed ubuntu started this is easely fixed with the update-grub command.
I have figured out by testing a couple of daily build 12.10 and the standard 12.04 live and alternate the occurrence of the grub2 installation problem . All live cd's and usb's showed the problem of insisting on the sda or sdb location. The alternate cd's/usb's of 12.10 were not fuzzy with regard to the fake raid MBR.
Ubuntu 12.10 presented a new problem relating to the software forum. The software center crashes immediately after starting, so I fell back on 12.04 with manual install of grub2.

---

