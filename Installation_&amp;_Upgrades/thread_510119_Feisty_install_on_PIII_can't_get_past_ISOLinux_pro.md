---
title: "Feisty install on PIII can't get past ISO/Linux prompt"
date: 2007-07-26
forum: Installation &amp; Upgrades
---

### Post by rbm0307 on 2007-07-26
Trying to install Ubuntu Feisty on an older Pentium III computer but running into a problem.

Environment:  Tekram P5MVP-A4 motherboard, Intel 450MHz Pentium III Socket 7 processor, 512MB RAM, 40GB IDE HD (IDE0 master), IDE CDR/CDROM (IDE0 slave), Nvidia 64MB graphics card, 3Com 10/100 network adapter.

The box was previously running Win98 no problems.  Pulled the disk and installed a new 40GB HD.  Tried booting Ubuntu 7.04 but gets stuck right after displaying the ISO/Linux banner.  Same thing happens for Ubuntu Edgy.  I've tried both the desktop and server versions of the LiveCD.  In addition, I've tried another CDROM but experience the same problem.

Could this problem be related to the configuration of the IDE devices?  Should the CDROM be on a separate IDE interface (haven't tried this for lack of a cable at the moment)?

Any other suggestions?  Thanks.

- Robert.

---

### Post by az on 2007-07-26
I doubt this is an Ubuntu problem, but a hardware problem.

Is your new hard drive properly configured in the BIOS?  Sometimes, you need to make the motherboard autodetect the ide devices once.  Are you sure both devices are not set the same (both jumpered for master, for example?)  If that's not the issue, you can try setting them to cableselect.

I would reset the bios to default values and then make sure everytying was properly detected.  

Another through;  I once had problems with a computer acting funny after I had installed a new hard disk.  I had plugged the ide cable upside down (it had no groove which only allows you to put it in the correct way).  Check that the red stripe is next to pin 1 on the MotherBoard and that the red stripe is facing you on the drive.

---

### Post by rbm0307 on 2007-07-27
az,
I agree...I think it is a hardware problem as well.

Tried your suggestions but no success.  I found another IDE cable and plugged the HDD in IDE0, CDROM in IDE1 so that they don't interfere.  The cables are plugged in properly as well.   I reset BIOS options to their defaults and set disk detection to AUTO.  The disk is found and set mode 4, LBA, 40GB. Yet,  the boot still hangs at the ISO/Linux prompt.  I even replaced the new HDD with the original HDD with the same results. I've played with other BIOS options such as memory timing and AGP video aperture but no joy.

Maybe CDROM booting is just not supported in this BIOS so it looks like I have to try a floppy boot (if that is even possible).

If anyone else can think of anything more I should try, pipe in please.

- Robert.

---

### Post by Pumalite on 2007-07-27
'Maybe CDROM booting is just not supported in this BIOS'

Is it or isn't? Do you have a place in BIOS to set the Boot order and if yes; can you set the CDROM as first?

---

### Post by rbm0307 on 2007-07-27
Yes, there is an option to select boot order in the BIOS _and_ CDROM is one of the selectable items _and_ the Uuntu LiveCD is booting.  But still CDROM booting is failing extremely early in the boot sequence.  I also just verified that the BIOS at the version I'm operating supports HDDs up to 64GB large which encompasses my 40GB drive size.

I'm just thinking that a network install will be easier than repairing this apparent HW problem since I've tried everything that I can think of in the BIOS and HW domains to get this to work.  Maybe network install will succeed.

- Robert.

---

### Post by Pumalite on 2007-07-27
...

---

### Post by dhopley on 2007-07-29
I have a similar configuration but cannot get any of the LiveCDs to boot . However the alternate 7.04 CD has worked fine . On my Windows 98 I always needed to use a floppy to install the CD drivers before invoking the Windows 98 set up CD and I think it might be a similar problem with Ubuntu on the LiveCDs . I have searched in vain for an equivalent to the 98SE boot floppy which would boot and allow me to pass control to the CD . The SBM.BIN floppy refuses to show my IDE/HDD CDROM in it's boot menu list so the lack of recognition of the CD drive is not solved .  I would love to know what the difference is which allows the alternate CD to steam away no problem !

---

