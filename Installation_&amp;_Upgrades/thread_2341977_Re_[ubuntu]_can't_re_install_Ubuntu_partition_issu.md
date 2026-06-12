---
title: "Re: [ubuntu] can't re install Ubuntu partition issues"
date: 2016-11-02
forum: Installation &amp; Upgrades
---

### Post by shinobikush74 on 2016-11-02
MY Asus is about 4 years old. Was running Windows 10 but had too many bugs. I fully installed Ebuntu and was running smoothly until about a month ago. I tried to install Ubuntu 14.04 and I keep getting a message saying my partition is messed up. So right now,I am running the install disk while posting. Which means I can save nothing after I turn the laptop off. I thought I could bypass the issue by running the disk and trying to install from a USB that had a Kubuntu version. This did not work either.I ran into the exact same partition messages. I tried to erase the entire disk to no avail. I have nothing else to try... something has to work because if the disk makes ubuntu run, then what is causing it not to fully install?  I apologize for my lack of technical terminology. I am totally new to this. But, I know I can solve this issue. 

Thank you for your time and energy,

                                                        Shinobi

ASUS with Intel  Pentium PU B980 @2.40 6 HZ 
4096 mb of memory

Attempted Disc Install.. wireless set up works. able to give password for wifi..wi fi connects

got into the "Preparing To 
install Ubuntu" Section and opted to not download updates or install 3rd party software..etc.... 

I am installing as a "superuser"

after about 5 minutes, I am still in the "preparing" section

Next steP

"the machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems installed suing "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating system later. 

this is to force UEFI installation...even when I continue in UEFI mode

Choose "erase disk and Install Ubunutu.. won't allow me to choose "install Now"... is my laptop dead?

ASUS with Intel  Pentium PU B980 @2.40 6 HZ 
4096 mb of memory

Attempted Disc Install.. wireless set up works. able to give password for wifi..wi fi connects

got into the "Preparing To 
install Ubuntu" Section and opted to not download updates or install 3rd party software..etc.... 

I am installing as a "superuser"

after about 5 minutes, I am still in the "preparing" section

Next steP

"the machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems installed suing "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating system later. 

this is to force UEFI installation...even when I continue in UEFI mode

Choose "erase disk and Install Ubunutu.. won't allow me to choose "install Now"... is my laptop dead?

All I wanted was ubuntu only on my laptop. I don't want any other operating system. I cant copy and paste as the laptop in question is not working properly. I selected the "erase disk and install Ubuntu Studio" option...but it won't let me install

I don't care if everything on my laptop is lost. I just want a fully operational system. I have nothing of importance on this laptop

My system is a little over 4 years old...I was running the e ubuntu package fine for almost a year..then it crashed......now I can't install anything

I disabled the csm and enabled it....still having issues either way....I am definitely getting frustrated. This has caused issues with my classes and I am too broke to purchase anything at the moment....so I need this laptop to work. I see people with older laptops that run fine....maybe I just got a crappy deal

This is the message I get....."This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "Bios compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.

If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing system, you have the option to force that here. If you wish to keep the option to boot an existing operating system,you should choose NOT to force UEFI installation here

---

### Post by oldfred on 2016-11-03
Was Windows in UEFI or BIOS boot mode.
And then was your Edubuntu install UEFI or BIOS.
UEFI boot is gpt partitioned with Windows & normally gpt with Ubuntu.
BIOS boot is MBR partitioned with Windows & normally with Ubuntu.

And how you boot install media UEFI or BIOS from UEFI boot menu is then how it installs.
Post this from live installer:
       sudo parted /dev/sda unit s print

---

### Post by shinobikush74 on 2016-11-03
not sure I can not access windows anymore..when  I go to "try ubuntu" instead of installing it..and try to access Gparted, I get a "Libparted Error... input/output error during read on /dev/sda, with the options to "retry","Cancel", or "Ignore"...

When my laptop comes on, it is automatically in BIOS mode.. I have no idea what UEFI mode even looks like
when attempting to install, it says I can force UEFI mode, I have no idea what that means

when  I turn on the laptop  I get this sequence of lines[ATTACH=CONFIG]271943[/ATTACH]

input/output error during read on/dev/sda
when  I try to access Gparted...does this mean my laptop is now dead?

---

### Post by oldfred on 2016-11-03
It can be just a corrupted partition table.
Are you able to run:
sudo parted /dev/sda unit s print 				
and:
sudo fdisk -lu

---

### Post by shinobikush74 on 2016-11-23
I typed in the lines and hit "enter"....nothing happened. I can use the disk to access ubuntu, but can not actually install it

Is something supposed to happen or do this mean my laptop is corrupted?

Is something supposed to happen or do this mean my laptop is corrupted?

I stand corrected. I end up getting a list saying /dwv/sdb1is 2.6g the id is 0 and the "type" is empty

Where as /dev/sdb2 is 2.3 M the id is "ef" the type is "EFI"(FAT_1/16/32)

---

### Post by oldfred on 2016-11-23
Please copy & paste text/terminal output. And if longer use code tags. Code tags also keep formatting which often helps, also. You can easily add code tags with Forum's advanced editor and # icon.

