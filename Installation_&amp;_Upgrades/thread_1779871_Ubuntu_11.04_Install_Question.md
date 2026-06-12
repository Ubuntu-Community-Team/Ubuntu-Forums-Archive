---
title: "Ubuntu 11.04 Install Question"
date: 2011-06-11
forum: Installation &amp; Upgrades
---

### Post by Gurn5 on 2011-06-11
Hi,

    I have what I hope is a simple question or at least a question with a simple answer.  I am installing Ubuntu 11.04 on a computer that already has Windows 7. I would like to install so that I could boot with either one.  This system has multiple hard drives.

    When running the install Windows 7 is detected and I get the option 'Install Unbutu alongside them'.  If I choose this option it only shows my external hard drive, if I disconnect the external hard drive it gives still gives me only one choice (not the hard drive I want to install to).  I have multiple hard drives, one of which is completely empty.  I would like to install to the empty drive.  If I select the install option 'Something else' I can see all my hard drives.  If I use this option and install to the drive of my choice will this still be a dual boot?

---

### Post by Herman on 2011-06-11
Yes, choose to do 'something else', and then you will be presented with a list of drives and partitions, you can choose an existing partition to format (I usually choose the ext4 file systems), and install / (the 'root' or main part of the operating system) in that and you can make the traditional swap area about 2x the size of your RAM if you wish. Alternatively, decline to make any swap area, ignore any warning messages that may pop up complaining about it and install 'dynamic swap' from the software menu later after the install has completed. (A 'swap area' is something roughly equivalent to a what you call a 'page file' in Windows language).

In the boot loader menu you can choose a hard disk or partition to install the first and second parts of the GRUB boot loader to.  It's up to you where you decide which hard disk's MBR you want to use for that and the default is to install it to the first hard disk, that's the easiest and that's what I always do, but there are a few reasons why in some cases that might not be ideal. It results in the most convenient way to dual boot though. You will be automatically presented with your GRUB Menu at boot time, and you can choose to boot Ubuntu or Windows.

If you install GRUB to the MBR of a non-first hard drive, that's okay but will you will only be able to boot Windows and if you want to boot Ubuntu you will need to go through the BIOS boot menu which is considerably less convenient. However, if you decide to remove the Ubuntu hard disk and put it in a different computer or USB external case it will be able to boot from its own MBR.

You can also install GRUB to all hard disks MBRs, which is also often a good idea.

If you have any kind of RAID or hard drive encryption then it might not be a good idea to install GRUB to MBR in the drives concerned and you will need to research and study the RAID or entire disk encryption documentation before deciding where to install GRUB.

---

### Post by Gurn5 on 2011-06-11
Thanks a bunch.  Got everything installed the way I want.

---

