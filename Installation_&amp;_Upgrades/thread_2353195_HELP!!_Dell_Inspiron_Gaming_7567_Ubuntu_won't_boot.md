---
title: "HELP!! Dell Inspiron Gaming 7567 Ubuntu won't boot"
date: 2017-02-19
forum: Installation &amp; Upgrades
---

### Post by joshuanorman on 2017-02-19
I've tried every combination of BIOS settings I can think of, and every installation setting, and always, every time, Ubuntu from a live USB (version 14.04-17.04, Mint and even Fedora) installs seemingly fine but is never bootable. This is the newest Inspiron Gaming laptop -- 7th-Gen i7 quad core. Samsung 961 ssd. Windows seems to work fine, but neither dual nor single boot Ubuntu works. Any help would be greatly appreciated.


UPDATE: Dell bios update 1.0.5 adds AHCI support, which makes Ubuntu install like a breeze. All you need to to do is change from RAID to AHCI in the BIOS. Even Secure Boot can be left on.

---

### Post by RobGoss on 2017-02-19
Hello and welcome, You will have to give us more information that in order to help you with your issue

First, what are the specs for your machine

Brand name and model
CPU
RAM (size)
Graphics chip/card
WiFi chip/card



What version of Ubuntu are you trying to install?

What actually are you trying to do with Ubuntu install, Upgrade or what? 

If installing what methods have you already taken and how far did you get? 

The more details you can provide us with the better users can help you solve your issue

---

### Post by joshuanorman on 2017-02-19
-Dell Inspiron Gaming 15" 7567
-intel i7 quad core 7th gen (7700?)
-16GB RAM
-NVidia 1050ti
-intel wifi

I have tried 14.04, 16.04, 16.10, 17.04. But 16.04 or 16.10 would be ideal.

I'm trying to install single boot uefi, have also attempted dual boot but I don't really need windows at all. 

I've tried the automatic install, and  manually creating the partitions. Secure boot on and off. Sata disabled and ACHI. Every time the installation goes fine but won't boot after the the installation is done. I've manually specified shimx64.efi in the bios -- doesn't help. When I check the hard drive from the live USB the partitions look as expected nvme0n1p1 for efi with the boot flag, *p2 ext4 with filesystem, *p3 swap.

---

### Post by RobGoss on 2017-02-20
Well it looks like your specs are more then acceptable

Are you downloading the ISO file from Ubuntu's main website? 

Try Turing off Fast boot

If you only want Ubuntu on this machine then you can choose Erase entire disk, then when you get to the screen to choose to install Update and third party software, do not check the box to install Updates you can do this later

You may also want to check to make sure the ISO file is not corrupt something people have stated that they got a bad ISO I've never encounterd this but there's always a first time

This will help you with that

