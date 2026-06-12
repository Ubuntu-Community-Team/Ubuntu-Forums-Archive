---
title: "No GRUB, No Boot Menu, Win10 on Asus Laptop"
date: 2016-07-09
forum: Installation &amp; Upgrades
---

### Post by homer1956 on 2016-07-09
I am trying to use Ubuntu 16.04 LTS  on CD-ROM to retrieve my files lost on a failed NAS that is supposed to be Linux file system. I have tried every trick that I can find on the web to get a boot menu to show up after I did a clean install in a 50gig partition that is unformatted and listed s free space. UEFI has secure boot disabled and Fast Boot is disabled in Windows as well. I can launch the CD with now problem but none of the Function keys will bring up a menu to launch Ubuntu. The only menu I get is with the ESC key pressed on boot to choose which drive to launch from. I installed Ubuntu numerous times and never once did it recignize my Windows installation and allow me to install along side with Windows 10. It sounds like the Windows Boot Manager is being a biotch but I can't figure out what to do about it. The boot-repair app from inside a "try" version of Ubuntu reports that I need to install the boot repair program from a USB in legacy mode or in EFI mode. Huh? Please help. BTW, my windows install was a clean install on a freshly partitioned 500gig drive.

---

### Post by yancek on 2016-07-09
> I am trying to use Ubuntu 16.04 LTS  on CD-ROM

Is that a typo?  Ubuntu hasn't fit on a CD for years,are you actually using a DVD?  If you are trying to use a Live DVD to recover data, what did you install on the 50GB partition you refer to and why?  Did all your attempts to install Ubuntu fail?  Did you use the "Something Else" option when trying to install Ubuntu?  That's basically the manual option and gives you more control over the install.  Did you install windows 10 or was it pre-installed?  If pre-installed, it was almost certainly using UEFI so you would need to boot and install Ubuntu UEFI.  See the link below for details and if you have boot repair, you should post a link to the output as instructed as that will give details on your system so someone can suggest a possible solution.

---

### Post by homer1956 on 2016-07-16
From everything I have read, I was under the impression that I needed to install Ubuntu in "legacy" mode so I turned off Secure Boot in UEFI bios and Fast Boot in Windows first. I created two partitions; one for "/" root and the other for "/boot" as per what I read and performed the install thinking the install would auto-select the appropriate partitions. Don't know if it did or didn't as I can't read the partitions in Windows 10. I installed Win10 fresh on a 500gig partition so it wasn't factory installed. The laptop came with Win8 but I hated it and started over with 10. And yes, my Ubuntu is on a DVD, not CD, that I purchased from Amazon thinking I would get some form of documentation to go with it as I am a super-newbie when it comes to Linux. The reason I installed Ubuntu, or tried to, was that I wasn't able to read my external drive at all with the LiveDVD and figured it was a partial install running virtual and the "full" install would give me more capabilities to access my lost files on the NAS drive. As far as the boot repair, it gave me a message that I had installed in "legacy" mode and would have to address the repair with "legacy" procedures. Huh?

Thanks for your reply. Maybe I'll get this figured out some day.

---

### Post by oldfred on 2016-07-16
Since you have an UEFI system, better to install in UEFI boot mode. And you cannot dual boot from grub if Ubuntu is CSM/BIOS and Windows UEFI.
But you can dual boot from UEFI. But may have to turn on UEFI to boot Windows and turn UEFI off/CSM on to boot Ubuntu.
UEFI & BIOS boot modes are not compatible. Just both are available.
       CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  

Also best not to use separate /boot partition.

Not sure what directions you saw, but many older ones that are not correct.
      
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)

---

### Post by homer1956 on 2016-07-17
Yes, it's been my experience during this ordeal that my UEFI Bios will not allow boot to DVD unless I am in CSM mode. When I try to install Ubuntu from the DVD it installs in legacy mode which prevents me from booting to the Linux partition OR from running the boot repair successfully as it is in legacy mode. 

Question, when I run the DVD in "Live" mode I am assuming it's running a virtual RAM instance, is Ubuntu fully functional or does it only have partial functionality?

---

### Post by oldfred on 2016-07-17
Some older UEFI systems were like that. We then installed in CSM to gpt drive, partitioned in advance, so it has the ESP - efi system partition as well as the bios_grub which is for CSM/BIOS boot.
Then with Boot-Repair run updates to uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI).

And some systems do require CSM on, but still let you choose to boot flash drive (or DVD?) in UEFI mode. Most see two boot options to boot installer, one clearly UEFI:name and other just name which is BIOS boot. Name is label or brand of flash drive, not sure what DVD shows. Few use DVDs anymore. I used to get a lot of coasters, and generally burned several support/repair DVDs including gparted, parted magic, knoppix, etc. But they changed versions and I had to burn more. With flash drive I just update to newest version.

Generally fully functional, but you cannot update and it can be difficult to add drivers. And each time you reboot you have to change all settings again. You can save downloading, but still have to reinstall software you download, if you use persistence with flash drive.

What model Asus. One very early Asus could not install in UEFI mode, but all recent ones do work. Some require boot parameters.

---

### Post by homer1956 on 2016-07-17
SUCCESS!! I downloaded Ubuntu, burned ISO to flash drive, flash drive recognized by UEFI, installed trial from flash, installed full from flash drive, performed updates and now I have GRUB UI with boot choices!!! I first went into UEFI and reset all to default just to see what would happen with secure boot on and everything went without a hitch.  Thank you, thank you, thank you!!!

But just one more question, the reason I pursued Linux in the first place; my Iomega 2 TB EZ Media & Backup Center hard drive is now in a USB3 enclosure so I can try and retrieve the 1TB+ files on it which are supposed to be accessible with Linux. I have no idea of where to start with this as I am completely new to Linux.

If you could provide some direction, I would be very pleased and appreciative.  Thanks for all your help in getting me up and running.

---

### Post by oldfred on 2016-07-17
Best to start new thread with title related to specific issue.

Many of the vendor backup are unique formats. You may have to install drivers and do repairs, if it is supposed to work with Linux.

---

