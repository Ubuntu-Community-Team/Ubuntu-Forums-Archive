---
title: "Sony vaio sve1713acxb and uefi"
date: 2013-03-10
forum: Installation &amp; Upgrades
---

### Post by CWM on 2013-03-10
Hello Everyone,

I am kind of a beginner... I have used Linux before just fine.... Kubuntu, and Unity...

But got a new laptop I thought the old one was dead.... but it wasnt OOPS...

I put Ubuntu on a 8 gig flash Using [http://www.pendrivelinux.com/resources/](http://www.pendrivelinux.com/resources/)

shut the pc completly down

held the red ASSIST button on the keyboard... pc turned on... said VAIO.......

then took me to a windows 8 screen.... asking me did I want to restore pc, yadda yadda

I put boot from CD / USB PEN

screen went blank for a sec.......

then I was greeted with a red box " SECURE BOOT FAILED.... OS NOT SUPPORTED..."

uh oh..... So now what? Can I have step by step instructions... I would rather run Linux... Windows 8 is.. after 2 weeks... confusing!

Thanks!

=============================================
Make *EVERYDAY *  count, and Count your blessings :)

-- Christopher

[EMAIL="CMAR606@CS.com"]CMAR606@CS.com[/EMAIL]
( Yes Mods, I know its risky to put it out there but I have a strong spam filter, So its ok. )

---

### Post by oldfred on 2013-03-11
All new Windows 8 systems have UEFI with secure boot and gpt partitioning. 

       You will need to use the 64 bit version of 12.10 or 12.04.2 and from the UEFI menu boot the flash drive in UEFI mode. That way it will install in UEFI mode.
Systems need quick boot or fast boot turned off in UEFI settings. Vital for some systems. Best to backup efi partition and Windows partition first.
Use Windows Disk Tools to shrink Windows main partition, but not to create any new partitions, if installing on same drive.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
As of 12.04.2, it is possible to install on UEFI systems with Secure Boot enabled (using signed versions of Shim, GRUB, and the Linux kernel). This is only currently set up for Ubuntu (desktop, alternate, and server) and Edubuntu images due to pressures of time; we expect to enable it across the entire Ubuntu family for 12.04.3.  Details:
[https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop](https://wiki.ubuntu.com/PrecisePangolin/ReleaseNotes/UbuntuDesktop)

Some other threads with Sony:

 Sony Vaio [SOLVED] dual boot ubuntu 12.10 & windows 8 problem 
[http://ubuntuforums.org/showthread.php?t=2094761](http://ubuntuforums.org/showthread.php?t=2094761)

sony vaio laptop error: symbol not found: `grub_efi_secure_boot'.
[http://ubuntuforums.org/showthread.php?t=2102083](http://ubuntuforums.org/showthread.php?t=2102083)
So this time I installed 12.10, then I booted again from liveCD, made backup of (efi part)/EFI/microsoft/boot and copied all files from /EFI/ubuntu into it. Then renamed /EFI/microsoft/boot/shimx64.efi to bootmgfw.efi. And it works
Used Boot-Repair to rename files:
[http://ubuntuforums.org/showthread.php?t=2103778](http://ubuntuforums.org/showthread.php?t=2103778)
To perform this, just run Boot-Repair --> Adv options --> tick "Backup and rename EFI files" --> Apply
Then reboot the PC and please tell us what you observe.

---