[https://www.ubuntu.com/download/how-to-verify](https://www.ubuntu.com/download/how-to-verify)

Try these suggestions and see how it goes

---

### Post by oldfred on 2017-02-20
If you have been able to install, then it may be nVidia driver.
You may need nomodeset or recovery mode to get to command line. Then install ppa and newest nVidia driver.

Probably best to use newest Ubuntu version. Older versions definitely will not work, need at least newer kernel.
Dell releases Sputnik or a set of drivers for its newest hardware. Eventually that gets incorporated into kernels, drivers, support software and then into a distribution. But that can take a while.
You may even do better with 17.04 which is not released. Do not make it you main working install until releases and consider yourself a tester. But it will have newer kernel & software.

 Dell Inspiron 7566
[https://ubuntuforums.org/showthread.php?t=2342359](https://ubuntuforums.org/showthread.php?t=2342359) 


Other Dell, while not same model issues are often common by Brand.
[https://ubuntuforums.org/showthread.php?t=2348921](https://ubuntuforums.org/showthread.php?t=2348921)
Did you have any trouble booting Windows with RAID off and AHCI on?

 Dell XPS 13 9360 Dualboot Windows 10 and Ubuntu 16.04 AHCI NVMe
[http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488](http://askubuntu.com/questions/867488/dell-xps-13-9360-dualboot-windows-10-and-ubuntu-16-04?noredirect=1#comment1344306_867488)
Ubuntu 16 on the DELL XPS15 9550 Tutorial
[https://ubuntuforums.org/showthread.php?t=2345444](https://ubuntuforums.org/showthread.php?t=2345444)
Ubuntu 16.04 on Dell Xps 15 9550 (i7-6700HQ - 1TB SSD - UHD 4k touch)
[URL="http://ubuntuforums.org/showthread.php?t=2317843"]http://ubuntuforums.org/showthread.php?t=2317843
[/URL]
 XPS 13 9350 Windows reinstall & discussion of RAID vs. AHCI
[https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/](https://www.reddit.com/r/Dell/comments/3sr1jh/windows_10_clean_install_guide/) 

               Dell XPS 8910  16.04.1 works, 16.04 did not
[https://ubuntuforums.org/showthread.php?t=2351949](https://ubuntuforums.org/showthread.php?t=2351949) 
    
 Dell support - Update on XPS 13/15 2016 Developer Edition availability
[http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9](http://en.community.dell.com/techcenter/os-applications/f/4613/t/19670562?pi22229=9)
[http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en](http://www.dell.com/support/article/ca/en/cabsdt1/SLN301754/en)
Kernel 4.6 has Dell & Alienware improvements including 9350
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Laptop-Drivers) 
    
 Dell XPS 13 Developer Edition New Kaby Lake 16.04  Sputnik 
[http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml](http://news.softpedia.com/news/dell-launches-its-new-ubuntu-powered-xps-13-developer-edition-laptop-in-us-eu-509039.shtml)
5th Generation Sputnik
[https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/](https://bartongeorge.io/2016/03/10/xps-13-developer-edition-launches-in-us-ubuntu-based-workstations-available-worldwide/)

---

### Post by joshuanorman on 2017-02-20
question-- does anyone know if FastBoot should be set to 'minimal' 'thorough' or 'auto' ? Those are the three options I have -- no option to turn it off or disable.

---

### Post by joshuanorman on 2017-02-20
Here's my most recent boot-repair output maybe that will shed some light for someone: [http://paste2.org/naFI8gtj](http://paste2.org/naFI8gtj)

---

### Post by oldfred on 2017-02-20
You need to check manual on Fast Boot settings.
You at minimum want fast boot not to be used if a full power down reboot. 
After system is fully configured, you can have fast boot on, but if major issues and you have to get into UEFI, may not have time to press a key with fast boot on.
And with one install even the grub menu will not show unless you have grub timeout slow enough that you can press escape.
My motherboard has two main settings one on cold boot, and one on reboot or warm boot. And then time to wait. 
I set both UEFI & grub to 3 sec delay which increase my boot time, but gives me a chance to get into UEFI if needed.

It looks like you did a full drive LVM install with encryption.
To reinstall grub using Boot-Repair you  have to mount & un-encrypt the LVM. In trying to mount it, Boot-Repair/mounting should ask for passphrase.
 
LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145](http://ubuntuforums.org/showthread.php?t=1586328&p=9917145#post9917145)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://wiki.archlinux.org/index.php/LVM](https://wiki.archlinux.org/index.php/LVM) 

 [http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf](http://www.intel.com/content/dam/support/us/en/documents/solid-state-drives/RSTe_NVMe_for_Linux_SW_User_Guide.pdf)

---

### Post by ashwink1295 on 2017-03-21
was this solved?? I'm planning to get this very same laptop for Deep Learning purposes

---

### Post by joshuanorman on 2017-03-27
Sorry no, I haven't been able to make it work yet

---

### Post by joshuanorman on 2017-03-27
"[COLOR=#000000]You need to check manual on Fast Boot settings."

Does this correspond to 'Minimal', '[/COLOR][COLOR=#000000]Thorough' or 'Auto'?[/COLOR]

---

### Post by oldfred on 2017-03-27
Possibly, every vendor seems to use different terms.
But all UEFI seem to have Fast Boot setting as Microsoft required vendors to make systems boot quicker. And UEFI fast boot is one of the things everyone does.

---

### Post by joshuanorman on 2017-04-05
It works!Dell bios update 1.0.5 adds AHCI support, which of course is necessary to install Ubuntu and makes Ubuntu install like a breeze. All you need to to do is change from RAID to AHCI in the BIOS. Even Secure Boot can be left on.

---

### Post by josephmanjiyil on 2017-06-01
Hi Joshua,:sad:

I tried installing the Ubuntu 17.04 on my Windows 10 pre-loaded Dell Inspiron 7567. I changed the SATA to AHCI and was able to successfully install Ubuntu 17.04 and boot it. My Inspiron 7567 came with Toshiba 512GB NVMe SSD. After installing Ubuntu, I am unable to boot into Windows 10 using AHCI in SATA mode. If I change the SATA mode to RAID On, then Windows 10 boots, but Ubuntu boot fails.

Can you please guide me, how you were able to circumvent the issue. I already have the latest BIOS version. Any help/guidance is greatly appreciated :sad:.

Regards,
Joseph M

---

### Post by oldfred on 2017-06-01
Someone posted that in Windows you have to add the AHCI driver before changing from RAID to AHCI.
Not sure how to do that.

---

### Post by josephmanjiyil on 2017-06-01
Hi All,

I was able to make it work! Like what oldfred stated, the Windows 10 should be modified to enable the AHCI for dual boot.
Here are the steps which I took to enable the dual boot of Windows 10 and Ubuntu 17.04 on SATA mode set to AHCI on NVMe SSD (Toshiba)-

    Created the Windows 10 local account before proceeding with the steps below
    Right-click the Windows Start Menu. Choose Command Prompt (Admin).
    Type this command and press ENTER: bcdedit /set {current} safeboot minimal
    Restart the computer and enter BIOS Setup (the key to press varies between systems). On Dell Inspiron it is F2.
    Change the SATA Operation mode to AHCI from either IDE or RAID.
    Save changes and exit Setup and Windows will automatically boot to Safe Mode.
    Right-click the Windows Start Menu once more. Choose Command Prompt (Admin).
    Type this command and press ENTER: bcdedit /deletevalue {current} safeboot
    Reboot once more and Windows will automatically start with AHCI drivers enabled.

Later installed the Ubuntu 17.04 from bootable usb by changing the boot sequence and disabling the secure boot option in BIOS.
It worked like a charm. I referred the link for the steps - [http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/](http://triplescomputers.com/blog/uncategorized/solution-switch-windows-10-from-raidide-to-ahci-operation/)

Thanks for the guidance

Regards,
Joseph M

---

### Post by malcaino on 2017-07-06
This is how I solved the issue.

 1.- Have the AHCI activated otherwise there is no chance to boot.
 2.- Install ubuntu normally (shrink the windows partition and leave an empty space where ubuntu will be installed, then in the installation select "Install alongside windows boot manager")
 3.- Open your bios
 4.- Go to boot order option
 5.- ADD a new UEFI
 6. Write Ubuntu, select the ssd drive, and press the button to locate a file. Here you will be exploring the content of the EFI partition and it's going to be a ubuntu folder and inside that folder you have to select the file "grubx64.efi" (I think that's the name I will dcorrect it once I'm with my pc)
 7. Accept
 8. A new UEFI record has been added under Windows boot manager. Click the Ubuntu one and move it to the first place.
 9. Apply the changes
 10. VOILA! The pc is going to boot using grub!
 11. Disable the fast boot option from Windows, cause it will delete the UEFI ubuntu record every time it boots.

That's how I'm using mine.
Cheers!

---

