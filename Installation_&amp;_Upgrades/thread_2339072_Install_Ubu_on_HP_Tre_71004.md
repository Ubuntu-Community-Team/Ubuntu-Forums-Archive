---
title: "Install Ubu on HP Tre 71004"
date: 2016-10-04
forum: Installation &amp; Upgrades
---

### Post by jamesisin on 2016-10-04
Has anyone successfully installed the latest Ubuntu on an HP Tre 71004?  I am having trouble getting my bootable installer noticed.  I can't seem to find the usual setting for disabling secure boot.  Any ideas?

---

### Post by Bucky Ball on 2016-10-04
*Thread moved to **Installation and Upgrades**.*

What is your 'bootable installer? USB or DVD?
How did you create the install media? 
Are you dual-booting with Windows?
Is Windows in hibernation? That locks the disk.

We'll need more info than you have given to provide much support. :)

---

### Post by jamesisin on 2016-10-04
I am doing a full installation of Ubu 16.04 64 bit to replace the current Win8 installation.  I have tried using an Ubu thumbdrive in addition to my usual YUMI drive.  Windows cannot be hybernating because I am booting into the EFI and making changes to the boot priority (many times).  Also, I am able to boot into the Recovery area (or whatever MS is calling it these days) and not locating the option to disable secure boot (though I get to the location where it is usually kept).

Boot order has been set (in the EFI) with both USB options above the OS boot manager.  It always boots to Windows.  Normally I would disable secure boot but this option seems to be missing.

---

### Post by Bucky Ball on 2016-10-04
You need to boot into the BIOS to change the boot order of devices or hit F12 (usually) to bring up a list of boot options at boot. Know nothing about Win recovery mode but that is not going to get you to the boot order.

To switch hibernation off in Windows you need to boot into Windows and switch it off. Nothing to do with recovery mode and the fact you can boot into recovery mode in Windows has nothing to do with it. You are trying to install Ubuntu. If your Win install is set to hibernate when you shut down it will lock the drive making it inaccessible to any other OS, not just Linux.

If you simply want to wipe Windows then there is no requirement to install in UEFI. Install however you like. It is only necessary if you are dual-booting with Win and Win is installed in EFI already.

Bottom line: the options for secureboot are in the BIOS. Nothing to do with Win recovery mode.

---

### Post by jamesisin on 2016-10-05
"Boot order has been set (in the EFI) with both USB options above the OS boot manager. It always boots to Windows. Normally I would disable secure boot but this option seems to be missing."

And here is how to disable Secure Boot:

[http://www.howtogeek.com/175641/how-to-boot-and-install-linux-on-a-uefi-pc-with-secure-boot/](http://www.howtogeek.com/175641/how-to-boot-and-install-linux-on-a-uefi-pc-with-secure-boot/)

You will see that first you select "UEFI Firmware Settings" and then are taken to a screen which has "Secure Boot Control".  I am instead taken to a screen which merely says "UEFI Firmware Settings" and "Restart to change UEFI firmware settings" and has a "Restart" button and a back arrow button.  No way to change anything.

Further down you will note that I can "Use a device".  If I run down that path and ask it to boot from an "UEFI device" I get the error "The selected boot device failed.  Press <Enter> to Continue." which suggests Secure Boot is in the way.

(All those blue background shots are from what I am calling the Recovery area.  Maybe it has a different name?)

---

### Post by Bucky Ball on 2016-10-05
> **jamesisin said:**
> If I run down that path and ask it to boot from an "UEFI device" I get the error "The selected boot device failed.  Press <Enter> to Continue." which suggests Secure Boot is in the way.

(All those blue background shots are from what I am calling the Recovery area.  Maybe it has a different name?)

Odd. Your secure boot settings must be there somewhere, though, and there must be some way of getting to it. You've also mentioned nothing whatsoever about whether you booted into Windows and switched of hibernation. You won't get anywhere if you haven't.

Try getting to the USB by hitting F12 at boot. Does that take you to a boot device menu with the USB on it and (UEFI) next to it?

---

### Post by jamesisin on 2016-10-05
I was able to boot into a fresh Ubu USB drive by choosing from the boot options (something like) "boot from an EFI file" and drilling down into the drive to locate the boot.efi file.  Once I pointed the machine (the EFI I guess) at that file it booted into the installer.  On a related note, the installer asked if I wanted to disable secure boot and (of course) I said yes.  Not sure if that matters much now that I have Ubuntu installed though.

Thanks for the effort, Bucky!

---

### Post by Bucky Ball on 2016-10-05
Great work and persistence is everything! Thanks for marking the thread as solved to help others. :)

---

