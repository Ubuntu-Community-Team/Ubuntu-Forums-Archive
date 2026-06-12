---
title: "Ubuntu, GRUB, etc"
date: 2007-09-28
forum: Installation &amp; Upgrades
---

### Post by simonalexander2005 on 2007-09-28
Hi,

I have currently got Ubuntu and windows dual booting on 1x160GB hard drive.

I have now purchased a second, 500GB drive, and would like to change my install as follows:

Drive 1 - 160Gb - Ubuntu Linux

Drive 2 - 300GB Windows XP Pro, 100GB Windows Vista, 100GB Solaris. (or something like that...)

The easy way to do this would be to run GParted, and extend the linux partition, deleting my current windows installation, then boot the other OS's onto the second hard disk.

but what would be the best way to set up the bootloader, bearing in mind that firstly, GRUB is already installled, and secondly I am dooing this over two disks?

Ideally, I would like GRUB to run on boot, and give me the option of all 4 OS's.

ta

---

### Post by Pumalite on 2007-09-28
To have an installation without problems is best to install Vista  first in sda1 (first hard drive, first partition), then install the rest. Also use the Vista's partitioner.

---

### Post by logos34 on 2007-09-28
I believe it would be easier to install XP first, leaving space for vista, otherwise you'll have to restore the vista boot manager (XP's NTLDR can't boot vista). 

[http://apcmag.com/5023/dual_booting_xp_with_vista](http://apcmag.com/5023/dual_booting_xp_with_vista)

Then install Solaris, but put grub on the bootsector of the linux root partition, not the MBR.  

To the bottom of ubuntu /boot/grub/menu.lst add a Solaris entry (pointing to that partition) and [a windows entry with mapping]("http://users.bigpond.net.au/hermanzone/p15.htm#Windows_on_a_non-first_hard_disk") pointing to the first partition on the other hard disk. 
 
Selecting Solaris from the grub menu will boot it directly; selecting windows will pull up the vista boot manager, giving a choice of vista or XP. 

To /boot/grub/device.map add a line for second drive:
[B]
(hd1) /dev/<drive>[/B]

Add [solaris]("http://www.psychocats.net/ubuntu/mountlinux") and [windows]("http://www.psychocats.net/ubuntu/mountwindows") to ubuntu fstab.

You can even use [EasyBCD]("http://neosmart.net/wiki/display/EBCD/Linux") to add linux to vista boot manager.

---

### Post by simonalexander2005 on 2007-10-01
right...

> Then install Solaris, but put grub on the bootsector of the linux root partition, not the MBR. 

I have Linux on my smaller hard disk, and XP Pro on my larger, in the first partition. it is currently booting through GRUB on the linux partition... was i supposed to put the linux /boot as a separate partition then?

---

### Post by logos34 on 2007-10-01
no, you don't need a separate /boot.  The reason for putting solaris grub on the bootsector vs. mbr of the larger disk is explained in the dual-boot and easybcd links I gave you.  It will enable you to boot solaris via vista boot manager (if you add it with easybcd).  Think of it as insurance: you have 4 OS's on two disks, so if grub on the smaller drive should fail at some point, you will still have a way to boot your other linux and windows on the second disk.

---

