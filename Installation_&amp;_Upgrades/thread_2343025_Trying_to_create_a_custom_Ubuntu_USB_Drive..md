---
title: "Trying to create a custom Ubuntu USB Drive."
date: 2016-11-12
forum: Installation &amp; Upgrades
---

### Post by vas2 on 2016-11-12
Pretty sure this falls under Installation, so I hope I chose the right board to post this in.

I've been trying to set up a flash drive I can use to repair Windows any time I need and do other certain tasks when I need.  My old USB 2.0 drive causes Windows Explorer to crash now if I try to load it, so I'm not sure if ext2fsd is broken or the drive is broken.  I now have a 128GB USB 3.0 flash drive that I want to install Ubuntu onto, and I prefer LiveCD mode because it allows me to stick it into any computer and boot without having to worry about system configurations/hardware/whatever.  I know it'll always boot because it'll load whatever it needs to in order to run.  On top of that, I like LiveCD mode because I may accidentally damage Ubuntu/Linux because I don't know how to use it and frequently try to customize it and do things that may otherwise damage the OS, and in the case that I do that, all I have to do is format the persistence partition and boom, its like new again.  A 3rd reason I like LiveCD, is it comes with all the software I want it to have, such as gparted and anything else I might need to perform repairs on pretty much any system I plug into, all right off the bat.  When I used install once from a LiveCD version and installed to a flash drive, it came blank, empty, devoid of anything useful whatsoever.  So I'm not sure if I want to install, or use LiveCD mode again.

An issue I'm facing right now thats preventing me from doing what I did before to make my USB, is the fact that I want to stick Ubuntu, at the end of the flash drive.  Windows, being as crappy as it is and will always be (but still the only one I can truly game on comfortably and not google "how to" every 10 minutes) can only see the first partition of a flash drive.  So I want the first 32GB of my flash drive, to be NTFS so I can transfer things back and forth between Ubuntu with great ease.  The middle partition, will be the persistence while the end of the disk will have as little free space as possible, being absolutely nothing but Ubuntu.  Thats the goal anyway.

This also needs to be UEFI compatible, as my current Ubuntu whatever it was, isn't and my laptop refuses to accept the flash drive at all when booting even though the flash drive is fine and functional.  Just very very very slow.  God, using Ubuntu on it was like waiting for something online to load on dialup.  I'm not sure whats going to happen with my system soon, as it appears in cloning my 1TB HDD over to the 500GB SSD with some dirty tricks and hacks I had to do, may have damaged my file system so I'll have to format my SSD and start over from complete scratch.  New UEFI partition, new partition tables and whatnot, all that jazz.  UEFI still seems to be able to block the original flash drive from loading however, even with no hard disks in my laptop.

So, are there any ideas for what I can do?  I prefer things that have a UI, because I can't remember command line things all that well and hate having to look them up constantly to do them.  Thats why I use Windows, requires no command line almost anywhere while Linux based systems appear to still be heavily command line.

---

### Post by oldfred on 2016-11-12
I have been using Ubuntu for ten years. And I had to start my notes as I could not remember command line tasks. 
But now I have one (word not allowed by forum) Windows 10 system just to watch DVR from Comcast. And help on Internet for Windows 10 issues is everywhere but a lot does not match the screens I see. And they rarely post terminal commands to fix things.

I did have XP and created one repair flash drive with the Windows 7 repair ISO installed and several Linux repair ISO booted with grub's loopmount all on one flash drive.

But now flash drives are cheaper and larger. So I typically have the Windows repair/recovery flash drive and many Ubuntu repair install flash drives.
I still have some older BIOS flash drives, but all newer ones are configured for UEFI boot. Most are full installs of Ubuntu and ISO for boot of other repair systems like gparted, knoppix, parted rescue, Boot-Repair, Supergrub etc.

I do not recommend using Windows to read Linux partitions. But have had no issues using NTFS for both Windows & Ubuntu when I needed the compatibility.

If you need UEFI, first partition should be FAT32 as the ESP - efi system partition. Not sure if then newer Windows will read additional NTFS partitions or not on flash drive. FAT32 should not be used for large partitions, but you can make it larger and store some data on it also if a flash drive.

So I typically have one Windows repair/recovery flash drive for UEFI, one Ubuntu live installer for current LTS version and several larger flash drives with full installs of Ubuntu both LTS and current version and grub boot of various ISOs.

You may be able to have both UEFI or BIOS boot on one drive, but updates can get out of sync and cause issues.
       Another new, simpler and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode 16.04
[http://ubuntuforums.org/showthread.php?t=2213631&page=7&p=13468260#post13468260](http://ubuntuforums.org/showthread.php?t=2213631&page=7&p=13468260#post13468260)
Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)
[https://ubuntuforums.org/showthread.php?t=2259682](https://ubuntuforums.org/showthread.php?t=2259682)
A new and so far successful attempt to create a stable portable system, that works in UEFI and BIOS mode
[http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506](http://ubuntuforums.org/showthread.php?t=2213631&p=13262506#post13262506)
[http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/](http://spblinux.de/blog/2013/06/uefi-and-bios-bootable-usb-stick-with-grub2/)

---

### Post by C.S.Cameron on 2016-11-12
Have a look at **mkusb**, it will make a Persistent Live USB with the first partition either NTFS or FAT32 depending on your choice.
I think it will fill your requirements exactly.

It is also designed by Sudodus. [https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

---

### Post by sudodus on 2016-11-13
+1 to *C.S.Cameron*'s suggestion. I think mkusb will make what you need. Try it, and please ask, if something is confusing or does not work for you. We are here to help :-)

When you feel more confident and if you wish, you can create your own USB boot drive 'from scratch' according to the tips by *oldfred*.

---

