---
title: "Boot from USB problem/ setting up dual boot"
date: 2015-08-03
forum: Installation &amp; Upgrades
---

### Post by Pedele on 2015-08-03
Hello,  I'd like to dual boot Ubuntu and Windows on my Lenovo Z500 laptop ( Intel core i5, 4 GB RAM, Win 8.1). But before doing any partitions I'm just trying to get to the try ubuntu function to see if the USB will even work.  

My main problem is that the USB doesn't boot properly. I boots up to the loading screen, starts flashing and then restarts and does the same thing over and over again until I plug the USB out and it says " System doesn't have any USB boot option. Please select other boot option in Boot Manager Menu."  
I've disabled fast boot and secure boot and USB boot is enabled.

  I'm not very experienced at this so if there are some really good instructions how to set up dual boot on a system like mine it would be really helpful if you could post me a link.

  I'd appreciate any help. Thanks.

---

### Post by oldfred on 2015-08-03
Is this Window 8 or later that is UEFI or older and BIOS based?
If i5 processor, hardware system is probably UEFI, but some have Windows in BIOS boot mode.

If UEFI you may have to go into UEFI and change settings to allow booting in UEFI mode from flash drive. It may let you boot in CSM/Legacy/BIOS mode, but if Windows is UEFI you want UEFI for Ubuntu.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Also shows Windows 8 screens
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-windows-8-64-bit-system-uefi-supported)
UEFI install,windows 8 with Something Else screen shots
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)
Linux on UEFI: A Quick Installation Guide
[http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/)

If not sure what UEFI or BIOS are, definitions are at end of link in my signature.

---

### Post by Pedele on 2015-08-03
Yes its Windows 8.1 and it is UEFI

Is there any way to make sure the USB works before doing any major changes?
And will I be able to update to windows 10 afterwards?

---

### Post by Pedele on 2015-08-03
So I've followed the instructions from the third guide and my USB still doesn't boot.

---

### Post by oldfred on 2015-08-03
If you have turned off secure boot in UEFI and changed settings to allow USB boot, it should work if flash drive/ISO correctly created.

Did you confirm that ISO was downloaded correctly?
       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

Which of the many tools to create bootable flash drives did you use.
Some seem to work better than others. Or even some flash drives work better than others.
       
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)

    

 Usb installer from Windows - pendrive may not work with UEFI
[http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)
Rufus Create bootable USB drives the easy way  From Windows create Linux installer
[http://rufus.akeo.ie/](http://rufus.akeo.ie/)

I have also seen that if you only want UEFI boot (thats all you need), then you can use any extraction tool to extract ISO to the preformatted FAT32 partition with the boot flag on flash drive.

UEFI expects to find /EFI/Boot/bootx64.efi on an ESP - efi system partition. Which is a FAT32 partition with the boot flag if created with gparted or parted. Or set active if created with Windows.

The Ubuntu installer is preconfigured with the /EFI/Boot/Bootx64.efi for UEFI boot. But the typical installer also adds code to MBR, boot files & configuration for BIOS boot.

---

### Post by Pedele on 2015-08-03
I confirmed that ISO was correct.
I used Universal USB installer.
I tried Rufus with the GPT partition scheme for UEFI just now and it didn't work either.
I tried extracting ISO before but that also didn't work.

---

### Post by oldfred on 2015-08-03
Probably a setting in UEFI.

Other Lenovo, often UEFI is similar across models. Is your UEFI the most current version from Lenovo?

 T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)

---

### Post by Pedele on 2015-08-03
Yeah, I've updated yesterday to the latest version available though for some reason it was called BIOS update not UEFI update or anything like that.

Also, in UEFI settings I don't have very many options:
Wireless LAN                  [enabled]
SATA Controller Mode      [AHCI]
Graphic Device               [switchable graphics]
PXE Boot to LAN             [enabled]
Power Beep                    [disabled]
Intel Virtual technology    [disabled]
BIOS Back Flash              [disabled]
Deep Sleep                    [disabled]
Hotkey Mode                  [disabled]
Secure Boot                   [disabled]
Boot Mode                     [UEFI]
USB Boot                       [Enabled]

That's like every choice I can make.

---

### Post by oldfred on 2015-08-03
As near as I can tell that looks good?

Just to see if it boots try BIOS/CSM/Legacy boot mode. 
You can even install in CSM mode and use Boot-Repair to convert to UEFI. It uninstalls grub-pc(BIOS) and installs grub-efi-amd64(UEFI).

---

### Post by Pedele on 2015-08-04
I made new bootable usb again to work in both modes.
Set Boot Mode [Legacy Support]
Boot Priority [UEFI First]
Then can still choose to boot from EFI USB Device.
Other options are SATA HDD, SATA ODD and Network Boot.
So I chose the usb again and i don't know what happened... laptop just froze on loading, usb is on. So it is different than usually everything flashing and restarting over and over again. But after waiting a few minutes nothing changed.

---

### Post by oldfred on 2015-08-04
I see in specs you have nVidia. Are you using nomodeset?

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by Pedele on 2015-08-04
Yes I have a graphics card.
I had no idea what nomodeset was.
I don't really understand how to open this grub menu.
When I boot my laptop there's only black screen for 1 sec, then loading screen and then windows.

---

### Post by oldfred on 2015-08-04
It seems like it is just not booting flash drive at all.
Some flash drives or certain ports on system make a difference. Have you tried all USB ports?

       pendrive speed tests USB2 & USB3 various brands - user sudodus
[http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085](http://ubuntuforums.org/showthread.php?t=2196858&p=12907085#post12907085)
Includes links to speed tests and lists some that do not work well.
[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)

---

### Post by Pedele on 2015-08-04
Yeah the flash drive might be the case. It's 2 GB big, several years old, really cheap.
I've tried all the ports but it didn't make any difference, I have both USB 2 and USB 3 ports.

---

### Post by oldfred on 2015-08-04
I have used MicroCenter's own house brand flash drives for years and they have always worked. May not be fastest?

I have my own issue, the MicroCenter is only a few miles away, so every time I would go to store, flash drives were lower in cost, or now USB3 flash drive is same or lower in cost than previous USB2. I try not to go to store too often as I already have many flash drives for backup, booting & repair ISO.

---

### Post by Pedele on 2015-08-04
Yeah this one I actually got for free and otherwise works fine. Speed also didn't make any difference because all I carried on it was some pdfs, powerpoints, word docs and python programs. 

Someone on amazon posted a review saying it was a breeze to dual boot linux on this and I'm just spending forever trying to figure this out...

Should I maybe try to boot a DVD instead or something? I don't know if that's more reliable or not nor if a laptop can even boot DVDs.

---

### Post by oldfred on 2015-08-04
If you have a DVD, it should be bootable. 
I just prefer flash drives as they are a bit faster & reusable for next install.

But some systems just are not as easy to install.

One Lenovo user did post this on DVD issues:
 > Lenovo's  buggy EFI Bios is will not boot from a DVD at all unless you enable 'legacy' (which you can't do because it screws with Windows 8!)
 The work around was to turn ON 'Legacy' boot mode in the BIOS and turn OFF "secure-boot" mode from locking out Ubuntu), and also make sure to turn OFF 'Legacy' SATA AHCI to ATA.
Then I installed Ubuntu from a USB stick (because these settings would only boot the Ubuntu installer from USB, but not DVD). 

---

