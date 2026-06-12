---
title: "Ubuntu Won't Reboot After Installation On Toshiba Satellite C55"
date: 2014-08-23
forum: Installation &amp; Upgrades
---

### Post by Al__Jones on 2014-08-23
The following was the process I used.

(1) I created a USB stick using Unetbootin.
(2) I then proceded to install it on my Toshiba.
(3) There was no operating system the computer.
(4) After installing I restarted the computer with the USB stick in it.
(5) It took me back to the original boot menu (1. Try Ubuntu without installing  2. Install Ubuntu  3. OEM Install  4. 'I don't remember what this was').
(6) I knew I had installed Ubuntu already, so I picked choice 1.
(7) After the computer booted (again, still on the USB stick), I ran Boot-Repair and it registered an error and gave me the following URL: [http://paste.ubuntu.com/8126339/](http://paste.ubuntu.com/8126339/).
(8) I then restarted the computer and it gave me the original boot menu.

I don't understand the problem. I have tried many different ideas and so far, none of them have worked.
Thanks in advance for the help.

---

### Post by yancek on 2014-08-23
You need to remove the usb stick you used for the installation and/or set the boot priority in the BIOS to boot from the internal hard drive.
You have an EFI partition but you also have Grub installed to the mbr.  I'm not familiar with UEFI but lots of members here are and should post to help.

---

### Post by oldfred on 2014-08-23
Are you booting in UEFI or BIOS boot mode.

You do show grub installed to MBR for BIOS boot, but do not have a bios_grub partition, so that will not work.
But you also show the efi partiiton with grub installed for UEFI boot.
You must turn on UEFI boot and/or turn off BIOS/CSM/Legacy boot mode in UEFI/BIOS. 

Since you only have one install, grub menu will not normally show. You may have to hold shift key from UEFI boot, to get grub menu to appear.

Some other Toshibas.
 TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)

---

### Post by Al__Jones on 2014-08-24
oldfred:

I tried booting using both UEFI and CSM. I got grub to put a menu up when I UEFI booted. It gave me the original boot menu.

---

### Post by Al__Jones on 2014-08-24
yancek:

I removed the USB and when I booted, I believe it said on a black screen, "Reboot and select boot device or insert boot device and press any key."

---

### Post by oldfred on 2014-08-24
Did you see links to other users with Toshiba.
The Toshiba have a limited UEFI in many models.

So you may have to use either the copy grub or shim into a /EFI/Boot folder in the efi partition or install rEFInd.

---

### Post by Al__Jones on 2014-08-24
oldfred:
I am having trouble installing refind.

---

### Post by christopher9 on 2014-08-24
I have a P50 and here's what worked for me when I would get the same error with Ubuntu 14.04, Mint 17, Elementary OS, and Lubuntu 14.04:

If you are still getting the error stating "Reboot or insert boot device....", then power off, power back on and when you see the "Toshiba" splash screen press f2 (or what ever your user manual recommendeds to enter the UEFI configuration (or BIOS in oldspeak).  Make sure the USB device is moved to the top of the boot order menu, turn on Secure Boot, turn on UEFI, and use Normal boot speed. Save that configuration with F10, then reboot with your USB boot stick inserted.  When you sign and enter the Desktop, use Software Center to install Gparted if you don't already have it. Then use the File Manager to look at the entire computer.  You should see a device listed on the left with a large Gb amount that is NOT part of the USB boot file system.  This should be your hard drive.  Open that device up and you should see the partitions from your attempted install of Ubuntu. Use Gparted to delete them all. (WARNING: this will delete everything on that hard drive!  As you stated above, there 'was no operating sysem on the computer' so this should not be a big problem for you I'm surmising...) Then reboot on with the USB stick still inserted and when you get the menu with the choice to 'Try with installing' or 'Install' use the 'Install' choice.  The Distro will handle creating the new partitions for the install. Follow the rest of the instructions. Good luck !

---

