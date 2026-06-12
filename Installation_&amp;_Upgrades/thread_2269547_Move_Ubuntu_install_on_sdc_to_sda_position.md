---
title: "Move Ubuntu install on sdc to sda position"
date: 2015-03-16
forum: Installation &amp; Upgrades
---

### Post by wjohnson55 on 2015-03-16
This is Ubuntu 14.04 on an old machine that serves as a media server.  When I started this, Ubuntu was (and still is) installed on sda1.  sda2 is used for media storage, as is sdb1.  I am running out of space on sda2 and want to repartition that disk so it is all available for storage, and also run Ubuntu from an ssd.  I acquired the ssd, hooked it up at sdc, copied the Unbuntu install to it, installed and updated grub.  So, now I have two identical Ubuntu installs, one at sda1 and one at sdc1, and both are in the grub menu.  I may not have done this as efficiently as possible, but this is where I am now.  I would like to move the ssd from the sdc position to the sda position, and put the old disk disk at sdc for repartitioning.  I need help with grub.  I'm thinking this:

Put the ssd at the sda position, and remove the old disk temporarily.
Boot from a live cd.
sudo grub-install /dev/sda
sudo grub-install recheck /dev/sda
sudo update grub

Will this work?  Am I missing anything?  Root directory issues? Do I have to mount sda1 and chroot to that mount point?  (BTW, I know I could just leave the ssd at sdc, but I would still have grub issues, as I would be repartitioning the current sda)


Once I have a bootable system, I'll put the old disk in and deal with that.

-- Bill Johnson

---

### Post by oldfred on 2015-03-16
With my old desktop, sda was XP and I booted from sdb back in 2006. Then I added a new larger drive and booted from sdc. Then I added a SSD and booted from sdd, so boot drive is not critical, you just set it in BIOS.

I found with my system drive order is set by the BIOS and port order connected on the motherboard. And I skipped one port, so if I reboot with a flash drive plugged in, it becomes sdb and all the other drives change. System still works but then I am booting from sdf and have to be careful with commands. 

If you copied install, did you change UUIDs as well as reinstall grub? And did you change the default drive that grub reinstalls into? Often better just to reinstall & copy /home over so all internal settings are correct.

       #To see what drive grub2 uses see this line   - grub-pc/install_devices:
sudo debconf-show grub-pc # for BIOS with grub-pc 
It will show drive model & serial number
to see drive info
sudo lshw -C Disk -short 

    sudo grub-probe -t device /boot/grub

   #to get grub2 to remember where to reinstall on updates:
sudo dpkg-reconfigure grub-pc or dpkg-reconfigure grub-efi-amd64
#Enter thru first pages,spacebar to choose/unchoose drive, enter to accept, do not choose partitions
[http://ubuntuforums.org/showthread.php?t=2189643](http://ubuntuforums.org/showthread.php?t=2189643)

With multiple drives I like to run Boot-Repair's Summary report just to know what is where. It shows lots of details that are difficult to otherwise find.

 Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
Precise, Trusty, Vivid, & Utopic all should work now with current ppa
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by wjohnson55 on 2015-03-16
Hello Fred.  Like I said, this is an old machine.  Drive order is determined by which SATA port the disk is plugged into.  SATA 0 = sda, SATA1=sr0, SATA4=sdb, SATA5=sdc (there is no SATA3 or 4).  The BIOS does give me control of boot order.  I want my root device at sda1 because that's where I expect it to be unless forced to think about it.


Your questions:
I did not do anything about UUID's or defaults.
Both installations are in the grub menu.  It defaults to the "old" installation on sda1.

If I boot into the sda1 installation, with sda1 mount at /, then
debconf-show grub-pc
  yields  
  pc-install-devices: /dev/disk/by-id/ata-(WD 500G at sda)
grub-probe -t device /boot/grub
  yields
  /dev/sda1

If I boot into the sdc1 installation, with sdc1 mount at /, then
deb-conf-show grub-pc
  yields
  pc-install-devices: /dev/disk/by-id/ata-(Crucial SSD at sdc)
grub-probe -t device /boot/grub
yields
/dev/sdc1

I've installed boot-repair and generated a summary report.  It's here:
[http://post.ubuntu.com/10611316/](http://post.ubuntu.com/10611316/)


Where do I go from here?

-- Bill Johnson

---

### Post by wjohnson55 on 2015-03-16
Update.  After looking at the output of the commands Fred suggested, and the boot-repair report, I thought it looked like I might not have to do anything.  Maybe I could just disconnect the old SATA0/sda disk, move the new disk from SATA5/sdc to SATA0/sda, and the thing would boot.  I tried, and it did!  /etc/fstab calls for mounting sdc1 at /, but I guess that just quietly failed because sda1 was already mounted at / and sdc is now non-existent (unplugged).  I've got some cleanup (fstab, update-grub) and some testing to do, but I expect to be able to mark this thread solved.

-- Bill Johnson

---

### Post by oldfred on 2015-03-16
That was exactly what I was going to suggest: :)

There are no duplicate UUIDs and grub reinstall looks like it would reinstall to correct drive on major update. So each drive's install looks like it should work without any other, which is what I normally suggest.

---

