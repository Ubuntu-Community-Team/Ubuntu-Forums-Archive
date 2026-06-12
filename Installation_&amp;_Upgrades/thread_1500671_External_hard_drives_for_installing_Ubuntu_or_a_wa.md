---
title: "External hard drives for installing Ubuntu or a way to circumvent the Windows 7"
date: 2010-06-03
forum: Installation &amp; Upgrades
---

### Post by elessar.telkontar on 2010-06-03
Months ago one of my computers died. I have bought a brand new one laptop, but I have a problem at the moment I wanted to install Ubuntu in dual boot with Windows 7: the new partition that windows 7 reserves for securing system files.

There are three partitions: Windows 7 principal, Windows 7 for securing system files (at the drive's beginning) and the recovery partition that HP puts there. Then I only have option to resize the Windows principal partition and get another principal partition. My question is if you know how to deal with this?

The other option you can help me is to advise me about some external hard drives to install ubuntu in them and don't touch the internal disk of my laptop.

---

### Post by darkod on 2010-06-03
You should resize (shrink) the win7 system partition using Disk Management in win7. That will create unallocated space, leave it as such. Reboot win7 few times to do its disk checks.
Boot with ubuntu cd and start the installer. When is asks where to install just select Use Largest Available Free space and that will install ubuntu inside he unallocated space you left.
I don't know how much unused space you have in the win7 system partition, but you should give ubuntu at least 35GB, even more if planning to keep large files in it.

---

### Post by elessar.telkontar on 2010-06-03
Thanks Darkod. However, Is sufficient only a paritition for installing ubuntu? where will be the swap? isn't no way to erase (with no side effects) the system files security partition of Win7 to get another paritition for swap?

And how about the external drives, can you recommend any external hard drive to install ubuntu?

---

### Post by darkod on 2010-06-03
The limitation of the hdd is 4 primary partitions, or 3 primary + 1 extended. Extended partition can have inside 16 logical partitions. That is how you can have more than 4 partitions on a hdd.

The ubuntu installer methods install ubuntu inside extended partition, creating logical partition root and logical partition swap. So, you would end up having:

Part1 - ntfs win7 boot partition
Part2 - ntfs win7 system partition
Part3 - extended, two logical inside
Part4 - restore partition

I haven't tried installing on usb hdd. I guess most of them should work fine, especially newer production. Also, some computers can't boot from usb but mostly newer can.

---

### Post by elessar.telkontar on 2010-06-04
Thanks for the help it is perfect!

---

### Post by darkod on 2010-06-04
You're welcome. I hope you enjoy it now. :)

---

### Post by brc816 on 2010-06-05
FWIW, I've got two different USB drives that I use as "sandboxes" for trying out various Linux distros, and can boot either one from my HP dv9000z laptop.

Trick is to make sure that you go into your BIOS and adjust your "boot options" to stipulate "CD/DVD" first, then "USB Disk", then "internal disk". That way, if you don't have a bootable CD or DVD in the drive, it will then try to boot off of an external USB drive if it's plugged in. And, if there's no external USB drive, then it will boot off of the first hard drive in the laptop. (Mine is a 17" model with two internal hard drives).

Basically, load a Linux (be it Ubuntu, Fedora, openSUSE or Mandriva; I've tried all of them) CD or DVD into laptop, and boot it. Follow the installation instructions BUT make VERY sure that you do NOT install GRUB/GRUB2 to the MBR, but instead to the boot block of your external USB drive (which will most likely be /dev/sdb, but make sure you are certain of that before you commit yourself!!). If you're installing with a Grub Legacy bootloader, you may need to twiddle with /boot/grub/menu.lst because when you boot off of an external USB drive, it is /dev/sda, and your first internal hard drive becomes /dev/sdb from the point of view of the grub code.

In fact, on one 250GB drive, I have GRUB (legacy, version 0.97) booting Fedora 13 or Fedora 12 or Ubuntu 9.10 or Mandriva 2010.
On a 1TB drive, I have GRUB2 (from Ubuntu 10.04) booting off of a GPT partition table into Ubuntu 10.04, openSUSE 11.3M7 or Mandrake 2010.1(Spring), each of which are on separate LVM partitions; I was unable to get Fedora 13's installer to let me install F13 onto another LVM partition.

If I unplug the USB drives, the MBR on my first drive gives me the GRUB legacy (0.97) boot menu that I installed when I installed openSUSE 10.3 a couple of years ago and subsequently upgraded to 11.0, 11.1 and 11.2. That menu permits me to boot either openSUSE or Windows XP or the Windows XP Rescue stuff that HP/Compaq plops on a 12GB partition on the first hard drive. I haven't tried Vista or Windows 7; I would urge you to read through all of the posts in this forum as it appears that there are a lot of Windows 7 users who have problems with GRUB2 for various reasons.

It all works fairly well EXCEPT that GRUB2 does NOT properly size disks when you have more than one internal drive. So, it claims that, when I boot off of my external 1TB drive, it can boot Windows XP, but in fact fails to enumerate the drives and can't/won't find all of the internal hard drives. I can replicate the problem with an installation I made on a 16GB flash ("thumb") drive as well. This is easily verified by booting using GRUB2, and stopping at the initial screen, then going to the command prompt and issuing the 'ls' command - you will see only two of the drives and their partitions, and those will be the USB drive and the SECOND hard drive. No, I don't know why, either.

BTW, despite the HP documentation, it didn't seem to faze their repair center that I'd done the GRUB (legacy) installation and installed openSUSE, and they repaired my laptop under warranty.
I made sure to tell them how to get at Windows XP if they really needed to, knowing how minimal their familiarity with Linux is.

---

