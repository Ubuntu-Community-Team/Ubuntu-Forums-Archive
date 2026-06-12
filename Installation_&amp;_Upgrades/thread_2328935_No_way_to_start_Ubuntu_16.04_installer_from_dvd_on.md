---
title: "No way to start Ubuntu 16.04 installer from dvd on Lenovo desktop Win 8.1"
date: 2016-06-25
forum: Installation &amp; Upgrades
---

### Post by dean.w.schulze on 2016-06-25
I want to replace Windows 8.1 on my Lenovo gaming desktop.  The BIOS doesn't have an option to boot from DVD (or USB) and when I insert the DVD it doesn't auto start.  I also can't find anything on the DVD itself to make the Ubuntu installer start.

What do I do in a situation like this to start the installation process?

Thanks.

---

### Post by oldfred on 2016-06-25
If system is newer UEFI, which if Windows 8 was pre-installed then it is, you may have to turn UEFI Secure Boot off. In Secure Boot mode, booting a DVD or flash drive is considered insecure.
And you may have separate settings for allowing DVD or USB boot.
Some also do not call it UEFI Secure Boot, but just Windows or "Other". But even Windows 7 must install in "Other" as it is not secure boot.

What model Lenovo?
I think most of these are laptops, and do not know if UEFI is similar or not. Many vendors do use same UEFI across multiple models, with options turned on or off where required.
 The thermal updates were submitted today for the Linux 4.6 kernel merge window and there's a very important fix for at least some newer Lenovo laptops.
[http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates](http://www.phoronix.com/scan.php?page=news_item&px=Linux-4.6-Thermal-Updates)
Lenovo rename files
[http://ubuntuforums.org/showthread.php?t=2302170](http://ubuntuforums.org/showthread.php?t=2302170)
Lenovo Laptops there is NOVO button on left side
Lenovo S20-30 BIOS install only
[http://ubuntuforums.org/showthread.php?t=2277003](http://ubuntuforums.org/showthread.php?t=2277003)
T540 works but UEFI settings critical or it may brick
[https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1](https://docs.google.com/document/d/1hFTArhNbmpmEBRkwRg0DMbEzLBCl43F1HXoXtJ8cm0k/edit?pli=1)
Lenovo Thinkpad E531 - turn off locked boot order setting in UEFI
[http://ubuntuforums.org/showthread.php?t=2255746](http://ubuntuforums.org/showthread.php?t=2255746)
[SOLVED] Error 1962: No operating system found. Lenovo K430  only boot Ubuntu, rename files
[http://ubuntuforums.org/showthread.php?t=2243715](http://ubuntuforums.org/showthread.php?t=2243715)
Some Lenovos comes with a physical switch that enables you to select which graphics adapter to use.
 Lenovo Z510 Laptop & Ubuntu 
[http://ubuntuforums.org/showthread.php?t=2232124](http://ubuntuforums.org/showthread.php?t=2232124)

---

### Post by dean.w.schulze on 2016-06-26
This is a Lenovo desktop gaming system I got from Costco a few years back.  The BIOS says it is an IdeaCentre K430.  It came with Win 7 Home edition.

The BIOS Startup menu only has a UEFI Boot Mode item and the three choices are UEFI, Legacy, and Auto.  I chose Legacy, but there is no where in the BIOS to enable a DVD or USB boot.

So it looks like I'm stuck unless there is a way to make the system "boot" from a downloaded .iso file from Windows 8.

Any other suggestions?

Thanks.

Is there a way to manually start the installer from the DVD?  That could be what I need.

---

### Post by oldfred on 2016-06-26
You have to boot correctly configured flash drive or DVD, not ISO copy.
Installers format flash drive, extract ISO and add boot files to flash drive. Similarly they extract ISO to DVD and make it bootable.
Then you can directly boot from UEFI/CSM/BIOS boot menu. How you boot install media, UEFI or BIOS is then how it installs.

       [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
these should then work:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]https://wiki.ubuntu.com/Win32DiskImager/iso2usb

      [/URL]
 Also link on how to create a  bootable DVD or USB flash drive, Windows or Ubuntu, Min hardware requirements
[http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)
UEFI only bootable flash drive
[http://ubuntuforums.org/showthread.php?t=2299040](http://ubuntuforums.org/showthread.php?t=2299040) 
    [URL="https://wiki.ubuntu.com/Win32DiskImager/iso2usb"]
[/URL]

---

### Post by dean.w.schulze on 2016-06-26
The DVD I burned from the ubuntu-16.04-desktop-amd64.iso file looks like the attachment.  There is no autorun.inf, start.ini, or start.exe though.

Do I need a different .iso file?

I just verified that my DVD is in fact bootable (on a laptop with BIOS, not UEFI).  Apparently UEFI is a way to prevent you from installing Linux on your system.

Isn't there a way to start the installer manually from the DVD?

---

### Post by QLee on 2016-06-26
> **dean.w.schulze said:**
> 
The BIOS Startup menu only has a UEFI Boot Mode item and the three choices are UEFI, Legacy, and Auto.  I chose Legacy, but there is no where in the BIOS to enable a DVD or USB boot..

According to the user manual for K430, push F12 key while booting to get a startup device menu.

---

### Post by oldfred on 2016-06-26
You do not boot from Windows, but from UEFI.
And UEFI or one time boot key like f12 should show two boot options, one UEFI and one not UEFI or BIOS/CSM.

       Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
 [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)
Something Else or manual Install
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
Also shows Windows 8 screens or similar to Windows 10
[http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system](http://askubuntu.com/questions/221835/installing-ubuntu-on-a-pre-installed-uefi-supported-windows-8-system)
UEFI install,windows 8 with Something Else screen shots, similar for newer versions of Ubuntu
[http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html](http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html)

---

### Post by dean.w.schulze on 2016-06-26
Thanks for that.

There is an item Primary Boot Sequence (or something like that) under the Startup menu that opens another menu which is where you can change the boot device order.  I thought that was just the title for the other menu items beneath it.  Once I opened that menu I was able to change the boot order.

Sorry for the confusion.  Installation underway now.  Thanks for your help.

Installation complete, but now the system cannot boot.  It says No Operating System found.  I've tried both UEFI and Legacy in the BIOS.  Opening a new thread.

---

