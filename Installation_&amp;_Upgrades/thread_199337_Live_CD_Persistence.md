---
title: "Live CD Persistence"
date: 2006-06-18
forum: Installation &amp; Upgrades
---

### Post by JackRazz on 2006-06-18
I'm trying to get the Persistence feature of Live CD working and I'm getting an error  at boot up.  I formatted a USB memory stick according to the wiki.  I'm getting 'Buffer I/O error on device hdc' on block 36734.  First some details.  My PC is a Windows XP PC with all NTFS basic partitions.  I'm guessing that hdc is drive 0, first partition, which is  a NTFS partition.

What could be wrong?  I've tried adding 'ide=reverse' to the boot up options along with persistent.  Does the bios need to recognize the usb stick as a boot drive or emulate a floppy?  I Looking forward to trying out ubuntu with the persistence feature.

Thanks - JackRazz

---

### Post by catlett on 2006-06-18
hdc is your 3rd hard drive. Your first hard drive is hda, second is hdb and third is hdc. In most systems hdc is your cd rom device. Kind of how it is usually E in windows. C and D are the first 2 hard drives and E and F are the next. But usually you have a cd rom connected to the second ide controller and not a hard drive.

So I would gues your live cd is no good. If you know how to run md5sum checks then do one to confirm or deny. If you don't, reburn the iso at 4x speed to cut down on the risk of a bad or corrupted burn.

---

### Post by JackRazz on 2006-06-19
catlett, thanks for the speedy reply.  This is good news as its a fairly simple solution.  I'll check out the iso and if needed, redownload it.

I'll let you know here how it turns out.

JackRazz

---

### Post by JackRazz on 2006-06-19
catlett,
Didn't work.  I checked the md5, which was good.  Then re-burned with nero at 8x with finalize and verify options turned on.  The Live CD works fine: I went through all the apps and they load up just fine.  It's late here in Houston, so I'll check the usb stick instructions tomorrow.

Your right in that I have 2 hard drives and the cd drive is hdc.  No floppy drive.  nForce motherboard with bios treating a USB stick as a hard drive.  I might try disabling this or at least leave the usb stick in and boot up without persistance and see if the usb stick is in the Administration/Disk applet.

I can't think of anything else relavent, but I'll check back tomorrow after thinking on it.  I'm still hoping on getting it working.

JackRazz

---

