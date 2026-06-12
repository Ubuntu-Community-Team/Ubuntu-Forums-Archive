---
title: "Ubuntu 14.04 + UEFI install problem"
date: 2015-04-17
forum: Installation &amp; Upgrades
---

### Post by Sophie_Lagace on 2015-04-17
I'm a user, not a hacker. I had an old computer that  had been running various incarnations of Ubuntu since Lucid Lynx (10.04  LTS) five years ago, but it was getting too slow for recent versions of Ubuntu so I bought a reconditioned  desktop unit:

HP Pavilion 500-314 Desktop, AMD A8-7600 Quad-Core 3.1GHz, 8GB DDR3, 2TB SATA, 802.11n, Win8.1

I used a LiveDVD  of Ubuntu 14.04.01 LTS to test, then install in dual-boot but it wouldn't boot on its own after install (I was not familiar with UEFI). I tried again to install, this time agreeing to wipe the disk. I  didn't need Windoze, after all. I researched a  bit, learned that I needed to install in EFI mode  since apparently Win8.1 would have been in UEFI. If I understand  correctly, I've compounded my error by trying to re-install, and these  would have ended up installing in BIOS, not EFI.

My question is: **How do I sort out what I messed up?** Answers in lay terms are much appreciated.

Here are the links I've explored, understanding only half:
[http://ubuntuforums.org/showthread.php?t=2147295](http://ubuntuforums.org/showthread.php?t=2147295)
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
[http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media/](http://askubuntu.com/questions/395879/how-to-create-uefi-only-bootable-usb-live-media/)&#65279;

I followed the instructions in the second link under "Installing Ubuntu Quickly and Easily via Trial and Error" and by turning off FastBoot, at least got the computer to boot from the LiveDVD rather than have to escape to BIOS and manually force it to boot. But after re-install it still won't self-boot. I ran Boot-Repair and got the following summary: [http://paste.ubuntu.com/10841217/](http://paste.ubuntu.com/10841217/)

I greatly appreciate any help I can get, but I need explained to me in lay terms.

---

### Post by oldfred on 2015-04-17
You have a full drive LVM type install. That is for advanced users or those who want full drive encryption. And LVM default install is always a full drive erase.

You have to use gparted to delete existing partitions

Unless that is what you really wanted, I would reinstall with standard partitions. And if you want Windows erase all of Ubuntu and reinstall Windows first.
But how you boot installer for both Windows & Ubuntu is how it installs either UEFI or BIOS boot.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

    
The dual boot instructions are with with Windows and you can skip those parts if only wanting Ubuntu.
 UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)

Default install is / (root) and swap, but better to have separate /home or data partition(s). But to have more than default you must use the Something Else install options. Examples above show screen shots of just about every step.

More info in link in my signature.

---

### Post by Sophie_Lagace on 2015-04-18
I used Gparted to delete the existing partitions, then used the LiveDVD to run Ubuntu and do a standard install, no LVM, encryption or options. Still won't self-boot, so I'm still doing something wrong. I took a few snapshots of the BIOS options as I have them now, perhaps this is where I goofed? 
[https://plus.google.com/photos/109519159272220299318/albums/6139144437863749425?authkey=CKrR_KuV3KuT5AE](https://plus.google.com/photos/109519159272220299318/albums/6139144437863749425?authkey=CKrR_KuV3KuT5AE)

---

### Post by oldfred on 2015-04-18
HP is one of the vendors that violate UEFI specs and require "Windows" entry to boot. If not using Windows you can rename the UEFI entry for grub or shim to read Windows.

        If Description has to be Windows then change UEFI description. Run this from live installer booted in UEFI mode.
sudo efibootmgr -c -L "Windows Boot Manager" -l "\EFI\ubuntu\shimx64.efi"

Others that dual boot with Windows, modify the hard drive boot entry in UEFI which uses /EFI/Boot/Bootx64.efi to really be grub or shim.  

Other HP users:

 HP to get into UEFI/BIOS menu - escape then f10 as soon as it starts.
[http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079](http://h10025.www1.hp.com/ewfrf/wc/document?docname=c01443329&lc=en&cc=us&dlc=en&product=5171079)
It seems hp firmware do not allow you to boot anything other than windows. Hence no ubuntu option in the UEFI. To work around it
[http://ubuntuforums.org/showthread.php?t=2227889](http://ubuntuforums.org/showthread.php?t=2227889)
1) press esc key while booting to access start up menu 2) press F9 for boot devices menu. 
[SOLVED] Trying to install Ubuntu as dual boot on Windows 8.1 desktop HP500
[http://ubuntuforums.org/showthread.php?t=2218154](http://ubuntuforums.org/showthread.php?t=2218154)
      
 HP ProBook 450 G1 Custom UEFI boot or copy to bootx64.efi
[http://forums.linuxmint.com/viewtopic.php?f=46&t=164076](http://forums.linuxmint.com/viewtopic.php?f=46&t=164076)
HP 4545s Secure boot off, manually copy files.
[http://ubuntuforums.org/showthread.php?t=2133796](http://ubuntuforums.org/showthread.php?t=2133796)
HP Manually renamed files to make it work.
[http://ubuntuforums.org/showthread.php?t=2131886](http://ubuntuforums.org/showthread.php?t=2131886)

If still issues, run Boot-Repair and post link to summary report.
      
 Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

---

