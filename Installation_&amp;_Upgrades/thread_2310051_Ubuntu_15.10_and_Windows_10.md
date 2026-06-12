---
title: "Ubuntu 15.10 and Windows 10"
date: 2016-01-15
forum: Installation &amp; Upgrades
---

### Post by shane_faulkinbury2 on 2016-01-15
I have both OS's installed, but I have a problem booting into Ubuntu.   I already had Windows installed on my laptop, but wanted Ubuntu on it too.  I created a partition in Disk Management in Windows and then booted using my Ubuntu disk and installed.  After installing all the programs I wanted I booted back into Windows.  After I was done in Windows I tried booting back into Ubuntu, but I can't.  I've tried everything in BIOS, but nothing works.  Ubuntu is still there because I can see it in Disk Management on Windows and when pressing F12 on bootup.  When I press Ubuntu after pressing F12 it takes me to an error screen!  It's a Dell Aspirion 5552.  :confused:

---

### Post by oldfred on 2016-01-15
Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

### Post by shane_faulkinbury2 on 2016-01-15
[http://paste.ubuntu.com/14514375/](http://paste.ubuntu.com/14514375/)

Thanks for your help oldfred!

---

### Post by oldfred on 2016-01-16
You have an UEFI system.
And you have Windows installed in UEFI boot mode with gpt partitioning. Not sure if secure boot is on or not. Usually better to have it off.
But you installed Ubuntu in BIOS boot mode, and put grub2's boot loader into sda6's PBR or partition boot sector. BIOS based computers only boot from MBR or first sector of drive. And BIOS normally uses MBR(msdos) partitioning. But Ubuntu can boot in BIOS mode from gpt partitioning (Windows will not), but requires another supporting partition, the bios_grub partition. That must be unformatted and only needs to be 1 or 2MB. And with bios_grub flag. Then you can use Boot-Repair to install grub to MBR. But you will not be able to dual boot from grub and must always select system to boot from UEFI boot menu or one time boot key like f10 or f12 (check manual).

What brand/model system?

Probably better to reinstall. Much better to use ext4 not ext3 and install in UEFI mode with Something Else choosing same / (root) partition. It will find swap automatically on a re-install.
Boot-Repair can convert a BIOS install to UEFI, but you would still have ext3 format. In advanced options when booted in UEFI mode, choose the total uninstall/reinstall of grub. It can then uninstall grub-pc(BIOS) and install grub-efi-amd64(UEFI).

How you boot install media is then how it installs, so boot in UEFI mode.
       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Lots more general info on UEFI in link below in my signature.

---

### Post by shane_faulkinbury2 on 2016-01-16
Thanks for the link oldfred!  I was reading through it and on[SIZE=3] [COLOR=#333333][FONT=Ubuntu]Identifying if the computer boots the Ubuntu DVD in UEFI mode[/FONT][/COLOR][/SIZE][COLOR=#333333][FONT=Ubuntu][SIZE=3] and I [SIZE=2]wondered what mode I was booting into and sure enough I was booting into Legacy mode so I went into BIOS and changed to UEFI.  So I tried to reinstall and get another error!      [B][SIZE=4]Unable to Install GRUB in /dev/sda'failed
 [/SIZE][/B]      [/SIZE][/SIZE][SIZE=2]               This is a fatal error
[/SIZE]So I tried to install on my usb flash drive instead and got the same error.  So I'm re-downloading and will try that out next! [/FONT][/COLOR]

Damn, I keep getting the same GRUB error.  I even tried Ubuntu 14.04.3 and both give the same error.  Any other ideas?

---

### Post by ubfan1 on 2016-01-16
Rerun the boot-repair report in UEFI mode, that will give some more information.  grub should linstall into the EFI partition directory /EFI/ubuntu, is that directory present and can you create a file in it?  Sometimes, a filesystem error prevents anything from being written into the directory, and some repair is necessary to fix it.

---

### Post by shane_faulkinbury2 on 2016-01-17
This is weird!  I try running Boot-repair and I get the following error!

---

### Post by oldfred on 2016-01-17
Python3 is not the standard, yet. Perhaps in 16.04. What live installer are you using for Boot-Repair? Same as install, 15.10?
So did you change default python which then causes major issues? I doubt if Boot-Repair has been updated to run with python3. Issue with many applications and that is why they have delayed a full change to python3 for years.

---

### Post by shane_faulkinbury2 on 2016-01-17
I'm just using The Standard method: from an Ubuntu disk as mentioned here  [HTML]https://help.ubuntu.com/community/Boot-Info[/HTML]

---

### Post by oldfred on 2016-01-17
What version of Ubuntu live installer?

---

### Post by shane_faulkinbury2 on 2016-01-17
Sorry I used Wrap [HTML] tags, but now I see that was the wrong one!  I should have used Link!

---

### Post by shane_faulkinbury2 on 2016-01-17
15.10

---

### Post by oldfred on 2016-01-18
I do not know how/where you are getting python3 errors. 
Python2 is the standard in 15.10.

---

### Post by shane_faulkinbury2 on 2016-01-18
What's strange is I was able to use it when I was in Legacy mode, but now I'm not able to in UEFI!

---

### Post by oldfred on 2016-01-18
And that difference makes no sense either.

The only real difference is whether you boot installer with syslinux for BIOS or grub2 for UEFI, kernel & applications are all the same. 

Once installed, the difference is just versions of grub2, grub-pc for BIOS and grub-efi-amd64.

---

### Post by shane_faulkinbury2 on 2016-01-18
The thing is that when I first got the laptop is that I installed Ubuntu on the whole hard drive with the same Ubuntu 15.10 media.  I then contacted Dell and they sent me recovery media for Windows 10.  I installed it and now I'm having problems installing Ubuntu on the partition I created in Windows!  :confused::rolleyes:

---

### Post by oldfred on 2016-01-18
Windows cannot create a partition for Linux, it does not know Linux format types.
Also did you recovery in UEFI or BIOS mode?
Post this:
sudo parted -l

---

### Post by shane_faulkinbury2 on 2016-01-18
Yes, UEFI is where I cannot run the Boot repair, it ran when I was in Legacy, but not in UEFI.  Here are the screenshots for sudo parted -l.  I created the 300 GB partition in Disk Management in Windows to install Ubuntu on.

---

### Post by oldfred on 2016-01-18
You have a DVD that says it is a MAC? Are you using a DVD created by a Mac?

I stopped using DVD ages ago except for data Backups. I often burned a coaster. Hopefully backups are not coasters. :)
And flash drives were reusable.

---

### Post by shane_faulkinbury2 on 2016-01-18
I never touch anything Apple :rolleyes:!  And I've tried installing on both DVD and flash drive!

---

### Post by oldfred on 2016-01-19
I have not used a DVD for years, so do not know structure now. 
What tool did you use to create DVD?

I prefer flash drives and if you just want UEFI boot, you only need to format a flash drive with FAT32 and boot flag and use any extraction tool to extract ISO onto flash drive.

 UEFI only USB key, just extract ISO ( 7 zip or similar) to FAT32 formated flash & set boot flag.
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media)

  
 Howto help USB boot drives - sudodus
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)


Installation/FromUSBStick - with lots of details on various USB drive issues by  sudodus
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
      
 Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
[https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode](https://help.ubuntu.com/community/Installation/FromUSBStick#Ubuntu_single_boot_in_UEFI_mode)

---

