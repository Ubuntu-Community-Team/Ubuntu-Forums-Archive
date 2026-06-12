---
title: "How to Install linux on an ACEPC AK1 Mini PC"
date: 2018-04-18
forum: Installation &amp; Upgrades
---

### Post by eric75 on 2018-04-18
I bought an ACEPC AK1 ([https://www.iacepc.com/acepc-ak1/](https://www.iacepc.com/acepc-ak1/)) mini PC. It had W10, and 32 GB eMMC storage.


First time using a machine with eMMC. I only installed 3 programs, then allowed W10 to update. There was not enough room for the updates. Only saw about 3 GB free.


I just need one program to run for CCTV cameras, so I decided to install ubuntu. I have 16.04.3 iso mounted on a USB. In the AMI BIOS boot menu option, there was UEFI version and a non-UEFI version of the USB drive with the ubuntu iso.


I chose the non-UEFI version, booted from the drive and installed. Rebooted without USB, got errors:


PXE-E61: Media test failure, check cable
PXE-M0F: Reboot and Select proper Boot device.


Realized I did not set the eMMC to be the primary boot device. Went back to BIOS, did not see the eMMC in the boot list option.


Booted from the USB drive again -> Chose Try ubuntu -> installed and ran linux boot repair. That didn't work. Got some hints from [https://amindlost.wordpress.com/2017/10/18/acepc-ak1/](https://amindlost.wordpress.com/2017/10/18/acepc-ak1/), same machine, but he installed Mint.


Went back to the BIOS, intent to reinstall again, and try the "non-UEFI" version this time. Early into the install, I see:


"This machine's firmware has started the installer in UEFI mode but it looks like there may be existing operating systems already installed using "BIOS compatibility mode". If you continue to install Debian in UEFI mode, it might be difficult to reboot the machine into any BIOS-mode operating systems later.
If you wish to install in UEFI mode and don't care about keeping the ability to boot one of the existing systems, you have the option to force that here. If you wish to keep the option to boot an existing operating system, you should choose NOT to force UEFI installation here."


Concerning. Seems there are a lot of options to go about this.


I just want:


1 to install any flavor of Linux
2 install and run "DW Spectrum" sw: [http://digital-watchdog.com/DW_Spectrum/](http://digital-watchdog.com/DW_Spectrum/) for our security cameras.


Is this really going to be this involved? What is the best way to install some linux distro or am I better off returning it?

---

### Post by ctkocmick-y on 2018-11-09
I have an ACEPC AK1 Slice and I am running MX Linux 18 from the emmc. Installation was easy. I formatted the emmc with gparted and performed a "full disk" install. Just remember to install Grub on the "ESP" partition and not on the root partition. It boots reliably and quickly. Apparently, keeping UEFI is a requirement, so check the option in BIOS to use the EFI shell. So far, everything just works.

---

