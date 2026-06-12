---
title: "Cannot Boot From USB On Windows Tablet"
date: 2014-12-10
forum: Installation &amp; Upgrades
---

### Post by Kale_Freemon on 2014-12-10
As the title suggests, I am having trouble booting Ubuntu 14.04 from USB on my Windows 8 tablet. I can use the USB as a Windows 8 recovery drive and boot from that just fine, but when I try to boot from Ubuntu, the tablet tells me that the system does not have a usb boot option. Secure boot is already disabled, and USB boot is enabled in the firmware settings. I already checked on another machine and the drive is indeed bootable.

Is there any other way to get Ubuntu to boot on this tablet from USB?

---

### Post by grahammechanical on 2014-12-10
I do not have any practical experience on this matter but as I understand things there are two basic types of Windows tablet. One type uses an ARM designed CPU which the standard Ubuntu 14.04 image would be incompatible with as it is for the Intel/AMD x86 CPUs.

> **Windows RT is an edition of [Windows 8]("http://en.wikipedia.org/wiki/Windows_8") designed for [mobile devices]("http://en.wikipedia.org/wiki/Mobile_device") that use [32-bit ARM architecture]("http://en.wikipedia.org/wiki/ARMv7") (ARMv7).[SUP][[3]]("http://en.wikipedia.org/wiki/Windows_RT#cite_note-The_Windows_RT_Review-3")[/SUP] Microsoft intended for devices with Windows RT to take advantage of the architecture's power efficiency to allow for longer battery life, **

[http://en.wikipedia.org/wiki/Windows_RT](http://en.wikipedia.org/wiki/Windows_RT)

Secure boot should not be the issue. But a boot system (UEFI) that has been set up to only allow a Microsoft OS to run is a possibility. Those who know more about this than I do will need lots more information about that device.

Regards.

---

### Post by Kale_Freemon on 2014-12-10
It's definitely not RT. It sports a quad core Atom processor.

Here's the link: [http://www.walmart.com/ip/Nextbook-10.1-Intel-Quad-Core-2-In-1-Detachable-Windows-8.1-Tablet/39092206](http://www.walmart.com/ip/Nextbook-10.1-Intel-Quad-Core-2-In-1-Detachable-Windows-8.1-Tablet/39092206)

If it has been set up to only allow a Microsoft OS to run on it, then that kinda sucks. Granted, 8.1 works just fine on it. I just wanted to see what Ubuntu would be like on a tablet.

---

### Post by guitarman89i-u on 2015-02-05
I too have this nextbook and have been trying to boot via the micro sd slot figured that would be the most useful way to duel boot but so far i cant navigate to the proper drive to boot it. anyone know if there is a way to adjust the bios setting to allow the micro sd slot to be a bootable opt?

---

### Post by oldfred on 2015-02-06
The systems that modify UEFI to only boot Windows are using the description to control booting. And that is not the UEFI standard.

But when you boot an external device you are booting /EFI/Boot/bootx64.efi. That is a device boot which does not indicate what files you really are booting. And that file is in the Ubuntu installer.

---

