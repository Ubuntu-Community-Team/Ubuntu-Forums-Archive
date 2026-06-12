---
title: "Is there any way to install Ubuntu to USB / thumb drive ?"
date: 2013-06-12
forum: Installation &amp; Upgrades
---

### Post by wpshooter on 2013-06-12
Is there any way to install Ubuntu to a USB / thumb drive ?  

I am not asking about putting the Ubuntu image on the USB for a LIVE version but actually INSTALLING (just like you do on a computer internal hard drive) with /root /home & swap partitions.

I have tried this a number of ways and none have so far been successfully.  

One of the problems that I am running into is that once the installation is completed to the USB, I get an error message saying that it can NOT install the bootloader to the USB drive.

Is there a way to do a complete installation to a USB key drive just like you would to a hard drive ?

Thanks.

---

### Post by slickymaster on 2013-06-12
See if this [post]("http://ubuntuforums.org/showthread.php?t=2153159&p=12685435&viewfull=1#post12685435") can somehow point you in a good direction.

Edit: Also, you might want to take a look at [isostick]("http://isostick.com/")

---

### Post by oldfred on 2013-06-12
It is just like any install to a second drive or external drive. You do have to use manual install and specify to install grub2's boot loader to the MBR of the external drive if a BIOS boot system. If UEFI then you need gpt partitioning and an efi partition to be first.

       Install to external drive. Also any second drive.
Installer version has not changed much so still a good guide except I do not recommend the separate /boot for most systems. Older systems may need it. And some with very large / (root) partitions. BIOS/MBR not for UEFI
[http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/](http://www.linuxbsdos.com/2012/07/23/dual-boot-ubuntu-12-04-and-windows-7-on-a-computer-with-2-hard-drives/)
Installing Ubuntu in Hard Disk Two (or more) internal or external Lots of detail - now alternative (text based) installer which is not available on newest versions. 
Different versions have slight difference in install screens but process is the same. And gui versions are not really a lot different.
[http://members.iinet.net.au/~herman546/p24.html](http://members.iinet.net.au/~herman546/p24.html)
p24/041.png Shows combo box to select where to install the grub2 boot loader.
Where Do You Want To Install GNU/GRUB boot loader?
[http://members.iinet.net.au/~herman546/p24/041.png](http://members.iinet.net.au/~herman546/p24/041.png)

If you have installed to a flash drive, run the BootInfo report and post link.
      
 Post the link to the BootInfo report that this creates. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or 'Create BootInfo' report (Other Options) & post the link it creates, so we can see your exact configuration and diagnose advanced problems.
LighterWeight (Lubuntu based) Boot-RepairCD
[http://sourceforge.net/projects/boot-repair-cd/files/](http://sourceforge.net/projects/boot-repair-cd/files/)

---

### Post by C.S.Cameron on 2013-06-12
Following is step by step how to install 12.04 on a 8GB flash drive, 13.04 is similar.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD or Live USB.
Start the computer, the CD/USB should boot.
Select language.
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Continue
At "Installation type" select "Something else".
Continue
Confirm Device is correct.
Select "New Partition Table" 
Click Continue on the drop down.

(Optional partition for use on Windows machine)
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1000 megabytes.
Location = Beginning.
"Use as:" = "FAT32 file system".
And "Mount point" = /windows.
Select "OK"

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 4500 to 6000 megabytes, Beginning, Ext4, and Mount point = "/" then OK.

(Optional home partition)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1000 to 4000 megabytes, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional swap space, allows hibernation)

Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1000 to 2000 megabytes, or same size as RAM), Beginning and "Use as" = "swap area" then OK.

(Important)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".

Select your location.
Continue.
Select Keyboard layout.
Continue.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are worried about loosing your USB drive.
Select Continue.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
You may do an update-grub later.

---

### Post by wpshooter on 2013-06-13
I discovered that the problem with the bootloader not being able to be installed was the fact that apparently you have to make a separate /boot partition on the USB thumb drive for it to be installed into and point to that /boot partition (whereas you do NOT have to do this when installing to an internal hard drive because the hard drive apparently already has provisions for the bootloader)  !!!

However, unfortunately, even after the "APPARENTLY" completely sucessfully installing to the USB thumb drive, when I tried re-booting to USB, it would not boot to it (yes, I had BIOS set correctly), just went to a blank screen after BIOS displays and would never come to the desktop.

Back to the drawingboard.

---

### Post by oldfred on 2013-06-13
I have a full install in a flash drive and do not have a separate /boot. 

Some large external hard drives need a /boot inside the first 100GB or a smaller / (root) fully inside the first 100GB and the rest of the drive as /home or data partitions.

---

### Post by TNFrank on 2013-06-13
If you're wanting to install Ubuntu on a USB drive so you can take it with you and boot off of it on other machines then you can either use UNetbootin or Startup Disk Creator.  I've had more luck with Startup Disk Creator in making bootable USB's then I have with UNetbootin although I can only use UNetbootin to make USB drives with small iso's like CorePlus or Damnsmall, Startup Disk Creator won't see them for somereason. 
  Either way I like being able to take a familiar Op System with me to use on other computers that I may have to use. ):P

---

### Post by ubfan1 on 2013-06-13
As Oldfred indicated, full USB install used to be nothing special, no need for /boot, swap, etc. Install the bootloader to the target device and enter your password when asked.  Maybe you have another issue?

UEFI/Secure boot machines have special requirements for booting, which a full install to USB must handle.  

You need to decide how you are going to use the USB:
 1) Booting on non-UEFI machines
   a) msdos partitioning takes an MBR bootloader (the legacy way).
   b) gpt partitioning requres a grub-boot partition (never tried this) 
 2) Booting on non-secure boot UEFI, need a bootable, FAT32, efi partition
    containing a copy of nonsigned grubx64.efi as file /EFI/Boot/bootx64.efi,
    and file /EFI/ubuntu/grub.cfg (never tried this).
 3) Secure boot machines need shim.efi copy as file /EFI/Boot/bootx64.efi
    as well as the signed grubx64.efi in /EFI/Boot.  grub.cfg should be 
    located at /EFI/ubuntu/grub.cfg  (Works on machines following the UEFI spec).
 4) Boots anywhere like the live media, use msdos partitioning for an
    MBR bootloader, have a bootable FAT32 efi partition set up like the secure 
    boot, but not sure how a non-secure boot EFI boot works.  As TNFrank
    says, the live media is hard to beat for portability.  Fix the UEFI persistence
    problem (bug 1159016) yourself, and if you really need more than 4G,
    use a partition labeled "casper-rw"

