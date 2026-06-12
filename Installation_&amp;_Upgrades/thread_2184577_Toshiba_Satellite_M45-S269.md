---
title: "Toshiba Satellite M45-S269"
date: 2013-10-29
forum: Installation &amp; Upgrades
---

### Post by rwhoward on 2013-10-29
I am trying to install ubuntu alongside windows XP on a 2006 Toshiba Satellite M45.  It's too old to install from USB and for some reason the DVD drive will work but can't boot from it (I've tried changing the settings in the BIOS).  Any suggestions on how to do a dual boot under these conditions would be appreciated.

Thanks!

---

### Post by mörgæs on 2013-10-30
Does it boot with a CD in the drive?

---

### Post by sudodus on 2013-10-30
> **rwhoward said:**
> I am trying to install ubuntu alongside windows XP on a 2006 Toshiba Satellite M45.  It's too old to install from USB and for some reason the DVD drive will work but can't boot from it (I've tried changing the settings in the BIOS).  Any suggestions on how to do a dual boot under these conditions would be appreciated.

Thanks!

I don't think it is too old to boot from USB. I have older computers that can do it, and my experience of Toshiba is good. Please try again! Maybe you get some tips at these links

[https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites](https://help.ubuntu.com/community/Installation/FromUSBStick#Prerequisites)
[URL="https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB"]
https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB[/URL]

---

### Post by sudodus on 2013-10-30
Please specify with more details the model

Toshiba Satellite M45-S165
Toshiba Satellite M45-S269
Toshiba Satellite M45-S331
...
or specify the

- CPU, RAM (size), graphics chip/card, number and description of USB 2 ports

The specs differ quite a lot between these models, and some of them are more likely to boot from USB.

---

### Post by rwhoward on 2013-11-11
Sorry I haven't responded.  In answer to your question, I get a note a boot that there's something wrong with the media and to check the wiring????.  Anyway it does not boot to the CD but it does recognize the drive because I can explore the CD after I open up in Windows XP.

---

### Post by linuxguru43 on 2013-11-11
You may need to upgrade your BIOS... When was the last time that was performed?

---

### Post by oldfred on 2013-11-11
Did you verify that download was correct and install to CD not copy to CD?

       [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)

 Also instructions for DVD or USB flash drive
[http://www.ubuntu.com/desktop/get-ubuntu/download](http://www.ubuntu.com/desktop/get-ubuntu/download)
Write image or burn image not copy ISO as one large file to flash or DVD.
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by rwhoward on 2013-11-11
> **sudodus said:**
> Please specify with more details the model

Toshiba Satellite M45-S165
Toshiba Satellite M45-S269
Toshiba Satellite M45-S331
...
or specify the

- CPU, RAM (size), graphics chip/card, number and description of USB 2 ports

The specs differ quite a lot between these models, and some of them are more likely to boot from USB.

***************

I have The Toshiba Satellite M45-S269.  Model PSM42U-016006.  I purchased it January 3, 2006.  I've been to BIOS and didn't see where it would have the abilty to boot from the USB drive.

Any help would be appreciated...Tx!!!!

---

### Post by rwhoward on 2013-11-11
> **linuxguru43 said:**
> You may need to upgrade your BIOS... When was the last time that was performed?

That very well could be the problem...How do I acquire the upgrade for a Toshiba Satellite M45-S269 laptop?

---

### Post by sudodus on 2013-11-12
> **rwhoward said:**
> ***************

I have The Toshiba Satellite M45-S269.  Model PSM42U-016006.  I purchased it January 3, 2006.  I've been to BIOS and didn't see where it would have the abilty to boot from the USB drive.

Any help would be appreciated...Tx!!!!

According to the specs I found it is not the earliest version. It has 3 Universal Serial Bus (USB) ports (v2.0) and I think it should be possible to boot from USB.

Boot the computer with a USB drive inserted in the computer. Check in the BIOS if it recognizes the USB drive as a hard disk drive (HDD) instead of as a USB HDD or USB device. In that case put it first in the boot order list, and reboot. See the tips in this link

[https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB](https://help.ubuntu.com/community/Installation/FromUSBStick#Booting_the_Computer_from_USB)

---

### Post by oldfred on 2013-11-12
My older Toshiba does not show the USB device unless when I boot a bootable flash drive is already plugged in. If not bootable BIOS will not show it. I normally use f12. Mine is about 1 year newer and has Intel duo core processor.

---

