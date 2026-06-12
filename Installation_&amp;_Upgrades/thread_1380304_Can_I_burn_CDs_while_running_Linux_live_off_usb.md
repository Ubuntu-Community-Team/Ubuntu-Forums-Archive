---
title: "Can I burn CDs while running Linux live off usb?"
date: 2010-01-13
forum: Installation &amp; Upgrades
---

### Post by azitizz on 2010-01-13
Ive been trying to burn a new iso image of Ubuntu 9.04 to reinstall grub for 9.10. Im currently running 9.10 off a usb, I try and write a cd off brasero but when Im ready to burn the cd it says theres only 1.7 MB or something available on the empty cd or DVD. I Imagine his has something to do with the fact its only a 4 GB usb stick and its trying to use that as a cashe? I dont know just talking out of my a**. Im still figuring things out.
If theres a way to burn a CD and get around the limitation Braseros giving me I would love to know. Im in a bit of corner as far as my options to be able to reboot with a new OS. My wondows is not showing up in the boot either so Im stuck using the live CD/USB for now.
The computer crashed when I tried to go ahead and burn the CD regardless of what it said about space. Seemed like a bad Idea now.
Thanks
I do have an SD card which Im not sure I can actually make into a boot drive but I would be willing to try.

---

### Post by ajgreeny on 2010-01-13
I suppose it's just possible that the 4GB size of the usb drive could be having this effect, but I have not heard of it before, and I would not have expected the usb system to try and put everything into cache before burning either.

Are you sure that the CD-R is not already used as a multi-session burned CD, with just a few MB free?  What shows on the desktop when you put the disk into the drive and wait for the system to find it; does it show Blank CD-R Disc, which my system does?

Your SD card, by the way, will be no different to the usb drive you are using at present; it's just another usb drive to the system, I think.

---

### Post by kayvortex on 2010-01-13
I wouldn't have expected Ubuntu running off a USB to cause any problems with burning CD images. Follow what ajgreeny says. You could also try burning it with cdrecord, which is a command-line program. There's some info on how to do that somewhere in this forum or in the help docs.
Backup suggestion: if you have a windows CD, then you can fix your MBR, boot windows, burn an Ubuntu iso in windows and then reinstall grub.

Bear in mind that 9.04 uses legacy grub and 9.10 uses grub 2, though: make sure you know what these two are and what you're doing. If you don't know, then ask and we'll be happy to explain.

---

