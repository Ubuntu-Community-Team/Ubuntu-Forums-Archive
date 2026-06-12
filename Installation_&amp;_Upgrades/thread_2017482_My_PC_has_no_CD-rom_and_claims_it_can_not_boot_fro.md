---
title: "My PC has no CD-rom and claims it can not boot from USB."
date: 2012-07-05
forum: Installation &amp; Upgrades
---

### Post by Ulvdatter on 2012-07-05
My PC has no CD-rom and claims it can not boot from USB, -is there a way I can get Ubuntu tonight?

I have one of these Eee-mini PC's, and I've been thinking I should buy one of these external CD-roms that you can conntect by USB, but I never got round to it. Now I am very regretful and far away from the posibility of geting my hands on one.

So, is there any way I can sneak Ubuntu on to my PC under these circumstances?

):P

---

### Post by msammels on 2012-07-05
When you try to boot from USB, what happens?

---

### Post by Ulvdatter on 2012-07-05
Boot from USB is not an option in the boot menu. I've tried "removable device" wich was what sounded closest to correct, but with no success. (It just boots from hdd and flashes the windows logo, as usual.)

---

### Post by CharlesA on 2012-07-05
I have seen machines lump usb drives under "hard drives"

Both in the BIOS and in the boot menu.

---

### Post by Ulvdatter on 2012-07-05
In my boot-menu the options are: removable device, hdd and dvd-rom (the DVD-rom does not exist in RL). I' tried to put all three of them on top of the list, with disapointing results. My knowledge about BIOS is limited to a truck stop resturant in rural Norway that is called Bios....

---

### Post by efflandt on 2012-07-05
Boot order in CMOS setup might only allow specific selection from devices connected at that time.  Putting a general class like removable devices first might be ignored if no such device existed when set.

I know that with Dell computers you usually have to press 12 to select booting from removable media.

Have you tried pressing the hot key to select boot device from BIOS splash screen during boot to see what that lists?

For my tablet PC (with attachable keyboard) I had to change a CMOS setting for the BIOS splash screen to even show up or display "F12 - select boot device".  I did buy a USB DVD writer, but have not used it yet.  I installed Ubuntu to SD in the tablet's card slot from bootable iso on USB memory stick.

---

### Post by Ulvdatter on 2012-07-05
All right, I don't understand 100% of what you are saying, but I get the general idea. I've got to run of and do analogue stuff for a while, but I'm going to try this out later on. 
Thanks so far!

To be continued...

---

### Post by Rex Bouwense on 2012-07-05
I have an EeePC as well and ASUS does lump the USB flash drive with the hard drive as CharlesA has already stated.  Insert the flash drive and press the power switch.  When prompted press F2 for set up.  Navigate to boot and press enter.  Navigate to hard drive which should have a + sign before it.  Press enter and you will see your flash drive.  Change the order for the flash drive to boot first.  Save your settings (F10 I think) and exit.  That should get you booting from the USB flash drive.

---

### Post by Ulvdatter on 2012-07-06
Hi again!
I'm happy to tell you that it worked, and I'm now a happy Linux user again. 
Thanx to everybody for interest and support, and special thanx to CharlesA for puting me on the right track. (I kept strugling with the removable devices, when it was in fact listed under hdd all along)

Ulvdatter

---

### Post by CharlesA on 2012-07-06
> **Ulvdatter said:**
> Hi again!
I'm happy to tell you that it worked, and I'm now a happy Linux user again. 
Thanx to everybody for interest and support, and special thanx to CharlesA for puting me on the right track. (I kept strugling with the removable devices, when it was in fact listed under hdd all along)

Ulvdatter
Glad you got it working. :)

---

