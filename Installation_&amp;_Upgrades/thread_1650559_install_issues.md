---
title: "install issues"
date: 2010-12-21
forum: Installation &amp; Upgrades
---

### Post by dennisboyer2009 on 2010-12-21
I am brand new and having problems installing ubuntu. I have burned bootable copy to dvd and trying to install to new hard drive. i cannot see rom drive in bios. where do i find a boot file for a usb? eager to learn! thanks in advance!

---

### Post by tommcd on 2010-12-21
> **dennisboyer2009 said:**
>  i cannot see rom drive in bios. 
If the CDROM drive is not seen by the computer's BIOS, then Ubuntu (or any other operating system) will not see the CDROM drive either.
Suggestions:
If the CDROM drive is IDE, set the jumper to *master*. Do not use *cable select*.
Again, if IDE, try another IDE cable if you can.
> **dennisboyer2009 said:**
> 
I have burned bootable copy to dvd and trying to install to new hard drive.
Just out of curiosity, if the CDROM drive is not seen by the computer's BIOS, how did you burn the Ubuntu iso to a DVD? Did you use a different computer? 
> **dennisboyer2009 said:**
>  
where do i find a boot file for a usb? eager to learn! thanks in advance!
To install Ubuntu from a bootable usb drive, see:
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)
There is also Unetbootin, which can be used from Windows or Linux:
[http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/)
Assuming your CDROM drive works, see this on how to properly burn the Ubuntu install iso to a CD or DVD:
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)
Be sure to burn the CD / DVD at the slowest possible speed. Then run the option to *Check CD for Defects* when you boot from the CD to be sure the CD is good.
Write back if you need more help.

And welcome to the Ubuntu forums!

---

