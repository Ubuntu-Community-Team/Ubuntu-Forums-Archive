---
title: "[SOLVED] install OS on external usb harddrive"
date: 2008-07-30
forum: Installation &amp; Upgrades
---

### Post by johnn1949 on 2008-07-30
This is probably a crazy idea,but is there any way to install an operating system on an external usb hard drive from a laptop that has a dead internal hard drive?

---

### Post by logos34 on 2008-07-30
sure, as long as your Bios supports booting USB devices.  

Start the installation...if the internal is dead it won't be recognized, and the installer will write Grub bootloader to the mbr of the usb drive.  Then set the Bios to boot from the external drive.

---

### Post by bobnutfield on 2008-07-30
It's not at all a crazy idea and it is done all the time.  But, you will have to make sure that the laptop can boot from the USB port.  Most 5 years old or younger can.  If it cannot, you can still do it with a floppy, if it has one.  To check whether or not it can boot from the USB port, go into the BIOS and check.  One further note, Puppy linux, which is a Live CD distro, will install to a USB drive and you can install there with the cd.

---

### Post by logos34 on 2008-07-30
> **bobnutfield said:**
> If it cannot, you can still do it with a floppy, if it has one.

If you're thinking of something like SmartBootManager boot floppy, it won't work--it's only good for booting from older non-bootable internal cdroms.  (usb modules are too big to fit on floppy).  That said, John1949 could use the internal cdrom to boot external drive if Bios does not support it.  

[https://help.ubuntu.com/community/BootFromUSB](https://help.ubuntu.com/community/BootFromUSB)
(-->'[Booting the kernel from a bootable CD]("https://help.ubuntu.com/community/BootFromUSB#Booting%20the%20kernel%20from%20a%20bootable%20CD")')

---

### Post by bobnutfield on 2008-07-30
> If you're thinking of something like SmartBootManager boot floppy, it won't work--it's only good for booting from older non-bootable internal cdroms. (usb modules are too big to fit on floppy). That said, John1949 could use the internal cdrom to boot external drive if Bios does not support i

Good point, thanks for reminding me...I should have known that up front because I tried to do just that with an old Toshiba laptop and couldn't.

Apologies to the OP for incorrect information.

---

### Post by johnn1949 on 2008-07-30
Hey, thanks.  I'll check out the usb boot.

---

### Post by confused57 on 2008-07-30
If you can't boot from USB, you might be able to click on the "Advanced" button and select to install grub to floppy or (fd0)?
Then you "should" be able to boot the USB drive from the floppy...if it works, which I haven't tried this, you may want to make several copies of the boot floppy(due to the failure rate of floppies).

---