The UEFI install problem is that the install allows you to specify the "boot" device, but that really only works for installing the MBR.  When run on an UEFI secure boot machine, and installing to a USB meant to be run on a secure boot machine, the hard disk's EFI partition is mounted on the target
 (/target/boot/efi) instead of the target's efi partition.
This leaves the USB efi partition empty, and unbootable.  Either you fix this empty partition manually (It's really simple), or run the install from the "Try" desktop icon, and have a terminal handy to quickly unmount the hard disk's efi partition and mount the target's.

Removable media ESP -- bootable FAT 32 EFI Partition (250M)
                       (Skipping the Windows files)
/EFI/Boot/bootx64.efi  -- this the bootloader used, so make it a copy of shimx64.efi for secure boot, otherwise a copy of unsigned grubx64.efi
/EFI/Boot/grubx64.efi  -- When bootx64.efi is a copy of shimx64.efi, put the signed grubx64.efi in the same directory.
/EFI/ubuntu/grub.cfg   -- The grub file.

---

### Post by wpshooter on 2013-06-13
> **TNFrank said:**
> If you're wanting to install Ubuntu on a USB drive so you can take it with you and boot off of it on other machines then you can either use UNetbootin or Startup Disk Creator.  I've had more luck with Startup Disk Creator in making bootable USB's then I have with UNetbootin although I can only use UNetbootin to make USB drives with small iso's like CorePlus or Damnsmall, Startup Disk Creator won't see them for somereason. 
  Either way I like being able to take a familiar Op System with me to use on other computers that I may have to use. ):P

