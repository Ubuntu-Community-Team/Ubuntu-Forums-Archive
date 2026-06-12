---
title: "Problem with install to usb drive"
date: 2012-03-02
forum: Installation &amp; Upgrades
---

### Post by kevin34ct on 2012-03-02
Ok so I am a newbie to Linux.  I have tried it out before but didn't like it much until recently with the new distro's.  SO here is my dilemma, I installed Ubuntu 11.10 on my usb drive but made a mistake and installed GRUB to a hard drive on my system.  The Drive is Disk 0, but it is not my boot drive for windows.  Disk 0 is an old XP drive that still was bootable if I wanted it.  (My BIOS has a Boot Menu in which I can boot from any device after POST) The problem is it won't boot my USB drive and I am trying to repair the MBR on that drive.  Also I need to get GRUB to install on the USB drive.  I plan on making this a portable system that I can move around from computer to computer.  I found out after the install that I was supposed to hit the Advanced button to tell it to install GRUB to the USB drive.  The only thing I can think of doing at the moment is to disconnect all my HDD's and boot the CD and install on the USB drive.  (My system does boot up into Windows without a problem since Windows is on Disk 2 and that is set as the Master Boot Drive) 

Sorry for the long winded question, but I've been searching all day for an answer to my problem and I don't know much about Linux.

---

### Post by darkod on 2012-03-02
There is no need to reinstall.

If you have two internal disks, I guess the external will be /dev/sdc. It might be another letter. If you are not sure, you can check with:
sudo fdisk -l (small L)

That will list all disks and partitions. Check if /dev/sdc is the external.

With all disks connected, boot your ubuntu that is on the external. Then, if the external device is /dev/sdc (use the correct one if it isn't) you can install grub2 on its MBR with:
sudo grub-install /dev/sdc

After that you should be able to get the same grub2 boot menu when booting from the external disk. Check if that works.

If it does, you can restore a windows MBR on the internal disk where grub2 ended up.

---

### Post by kevin34ct on 2012-03-04
ok, I have 3 internal drives but I can only boot into windows at this time so I can't get into Linux.  Do you mean boot from the Live CD and use those commands?

---

### Post by darkod on 2012-03-04
You can do it from live mode, but then the command needs slight modification because it needs to know what is your root partition.

If you have three internal, that makes your external fourth, lets call it /dev/sdd. And lets assume the ubuntu root partition is /dev/sdd1.

You can check this with:
sudo fdisk -l (small L)

If the above assumption is not correct, just use the correct values in these commands:

sudo mount /dev/sdd1 /mnt
sudo grub-install --root-directory=/mnt /dev/sdd

That sgould install grub2 to the MBR of /dev/sdd using the partition #1 (/dev/sdd1) as root partition. Note that there is no number 1 in the second command, just /dev/sdd.

After that you should be able to boot grub2 from the external disk.

---

