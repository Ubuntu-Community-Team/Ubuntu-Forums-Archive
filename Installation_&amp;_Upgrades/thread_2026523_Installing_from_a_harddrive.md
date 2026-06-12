---
title: "Installing from a harddrive?"
date: 2012-07-15
forum: Installation &amp; Upgrades
---

### Post by Romanrp on 2012-07-15
My laptop currently has Ubuntu 10.04, and I want to upgrade to 12.04.
I want to do a fresh install, however the cd drive on my laptop doesn't seem to be working.
I have tried booting from USB, that didn't work either.
And yes, I have changed the bios boot parameters, there is no problem with that.

So is there anything else I can try?

---

### Post by OM55 on 2012-07-15
When you say that "Booting from USB did not work" can you be more specific and describe what you did and what happened?
Notice that there are two kinds of USB bootable devices, the USB Key and the USB Drive. If you are using a regular USB dongle, it could be formatted to either option. In the BIOS settings, some BIOSes recognize only the USB Drive ( = USB HDD) while others will have both kinds. It is possible that your BIOS either does not recognize the USB Key, while that is how your USB dongle formatted, or that you did not bring that option to be first in the boot order.

A good utility to format the USB dongle as USB HDD is unetbootin (you can install it from the Software Center or: sudo apt-get install unetbootin

If all that fails, you can also purchase an external USB CD drive (quite cheap) and install from a CD this way.

---

### Post by z3nhakr on 2012-07-15
how did you set up your usb? the startup disk creator that comes pre-installed on ubuntu has always worked for me. as OM55 said you a usb HDD is more likely to be supported.

---

### Post by coldraven on 2012-07-15
I just install from a 1GB SD card after using  Unetbootin to copy the .iso
You can't get much cheaper than that :)

I'm lucky to have an SD card slot on my laptop but it should work from a $1 card reader.

---

### Post by pqwoerituytrueiwoq on 2012-07-15
why 11.04 that is a little outdated since 12.04 is out
did you try your boot menu from the bios (not your grub menu)

---

### Post by Romanrp on 2012-07-15
I used an 8GB USB key.
I used Lili USB creator, and when that didn't work, I used Universal-USB-Installer. (Both on Windows 7).

And when I put it in, literally nothing happened.

I disabled the boot from harddrive in the BIOS, so it could only boot from the USB stick, but when I did that it told me that no boot media was found.

The same when I used a CD.



> **pqwoerituytrueiwoq said:**
> why 11.04 that is a little outdated since 12.04 is out
did you try your boot menu from the bios (not your grub menu)

Sorry it was a typo, I meant 12.04.

EDIT: I tried making a bootable USB stick using startup disk creator, didn't work.
I will try unetbootin  next.

---

### Post by z3nhakr on 2012-07-15
> **Romanrp said:**
> I used an 8GB USB key.
I used Lili USB creator, and when that didn't work, I used Universal-USB-Installer. (Both on Windows 7).

And when I put it in, literally nothing happened.

I disabled the boot from harddrive in the BIOS, so it could only boot from the USB stick, but when I did that it told me that no boot media was found.

The same when I used a CD.





Sorry it was a typo, I meant 12.04.

is boot from usb a visible option in your bios? what model pc are you installing on?

---

### Post by Romanrp on 2012-07-15
> **z3nhakr said:**
> is boot from usb a visible option in your bios? what model pc are you installing on?

It doesn't specifically 'USB device' just 'removable device'.
And it is an Asus K50IN.

---

### Post by sudodus on 2012-07-15
Sometimes the USB drive (HDD or flash) is recognized as one of the hard disk drives, so you need to go the page in the bios menu, where you change the boot order among the 'hard disk drives'.

By the way, is your CD drive working, when you try to read from a regular audio disk or a data disk?

---

### Post by OM55 on 2012-07-15
One more thing to remember: When you boot to get to the BIOS settings, you HAVE to have the USB key plugged in or otherwise many BIOSes will not show its option on the boot list.

---

### Post by sudodus on 2012-07-16
> **OM55 said:**
> One more thing to remember: When you boot to get to the BIOS settings, you HAVE to have the USB key plugged in or otherwise many BIOSes will not show its option on the boot list.
+1
This is important, but easy to forget when giving advice

---

### Post by Romanrp on 2012-07-16
> **sudodus said:**
> Sometimes the USB drive (HDD or flash) is recognized as one of the hard disk drives, so you need to go the page in the bios menu, where you change the boot order among the 'hard disk drives'.

By the way, is your CD drive working, when you try to read from a regular audio disk or a data disk?

Thank you, this did it, I changed the boot order among the hard drives, and I am installing 12.04 as we speak.

Thanks for the help everyone :)

---

### Post by sudodus on 2012-07-16
> **Romanrp said:**
> Thank you, this did it, I changed the boot order among the hard drives, and I am installing 12.04 as we speak.

Thanks for the help everyone :)
I'm glad to help :-)

If you have more questions on the way, please come back, otherwise click on **Thread Tools** at the top of this page and mark this thread as SOLVED

---