My understanding is that the programs that you mention do not **INSTALL** OS to the USB drive but instead only burn the ISO image to the USB drive, which you can then boot to (i.e. LIVE boot version) but it is NOT the same as doing an INSTALL to a hard drive which can subsequently have all of the available updates applied to it and also has the capability to save user data to the /home partition so that it can be available to the user on subsequent boots.  I have tried both of the ones you mention and also others and none of them so far will make a bootable INSTALL of the OS to a thumb drive, make a LIVE boot version with the image YES, no problem, but it is a no go for INSTALLING.

How do you INSTALL the OS to a USB thumb drive.  It would seem like that this would be a fairly straight forward task but it sure is NOT turning out that way for me ?

Thanks.

---

### Post by C.S.Cameron on 2013-06-13
See post 4 above for a step by step on installing to USB.

---

### Post by ubfan1 on 2013-06-13
Was your "successful" install from a live USB?  If so, did you fix the grub.cfg devices for the first reboot (bug  384633)?  Can you confirm you are not on a UEFI machine?  Do you have a password on your account, and are you asked for the password before the bootloader installation ?  Your error is puzzling, and some more info might help us determine what's wrong.7

---

### Post by confused57 on 2013-06-13
You might want to try installing to a different brand of usb flash drive, it's been my experience that some were much better than others for an Ubuntu installation(not a live usb).

---

### Post by sudodus on 2013-06-14
I have also made such installations to USB HDDs, USB SSDs and USB pendrives (flash drives). I have used USB 2 and USB 3 devices. All work. So we are many people who have succeeded, and we can help you, but I think we need more information about your hardware and software. Otherwise we can only guess.

Please let us know the

- brand name, model and above all, the size of your USB pendrive(s)!
- brand name, model and above all, the CPU, RAM size and graphics processor of your computer!
- operating system you are using (installed in your computer)!
- installation media source and target (from what device to what device are you trying to install)?
- OS distro, version and flavour that you try to install!

---

### Post by wpshooter on 2013-06-18
> **C.S.Cameron said:**
> Following is step by step how to install 12.04 on a 8GB flash drive, 13.04 is similar.

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.

Why is it necessary to unplug the hard drive ?

It appears that you are probably correct about this but I am just wondering why this seems to NOT work unless the hard drive is disabled while the install is taking place.

Thanks.

---

### Post by TNFrank on 2013-06-18
I have a copy of Ubuntu 12.04 that I installed on an 8GB USB using UNetbootin and I've updated it just like I've done on my laptop. No difference that I can see in the way it runs.  
 I've also heard of people burning the OS to a DVD(CD is too small for something the size of Ubuntu 12.04 when you include the boot loader, ect.) then they boot to the CD/DVD drive and install to their USB drive. Just choose your USB(for me it'd be sdg) and click Install. 
I'm still trying to figure out how to install multiple OS's onto a single bootable USB using UNetbootin. I posted a YouTube vid of a guy doing it but for some reason it's just not working for me or I"m not doing something right. 
 Still, it is kind of fun messing around with this stuff trying to get it to work. Hope you get it figured out. ;)

---

### Post by sudodus on 2013-06-18
It is not necessary but recommended to remove the internal drive, because it makes it easier to get everything correct. Otherwise it is easy to write the bootloader to the wrong drive (as a matter of fact, the default is the (first) internal drive). And there might be problems selecting swap partitions too. All these things are possible to manage during or after the installation, but it might be harder than removing the internal drive.

---

### Post by oldfred on 2013-06-18
All the auto install choices will install grub to sda which is the internal drive in most cases. 

Or if installing to an external device you do not want to use auto install, but need to use Something Else or manual install to get the option on where to install the grub2 boot loader.

If internal drive is disconnected then it does not matter, but manual install also gives additional options like letting you create a separate /home.

---

### Post by C.S.Cameron on 2013-06-18
Another small matter is that if you leave the internal drive active while installing, it will be mentioned in grub when you boot the USB drive.
This may or not be preferred.

---