You show standard UEFI partitions for an Ubuntu only default install. You may have forced an install and overwrote whatever else was on system.
If that was not intentional, stop using system, and post for recovery instructions, but you will not be able to recovery everything. Often easier just to restore from your backups.

If you have UEFI on in UEFI/BIOS then you should be able to boot. With only Ubuntu installed you do not get a grub menu unless you press escape key (possibly more than once) between UEFI/BIOS screen and grub. You may have to use UEFI boot menu or f10 or f12, varies by brand, check manual.

---

### Post by oldfred on 2016-11-23
Do you have UEFI turned on in UEFI/BIOS?

Do you have newest UEFI/BIOS from Asus. If system is 4 years old, vendors were often updating/fixing UEFI issues.

A lot of newer Asus have needed boot option, pci=nomsi

 Some have had to turn on CSM/Legacy boot to be able to boot USB flash drive in UEFI mode?
[http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/](http://blog.technotesdesk.com/how-to-enable-boot-from-usb-drive-in-bios-asus-zenbook/)
Asus UX303UB hardware problems - a list  15.10
[http://ubuntuforums.org/showthread.php?t=2319066](http://ubuntuforums.org/showthread.php?t=2319066)
Asus M32CD desktop - Skylake several boot parameters  pci=nomsi  i915.preliminary_hw_support=1
[http://ubuntuforums.org/showthread.php?t=2312977](http://ubuntuforums.org/showthread.php?t=2312977)
ASUS G752 Can't see SSD NVMe Needed UEFI/BIOS update
[http://ubuntuforums.org/showthread.php?t=2307273](http://ubuntuforums.org/showthread.php?t=2307273)
ASUS ROG GL552VW-CN104T
[http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters](http://askubuntu.com/questions/694453/new-laptop-skylake-cannot-boot-xubuntu-even-with-boot-parameters)
Problems Installing on ASUS F555U   needed boot option pci=nomsi
[http://ubuntuforums.org/showthread.php?t=2303665](http://ubuntuforums.org/showthread.php?t=2303665)
Asus x555u w/o pci=nomsi - space issue on drive and runaway log files filling drive
[http://ubuntuforums.org/showthread.php?t=2327103&page=3](http://ubuntuforums.org/showthread.php?t=2327103&page=3)

---

### Post by oldfred on 2016-11-23
Not sure why you are getting that message.

May be better to just turn CSM on.
 CSM - UEFI Compatibility Support Module (CSM), which emulates a BIOS mode  


And boot installer in CSM/BIOS/Legacy mode. How you boot install media is then how it installs.
If you manually with gparted add a 1 or 2MB unformatted partition and use Boot-Repair you can convert your UEFI install to CSM. It actually just uninstalls grub-efi-amd64 (UEFI) and installs grub-pc(BIOS)

---

### Post by shinobikush74 on 2016-11-23
Where do I get this "boot repair"? Just installed ubuntu on my desktop which is seven years older than my laptop with no issues. So it is not the usb boot flash drive....

---

### Post by shinobikush74 on 2016-11-23
Sorry dumb question about boot installer...read it the wrong way and being frustrated isn't helping....I refuse to give up....

---

### Post by oldfred on 2016-11-23
Boot Repair -Also handles LVM, GPT, separate /boot and UEFI dual boot.:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair) 

Old systems have BIOS only.
The new UEFI complicates it just by including backwards compatiblity. And then it added UEFI Secure Boot which Windows has on by default.
So you have three ways to boot install media, and then three ways to boot actual install. And they must match or system does not work.
So most just turn off UEFI Secure boot, then you only have two options. But if you install in UEFI mode, you must boot actual install in UEFI mode. Or if you install in BIOS boot mode you must boot install in BIOS.
UEFI will normally show two boot options for USB drive. One is UEFI:name and other is just name where name is label/brand of flash drive.
And then UEFI will have settings to boot install.

Some have Secure boot called "Windows" and "Other" where other is the CSM/Legacy/BIOS. Fine print indirectly says that as Windows 7 does not support Secure boot and it will say if using Windows 7 change setting to "Other", not Windows.
And then you may have UEFI on/off and CSM on/off or just one setting. You may not even see CSM if Secure boot is on.

---

### Post by shinobikush74 on 2016-11-23
Got a message saying partition created failed

Can you completely factory reset a laptop deleting any and all OSs?

---

### Post by oldfred on 2016-11-23
Not specifically. Your full backup of the drive or a system restore backup may do that. But if drive has some partition issue it may still fail.
My new Dell wanted a Windows backup, a Dell Backup and I also made a full backup with Macruim Reflect.

Did you at some point use Windows to change partitions. Or turn RAID settings on in UEFI/BIOS?
Post in code tags the other partition table info again.

sudo parted -l
sudo fdisk -lu
sudo gdisk -l /dev/sda

It may be just a case where running a fix from one of those tools is all that is needed.
The brute force method is a complete zero out of entire drive.

---

### Post by shinobikush74 on 2016-11-23
No..all I did was put the dvd in an install....have never tried to partition anything before...I went all in....just erased the drive and did a full install.....no problems until a few months ago when an OS update came thru and my laptop crashed....tried to re install and this is where I am now...in pc purgatory.....lol....slowly but surely becoming a software specialist....lol

The desktop is working fine.......the laptop is not and they are using the same OS, which is ubuntu studio

---

