---
title: "Can not boot from USB Stick if write protection enabled"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by dwvm3 on 2010-11-07
I have a USB stick with a mechanical write protection (a small switch that disables writing on the stick). I have installed Ubuntu 10.04.1 on this device usung the startup drive creator. If the switch is in the position that allows writing, Ubuntu boots as expected. But if I switch to write protection, I only see a blinking cursur. Because it is a live system on the stick I expected that it should work as well, because nothing should be written to the stick. Does anyone have an idea why it behaves like this and how I can change it?
Best regards

Dierk

---

### Post by uRock on 2010-11-07
Leave the switch on. The system has to be able to write to the log files.

---

### Post by dwvm3 on 2010-11-07
But if I burn the same image to a cd, the system is also not able to write log files and can boot.

---

### Post by uRock on 2010-11-07
The image on the CD is not the same as the files system on the thumb drive.

---

### Post by dwvm3 on 2010-11-07
yes, it is. I burned the image on a CD and I use the same image to create a bootable thumb drive.
Anyhow, is there a way to run Ubunto from a write protected usb drive ? Or is a CD the only solution?

---

### Post by uRock on 2010-11-07
The CD image is 700MB, the USB drive image is more than 2x the CD image size.

Does your BIOS even see the OS on the thumb drive when it is locked? If you set the Startup Disk Creator to discard on shutdown, then you don't have to worry about it saving user data.

---

### Post by dwvm3 on 2010-11-08
... hmm, the used space on my USB drive is 800 MB, not 1.4 GB. 
If it is possible to boot from CD, there should be a way to boot from another write protected media as well. The question is how.

---

### Post by albandy on 2010-11-08
> **dwvm3 said:**
> I have a USB stick with a mechanical write protection (a small switch that disables writing on the stick). I have installed Ubuntu 10.04.1 on this device usung the startup drive creator. If the switch is in the position that allows writing, Ubuntu boots as expected. But if I switch to write protection, I only see a blinking cursur. Because it is a live system on the stick I expected that it should work as well, because nothing should be written to the stick. Does anyone have an idea why it behaves like this and how I can change it?
Best regards

Dierk

When you make the live pendrive, select the second option: All changes will be lost. (See image attached)

---

### Post by uRock on 2010-11-08
> **uRock said:**
> [s]The CD image is 700MB, the USB drive image is more than 2x the CD image size.[/s]

Does your BIOS even see the OS on the thumb drive when it is locked? If you set the Startup Disk Creator to discard on shutdown, then you don't have to worry about it saving user data.You never answered this question. But now that you say the image is only 800MB I am guessing you did select this option when creating the bootable drive. Otherwise the image would have been closer to 2GB.

> **dwvm3 said:**
> ... hmm, the used space on my USB drive is 800 MB, not 1.4 GB. 
If it is possible to boot from CD, there should be a way to boot from another write protected media as well. The question is how.
Being you did select the discard on shutdown option, why not turn the switch on? It is obvious that the system can't read the drive to boot from it with the switch off.

---

### Post by dwvm3 on 2010-11-10
@albandy
Thank you for the hint, I tried both options, but unfortunately none of then works if the write protection is on.

@uRock
the used space on the Thumb drive is in both cases approx. 800 MB. I think what you mean is to install Ubuntu on the USB drive. If I install on the drive (not using the startup disk creator, just installing it like on a regular internal hard disk) then the used space is approx 1.4 GB.

I also tried this third option and created a RAM disk for /var and /log, but it doesn't work either (if write protection is on).

Maybe it helps if I explain the reason why I want to boot from a write protected media:

I have developed an interactive media player application that is running in a museum. The gatekeeper switches the power on in the morning and off in the evening. The Ubuntu PC is located in a position where it is not easy to access. The BIOS of the PC allows to start if external power is supplied.
From time to time, the boot process failed in the morning when the power is turned on because of a corrupted file system. Booting from a Live USB thumb drive and do fschk repairs the file system and the Computer is working well, until this happens again (approx. every 3 month).  It is not possible to do the shutdown gracefully by a cron job, because the museum has often special events and the opening hours are different in that case.
My idea was to use a write protected boot medium such as a USB thumb to protect the file system.

---

### Post by uRock on 2010-11-10
I understand where you are coming from and what you are trying to do. With the protection turned on the shutting off of the power shouldn't cause a loss of data on the thumb drive.

I am not sure what the solution to our issue would be. I've never used a lockable thumb drive.

---

