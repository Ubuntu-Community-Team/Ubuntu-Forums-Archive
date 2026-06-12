---
title: "Installation of Ubuntu 11.10 halts with HP Z400"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by lmlahti on 2012-01-11
I am installing Ubuntu 11.10 on HP Z400 Desktop, to replace reinstalled Windows. The installation starts and prints log messages on the screen but soon halts at the point: '4.425137 generic/usb 9993:046D:C077.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:001d.2-2/input0'. The cursos blinks but the installation never seems to proceed beyond this point. Ctrl-alt-del restarts the machine. I also tried 11.04 and 32-bit version but got the same problem.

Any tips on how to get forward?

---

### Post by adityamagadi on 2012-01-11
if u r installing with windows already present, first run wubi in windows it automatically reboots then select ur boot device as ur ubuntu DVD . this shud solve ur problem.
also select the option as "install ubuntu along side windows" n give ubuntu atleast 50gb space. let me know if this solved ur problem :)

---

### Post by lmlahti on 2012-01-11
No success. I installed with Ubuntu Wubi and restarted. I selected Ubuntu from the OS menu. It get stuck on the same message than previously. I tried to boot from hard disk (after Wubi installation) both with CD in and CD out.

---

### Post by lmlahti on 2012-01-11
Ok, above I clicked on wubi file on installation CD. Now I also tried to directly download Wubi installer at Ubuntu website. The installation starts but does not seem to proceed from '[155.557430] type=1400 audit(1326285026.350:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=6962 comm="apparmor_parser"'. 

Any tips on how to get forward? Or is this operation supposed to take a long time (>30min)?

---

### Post by adityamagadi on 2012-01-11
it doesnt take more than 20min to install... the only other reason for this is ur iso image either not burnt properly or the iso image is corrupted.. try burning the iso image at the slowest speed possible , if this also doesnt work download the iso file again... instead wasting cd's u can use a pendrive(usb stick) n install from it.

---

### Post by lmlahti on 2012-01-11
Thanks. I have tried with four installation files on four separate CDs (32/64 bit, 11.04/11.10). None of them gets the installation done.

---

### Post by lmlahti on 2012-01-11
I have now also tried with Ubuntu and Xubuntu Wubi without CD, directly from hard disk. Neither of them goes through, either. I am surprised since HP Z400 is 'certified' for Ubuntu 11.10 according to Ubuntu website.

---

### Post by lmlahti on 2012-01-13
I now updated the Z400 BIOS to the newest version (3.54) from HP website and ran Ubuntu Wubi (11.10) from Ubuntu website. Now the installation halts at the following point: 

[172.837456] type=1400 audit(1326446711.843:12): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=6970 comm="apparmor_parser"

Any further tips on how to proceed? The SUSE and RedHat installation CDs from HP website do not even boot from CD while Ubuntu does.

---

### Post by adityamagadi on 2012-01-13
this is peculiar does your laptop have enough hardware to support ubuntu 11.10?.

---

### Post by lmlahti on 2012-01-13
This is a Z400 workstation aimed at computational science work and it certainly has sufficient hardware power. No default options were removed from the order, and Z400 has been certified for Ubuntu 11.10 so I assume that the hardware should have all necessary components to run Ubuntu.

---

### Post by adityamagadi on 2012-01-13
in your boot menu set ACPI=off and try to install.

---

### Post by lmlahti on 2012-01-13
The problem persists after setting from BIOS Power Menu: 

ACPI S3 P2S Mouse Wake Up -> Disable

This is the only ACPI option which was enabled in the BIOS menu.

The installation still halts at the same point as previously (generic/usb 9993:046D:C077.0002: input,hidraw1: USB HID v1.11 Mouse [Logitech USB Optical Mouse] on usb-0000:001d.2-2/input0).

---

### Post by lmlahti on 2012-01-25
Hi community, I was finally able to install Ubuntu 11.10 64-bit on HP Z400 after setting ACPI=off from the F6 menu, which is available on the Ubuntu installation startup screen (which has the alternatives to try without installing, install, etc.). There are some ACPI setting also in BIOS, where I first tried to tune them, so I was confused.

Now I will keep fingers crossed that there are no more problems with the installation. At least to start with everything runs smoothly.

---

