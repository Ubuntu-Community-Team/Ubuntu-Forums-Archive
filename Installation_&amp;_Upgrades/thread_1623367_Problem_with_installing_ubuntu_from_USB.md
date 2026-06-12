---
title: "Problem with installing ubuntu from USB"
date: 2010-11-16
forum: Installation &amp; Upgrades
---

### Post by luckyvictor on 2010-11-16
Hi all

I downloaded the latest ubuntun, and used universal usb installer to create the USB ubuntu disk on a 1GB USB stick.

I rebooted and selected USB to be the first in boot order, although it did detect my USB, it never went into the installation process, instead, the cursor was just blinking.

so what is the problem please?

---

### Post by C.S.Cameron on 2010-11-16
First check your MD5SUM of the downloaded iso.

---

### Post by luckyvictor on 2010-11-17
MD5 Check sum are the same, result from winMd5Sum

---

### Post by sikander3786 on 2010-11-17
> the cursor was just blinking.


We actually can't be sure if your computer is even trying to boot from the USB.

Start pressing any key as soon as the computer gets past the Bios screen until you see a menu with Try or Install options. Check disc for defects. If ok, try some boot options like acpi=of, noapic etc.

[https://help.ubuntu.com/community/LiveCDBootOptions](https://help.ubuntu.com/community/LiveCDBootOptions)

---

### Post by luckyvictor on 2010-11-17
I only know that the computer does detect my USB, because I put USB to be the first in my boot order, and when there is no USB connected, the cursor blinks for a couple seconds then go straight into Windows 7.

However, if I inserted the ubuntu install usb, the cursor will stay there forever, in fact, I did a little search in the forum and 'looks like' booting from ubuntu USB will take quite a long time, is it true?

---

### Post by sikander3786 on 2010-11-17
No, on an average machine it takes less than 5 min.

Can you try with some other USB drive?

---

### Post by luckyvictor on 2010-11-17
I can try borrow a bigger size USB from my frd, would you think that 1GB is too small??

btw, in the universal usb installer, there is an option, persistent, what is it? do I need it?

---

### Post by sikander3786 on 2010-11-17
1 GB will be enough to create a Live USB.

No, you don't need a persistent install. It is meant to save your changes/data in the Live session while you only intend to use that Live USB for installation.

Using some other USB creation tool might also help.

[http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by rowanq on 2010-11-17
One gig should be plenty of space.

The Persistence option allows you to make changes while you are inside the live-usb environment and have them remain after a reboot.

You really only need this if you plan on using the live-usb as a portable OS and like to have something other than the default settings.

Rowan

---

### Post by luckyvictor on 2010-11-17
I will try using this, [http://unetbootin.sourceforge.net](http://unetbootin.sourceforge.net)

and will let you guys know what's going on.

thanks for all the helps

---

### Post by luckyvictor on 2010-11-17
ok, I have tried another usb installer, same thing, it just loaded the USB, but stayed there forever, with the cursor blinking

---

### Post by C.S.Cameron on 2010-11-17
Can you try your flash drive in a second machine?

---

### Post by luckyvictor on 2010-11-18
I will try get someone's computer to try, and also try using another USB if I can borrow one.

---

