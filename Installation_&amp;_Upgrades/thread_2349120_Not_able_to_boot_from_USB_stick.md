---
title: "Not able to boot from USB stick"
date: 2017-01-11
forum: Installation &amp; Upgrades
---

### Post by ssreddy555 on 2017-01-11
My Lenovo laptop & another desktop are unable to boot from a Sandisk Cruizer Blade 8 GB USB stick with Kubuntu 16.04.1 LTS.

No other files on it. 

Don't know why USB stick method doesn't work as consistently as the disk for live or installation.

Yes, I have set the priority of BIOS boot options correctly.

---

### Post by RobGoss on 2017-01-11
Depending on what machine your using it might be choosing the correct F-key most machine use the F-12 key on startup to boot from a USB drive

I know you mentioned your using a levono computer so you might have to refer to the owners manual or do a Google search to find the correct key

---

### Post by oldfred on 2017-01-11
Some users have issues with one installer, but another works.
And some have issues with one flash drive but another works.

What installer did you use to create USB flash drive?
What model Lenovo system are you installing. Is it older BIOS or newer UEFI?

 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
Also:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

---

### Post by ssreddy555 on 2017-01-12
At first, I have used unetbootin but failed to boot. Then I have used the native USB installer provided with Ubuntu 16.04. This also failed. I have installed Ubuntu in another Lenovo machine with the same USB stick. The BIOS is UEFI but set to legacy.
The model of LENOVO is G 50.

---

### Post by oldfred on 2017-01-12
If system is UEFI better to have UEFI on and legacy off. Although some systems need legacy on, but still let you boot in UEFI mode. Most only boot and install in Legacy mode with Legacy on.

Also in UEFI you may need to have Secure boot off. You may have it off already if you turned on legacy boot.
But you may also have to allow USB flash drive boot or other USB settings to let it work.

Possibly similar Lenovo. UEFI/BIOS is usually the same or similar by vendor with only slight differences base on options for different models.
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

### Post by sudodus on 2017-01-12
The native USB installer provided with Ubuntu 16.04, Ubuntu Startup Disk Creator, clones the iso file, and it is a reliable method.

I have good experiences of Sandisk Cruizer Blades (4GB and 16 GB) for booting.

I have also good experiences with old and middle age Lenovos. But I don't know about new models, but sometimes new models with UEFI are tricky to boot. I found this information about which hotkey to use to reach a boot menu and the UEFI/BIOS setup:

Boot menu:	fn+F12 or power on by pressing «OneKey Recovery button»
Bios setup:	fn+F2 or power on by pressing «OneKey Recovery button»

according to

[http://boot-keys.org/notebook/lenovo/g50/](http://boot-keys.org/notebook/lenovo/g50/)

---

### Post by ssreddy555 on 2017-01-12
There's no problem reaching the boot menu, which I  did already & set the priority to boot from USB.

---

### Post by sudodus on 2017-01-13
Please describe with as many details as possible what you do when trying to boot from the USB drive, and what happens (what you see and what you hear, everything that can be relevant to identify and solve the problem.

---

### Post by ssreddy555 on 2017-01-13
I followed the standard procedure. 
Seems booting from a USB stick may not succeed every time. 
I have succeeded in booting a Ubuntu 16.04 iso image using the same USB stick and with the same machine. 
It didn't work with Kubuntu & Mint latest editions. 
Reading through these forums, USB stick method doesn't appear to be as reliable as booting through DVD.
So, I will go the DVD way. 
Thank u all the responders.

---

