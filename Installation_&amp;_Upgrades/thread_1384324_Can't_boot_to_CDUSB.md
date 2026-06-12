---
title: "Can't boot to CD/USB"
date: 2010-01-18
forum: Installation &amp; Upgrades
---

### Post by LykkeLamaen on 2010-01-18
Hi

I'm trying to install Ubuntu 9.10 on my old Toshiba Protege m300. The problem is that there's no internal CD drive, so I'm forced to use an external cardbus cd-drive. And I cannot get the bootloader to boot from it. And using an usb pendrive is the same problem. I used unetbootin to create a bootable usb but it didn't work either.

I just want to get a clean install, so i want to wipe windows completely. I tried Wubi, and it worked, but I want to install Ubuntu properly. 

Any ideas on what to do?

---

### Post by phillw on 2010-01-18
Hi,
 the first thing to check is your boot order in BIOS - You have to be quick, on boot to catch this, often it is Press F2, or esc - That will pop you over to BIOS - look for 'Startup Disk' - or words to that effect. You'll have to look at what options there are. If you have the option of USB-(Hard) Drive that seems to work the most. Else - play with the various USB options until it works !! - Make sure the USB device is the **first** boot device, else the system will always look to your internal hard disk.

/edit - you may see an option for cardbus cd-drive  in there - It's a case of having a look at the options available.

Regards,

Phill.

---

### Post by LykkeLamaen on 2010-01-18
Okay. I found my way into the BIOS and I can change the boot order. But when i change it to CD-ROM i doesn't work. And there is no USB option. 

Can I install from a floppy?

---

### Post by phillw on 2010-01-18
Hi,

when you switch to USB, does it attempt to load the CD?
I'm just wondering if the CD is okay - If you have another computer, you can check it - Boot from the CD (You'll possibly have to alter the BIOS) and select 'Check the CD' to ensure it has burned okay.

I'll go have a dig for floppy booting.

/edit - I think this what you need :-)  --> [http://edivad.wordpress.com/2009/12/21/install-ubuntu-9-10-via-floppy/](http://edivad.wordpress.com/2009/12/21/install-ubuntu-9-10-via-floppy/)

Regards,

Phill.

---

### Post by LykkeLamaen on 2010-01-18
Thanks a lot! 

The link you gave me helped a lot. I'm trying right now, and it might just work. The boot process froze a few times but after reading some more I found out that by holding SHIFT you force it to use USB 1.1 and now its booting :-)

Thanks again

---

