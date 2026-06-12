---
title: "Triple boot - Windows / Ubuntu 14.04 / Ubuntu 16.04"
date: 2017-11-05
forum: Installation &amp; Upgrades
---

### Post by 5circles on 2017-11-05
I'm trying to figure out how to add Ubuntu 16.04 LTS to a dual boot system that has Windows 8.1 and Ubuntu 14.04 installed already.  The system is a Dell 8700 XPS with a 1TB hard drive.

My basic concern is that when I try installing from the DVD, using Other type of installation, the install wants to create a boot partition.  According to what I've read, if it boots in UEFI mode (which apparently it did because of the list of GRUB options), the install shouldn't be asking to create a boot partition. I turned off Secure Boot, but it made no difference.  I've seen some references to downloading a UEFI version of the install DVD, but I can't see any version with that option.  The disk is GPT with 10 partitions (4 primary - which is either relevant or not depending on what I read).   

I'm currently making a partial image of the 5 windows partitions (ESP, Diags, WinRetools, OS, PBR Image) using O&O Disk Image.  I have space available for the Ubuntu 16.04 system, and intend to reuse the ext4 and swap partitions.

I've also seen some references to using Boot Repair after the installation - because it will probably get screwed up.  I did something like that years ago for a much earlier version, but I was hoping it wouldn't be necessary to just wish for the best this time.

Any guidance would be most appreciated.

Thanks
Mike

---

### Post by oldfred on 2017-11-05
Only if you choose one of the automatic install options that uses LVM or LVM with full drive encryption (which erases entire drive) will you get a /boot partition. But LVM should be used for entire drives and then it is not compatible with Windows.

If drive is gpt which pre-installed Windows would be, there are no primary, nor logical partitions. Just partitions that are in effect all primary.

 If UEFI only, then can just extract ISO with 7-zip to FAT32 formatted drive with boot flag on FAT32 partition.
Will not boot in BIOS mode
UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 

More info on UEFI installs in link in my signature, below.

---

### Post by 5circles on 2017-11-05
Thanks OldFred.  I didn't see your reply first, but it covers some of the things I did.  I created a USB drive instead of using the DVD, and paid more attention to the messages at the critical point (particularly the part that seemed to imply that a boot partition would be created/overwritten), and I crossed my fingers.   It all worked as I'd hoped.  The boot window now shows an additional couple of entries for Ubuntu 16.04 and the old Ubuntu entries were renamed as 14.04.   All 3 OS can boot, and I can ditch the image of the windows partitions in favor of a better backup before too long.

Now I have to figure out how to get VNC access to the new installation, and do all the rest of the setup.  VNC access was a lot of trouble with 14.04, and I was never able to get a connection before login.  I thought I had it right this time, but I'll have to go back to 14.04 anyway so maybe I can figure it out from there.

---

