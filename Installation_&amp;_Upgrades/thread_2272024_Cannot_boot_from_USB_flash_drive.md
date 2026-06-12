---
title: "Cannot boot from USB flash drive"
date: 2015-04-03
forum: Installation &amp; Upgrades
---

### Post by Rex Bouwense on 2015-04-03
I download Lubuntu 14.04.2, checked the hash, and used unetbootin to create a bootable flash drive.  However,it will not boot.  I am aware of the bug [https://bugs.launchpad.net/unetbootin/+bug/1190256](https://bugs.launchpad.net/unetbootin/+bug/1190256) but none of the work arounds seem to work.  My computer is an ASUS EeePC 1000h and has no optical drives.  Any ideas on how I can get it to boot so I can install 14.04.2.

oops.  I forgot to include the error code:
Failed to load libutil.c32
Failed to load COM32 file menu.c32

---

### Post by Dennis N on 2015-04-03
Hi Rex,

I have see those same errors too. I then resort to another option to create the usb installer. I successfully made my 14.04.2 installer from the unetbootin in 14.04. Making it from 14.10 didn't work and may have been when I got those errors. 

I have also used the dd method successfully a couple of times - especially if you want a UEFI bootup. I did my dd copy from the command line to transfer the iso. There is also a mkusb tool that helps with that:

[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)

but I have not yet tried this tool. 

I always reformat the FAT32 partition on the USB I intend to use before using it. 

That's about it.

---

### Post by mateojonsonguynn on 2015-04-03
I wouldn't use unetbootin.
It apparently has lots of problems after a quick search.
I would instead use another program like Startup Disk Creator (if you are trying to install the iso from a Linux computer) or Linux Live USB Creator (if you are trying to install the iso from a Windows computer).

Check this out: [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by Rex Bouwense on 2015-04-03
Thanks for the information guys.  Since there is always more than one way to skin a cat I used Startup Disk Creator to create a bootable flash drive and booted and reinstalled from it.  I had always used unetbootin and never had a problem before.  I haven't given up on Unetbootin.  I will just wait until the bug is patched.

---

