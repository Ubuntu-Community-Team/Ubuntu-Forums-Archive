---
title: "Installing from USB flash drive -- PC ignores it"
date: 2010-08-09
forum: Installation &amp; Upgrades
---

### Post by Qure on 2010-08-09
Hi,

I'm trying to install Ubuntu 10.04 - I want it to sit on another partition along with my Windows XP installation.

I don't have a blank CD handy, so I opted for the USB installation option.

I followed the very clear instructions for doing this from the Ubuntu download page ([http://www.ubuntu.com/desktop/get-ubuntu/download]("http://www.ubuntu.com/desktop/get-ubuntu/download")) - however, my PC skips straight over the USB drive and continues to boot into Windows XP.

I tried an alternative bootable USB creator (unetbootin-windows-471.exe), but it has the same result.

I have verified that the flash drive is at the top of the boot list - I can also see the name of my flash drive flash past seconds before it boots into Windows, so the PC knows its there. I have also booted into a Live version of Linux using the same PC and pen drive before, so I know booting from it is possible - I suspect the ISO is bad? Or perhaps I'm missing something completely.

I tried alternative USB ports too.

Any suggestions at all would be much appreciated,
Thanks very much!

---

### Post by davidmohammed on 2010-08-09
have you checked that your BIOS is set to boot first from removable devices?

---

### Post by efflandt on 2010-08-09
Sometimes even if you set USB first in boot order, you still need to press whatever key the BIOS splash screen shows to select boot order to boot from anything other than the hard drive.  That may be protection to avoid inadvertently booting from possibly infected CD or USB drive.  The only virus I ever caught was a boot sector virus spread by floppy disks (even accidentally booting to an infected non-system floppy).

Or if it is a USB hard drive, it may not spin up yet during quick BIOS splash (especially with Dell laptops).  So in that case you boot first and then reboot with the USB drive already connected, or change something insignificant in CMOS set up (like boot order of CD/DVD and floppy), then save (which reboots).

---

### Post by Nima1972 on 2010-08-13
Having the same issue only started in Mint 8 to create startup USB.  Used same set of instructions (with different options of course).

After entering BIOS setup the following were tried as first boot device: LS120; ZIP100; USB-FDD; USB-ZIP and even Onboard Lan.  Floppy and HARD DISK were avoided.

There are no options for USB in Boot Menu (F12).

At first it seemed the USB flash drive isn't set up properly.  Now it occurs to me that the BIOS isn't setup to boot from the USB Flash.

Any advice?  Can bios be upgraded to install from USB Flash?  

Thanks.

---

### Post by oldfred on 2010-08-13
On my computer I originally tried all those USB alternatives and none worked. But I left flash in one day and was using f12 to choose a different hard drive and there it was. Bootable flash drives were seen as hard drives not USB alternatives. Go figure.

---

### Post by Nima1972 on 2010-08-13
So it was a part of the boot menu (F12) all along or it just showed up after leaving it in for a day?

---

### Post by oldfred on 2010-08-13
It was always part of the selector for hard drives, just not USB-floppy, usb-CD, usb-zip, or any other usb device - I had a long list of devices. 

But what worked was hard drives and flash drive appeared along with sda, sdb, sdc on my system. Of course BIOS did not call them sda, sdb and I have two identical drives which sometime I have to try each to know which is really booting.

---

