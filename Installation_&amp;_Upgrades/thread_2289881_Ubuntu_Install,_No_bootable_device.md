---
title: "Ubuntu Install, No bootable device"
date: 2015-08-07
forum: Installation &amp; Upgrades
---

### Post by j.arland on 2015-08-07
I am trying to install Ubuntu on my HP G62 laptop. I booted up my computer and installed ubuntu with a flash drive. When I restart the computer I get a black screen that says "No bootable device -- insert boot disk and press any key". I tried to run boot repair but to no avail. Here is the link to the report it gave me. Anyone have any ideas how to fix?
[http://paste.ubuntu.com/12024357/](http://paste.ubuntu.com/12024357/)

---

### Post by grahammechanical on 2015-08-07
I do have one idea of what to check.

To boot the computer from a USB memory stick we have to enter the UEFI boot system and direct the motherboard to boot from the USB stick and not the hard disk. Aftwards we have to go back into the UEFI to direct the motherboard to look to the hard disk for an OS and not look to the USB port for an OS. Or go into UEFI boot system to set up a boot order. Such as, USB first and if not present then hard drive.

Regards.

---

### Post by j.arland on 2015-08-08
Thanks for the tip, but I am trying to run the installed version off of my hard drive, not boot from the USB, which works fine.

---

### Post by yancek on 2015-08-08
You have Grub code in the master boot record of the hard drive looking for the core.img file needed to boot.  As you can see, the message states the file can't be found.  If you are using MBR with GPT format, you need a small BIOS boot partition which you don't seem to have.  Additionally, sda1 your first partition is an EFI partition used when booting UEFI/GPT which does contain efi files for Ubuntu and windows.  Mixing these two methods leads to problems as you have seen.  Is your BIOS using UEFI or MBR to boot?

---

