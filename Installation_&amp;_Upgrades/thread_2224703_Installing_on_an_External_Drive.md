---
title: "Installing on an External Drive"
date: 2014-05-17
forum: Installation &amp; Upgrades
---

### Post by luis28 on 2014-05-17
Hey guys! I had a Fedora/Windows 8 dual boot going on but when I was upgrading to windows 8.1 it caused my windows bootloader to break (at least that's what I think happened). Long story short I had to format my hard drive and clean install windows 8 because I use it more often than linux. Now I want to install Ubuntu on an external hard drive. I want to have 4 partitions: a swap, a root, home, and an unrelated partition where I can backup files. I created the partitions on Windows (picture below). So can I get on the Ubuntu installation and tell it where I want each thing to go under 'something else'. I tried installing it yesterday and making the partitions from the install dvd, but it was taking too long, so this might be better. Any advice will be appreciated. 

[IMG]http://i61.tinypic.com/n4gmww.png[/IMG]

Also I'm installing on a Samsung np700z5c-s02ub laptop. I've heard that these laptops have been bricked from installing another os on it. Should I be concerned if i'm installing to an external drive?

---

### Post by Mark Phelps on 2014-05-17
The partitions you created are all Windows filesystems -- and Ubuntu doesn't use Windows filesystems.  Also, as far as I know, Windows does not know how to format partitions using Linux filesystems.  So, what you really need to do is boot from an Ubuntu LiveDVD/LiveUSB and use GParted to create the Linux filesystems on the external drive.

---

### Post by GeorgeLSpencer on 2014-05-17
Windows 8 makes a secured boot, so unless this is turned off in the BIOS, you will not be able to choose an operating system via grub. Others have learned how to overcome this, so read the replies in this forum to do the same. The only thing to remember for the live Ubuntu boot is to correctly identify your external hard drive, so that Ubuntu is installed on the right drive. Other than this, it should be a piece of cake.

---

### Post by ubfan1 on 2014-05-17
Is this a UEFI machine?  Did Windows 8 come preinstalled on it?  Why is your external disk not using the gpt partitioning?  Assuming a UEFI machine:
Now assuming the external disk is USB, in the UEFI Settings/BIOS, make it earlier in the boot order than the hard disk.  There is absolutely no reason in the world to make any other changes to the NVRAM boot entries, so using a current Ubuntu like 14.04, the bricking issue should not arise -- nevertheless, have a good backup procedure, the nvram can be filled up from userspace as well as from a bad kernel driver.  

You should use the gpt partitioning to avoid all the primary/logical partition limitations.   Make a EFI partition (300-500M FAT32) flagged bootable.  In the install, give this external EFI partition (NOT the disk itself) as the location for the bootloader.  The installer will want to dump the shim/grub boot files onto the internal disk's EFI, which you want to avoid, and hopefully the explicit external EFI partition will do that.  Not that the boot wont work with the boot files on the internal disk, but next thing you know, there will be unwanted, unneeded, nvram entries created for them, and the fight begins between Windows and Ubuntu for who's going to be in position one, burning through nvram on both sides.
  After the install, and the bootloader files are (hopefully) put into the EFI partition in directory /EFI/ubuntu.  These boot files are shimx64.efi (for secure boot), grubx64.efi (signed for secure boot, unsigned otherwise), and a grub.cfg stub which should just pull in the maintained grub.cfg from the root /boot/grub/grub.cfg file.  Now, the gotcha is for an external boot, the bootloaders are in the wrong place!  The removable media boots from /EFI/Boot/bootx64.efi , so simply copy from /EFI/ubuntu/grubx64.efi to /EFI/Boot/bootx64.efi (or for secure boot, use the shimx64.efi as the bootx64.efi and have a copy of the signed grubx64.efi in the same directory.  The grub.cfg file will still be found in /EFI/ubuntu, so no need to move it.  boot-repair does this for you, but really, it's just copying a few files around.  Of course, you will have to reformat the ubuntu partitions to ext4 or something more appropriate for the install than ntfs.

---

### Post by oldfred on 2014-05-17
They originally blamed it on Linux, but some Linux developers showed that eventually Windows may trigger same issue. Best to make sure you have an updated UEFI/BIOS.

 [https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/QuantalQuetzal/ReleaseNotes/UbuntuDesktop)
Booting the Ubuntu installer in UEFI mode from a USB disk on certain Samsung laptops (530U3C, NP700Z5C) may trigger a firmware bug that renders the machine unbootable. Users are advised to use caution when installing on Samsung laptops and ensure that they are configured for legacy BIOS mode, not UEFI mode. (1040557) 


 UEFI boot live-usb bricks SAMSUNG 530U3C,np700z5c laptop - fix released
[https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557](https://bugs.launchpad.net/ubuntu-cdimage/+bug/1040557)
[http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html](http://www.h-online.com/open/news/item/Booting-Linux-using-UEFI-can-brick-Samsung-laptops-1793958.html)
[http://mjg59.dreamwidth.org/25091.html](http://mjg59.dreamwidth.org/25091.html)
The problem also appears to affect Ubuntu 12.10 and other Samsung models. The Ubuntu bug report includes posts from users reporting that the problem also affects 300E5C, NP700Z5C, NP700Z7C and NP900X4C series laptops.
[http://mjg59.dreamwidth.org/23554.html](http://mjg59.dreamwidth.org/23554.html)

---

### Post by luis28 on 2014-05-17
Okay so I took the plunge and did it according to my plan above (no replies had been posted at the time). And it worked. I had to format the root and home partitions I created to, as Mark Phelps pointed out, Linux filesystems; I chose EXT4 because I read it's the most widely supported. The installation was successful and after restarting the computer booted straight to Ubuntu. Great! I shutdown the pc and tried to boot to windows but it didn't. I went back to BIOS settings and set it to UEFI mode. Exited BIOS and the pc went straight into Windows. Everything is working fine to my knowledge. EXCEPT I couldn't access my Windows drive on Ubuntu. And I couldn't get onto /home on the Windows side (sometimes I need to do that). 

This is a UEFI @GeorgeSpecer I did turn off UEFI as a security measure, I don't want a brick lying around. @ubfan I don't know why my external usb drive doesn't use a partition scheme. I don't understand most of your post dealing with the NVRAM issue. Would you mind explaining further?

---

### Post by Mark Phelps on 2014-05-17
You won't be able to access the Windows side from Ubuntu because when you leave Windows, the partitions remain MOUNTED.  This is the new Hibernation form that Win 8 establishes by default.  You have to disable FastStartup in Win8 to turn off this Hibernation.

Also, unless I misunderstand what you are trying to do, you are not going to be able to get to "/home" (in Ubuntu) from Win8 because it can't read Linux filesystems.

---

