---
title: "Boot installation Ubuntu 12.10 and newer version"
date: 2013-02-21
forum: Installation &amp; Upgrades
---

### Post by takeit on 2013-02-21
I have dual boot on laptop HP Pavilion dv6-2040ev, Ubuntu 12.04LTS 64bit and Win7 Home 64bit, my problem is that I can't install any other newer version of ubuntu in the laptop 12.10 or 13.04 (have tried the beta version) 32 or 64bit. I have tried all the ways boot CD, USB 32 and 64bit, even that they boot and start the installation on other computer (I have a desktop computer) on my laptop I get a blank screen (with a cursor on top left corner) and nothing works.... I can only power down the computer with the power button.
Is there any way that my laptop is not compatible with the newer versions? or is it locket in some way ??
Thanks for your help.

[COLOR=DarkRed]My laptop specs  AMD Turion II Ultra Dual-Core Mobile M600 2.4Ghz, RAM 4GB DDR2, WiFi Atheros AR9285,VGA ATI Mobility Radeon HD 4530-512MB, Monitor LED 15,6'' 1366X768.[/COLOR]

---

### Post by grahammechanical on 2013-02-21
Can you run a live session? Try this

1) at the first purple screen press Enter
2) at the next screen press enter (sets English as the default language). Otherwise select another language
3) at the Try - Install screen press f6
4) scroll down the menu and select nomodeset and press Enter
5) Press Esc to close the menu
6) Press Enter to select the Try Ubuntu option and see if a live session loads.

Regards.

---

### Post by takeit on 2013-02-24
I have tried to boot from a USB Flash with Ubuntu 12.10 64bit (again) and I got this screen [http://imageshack.us/photo/my-images/842/hp1sn.jpg/](http://imageshack.us/photo/my-images/842/hp1sn.jpg/) while it was trying to start the installation.
I have test the nomodeset and nothing works, but I have selected the ACPI=off and it worked! The live session loads and works fine, I installed the Ubuntu 12.10 64bit on a 16GB Flash drive and it worked ... but after the first boot it has stopped and I got the same screen like above.
Can I disable the ACPI permanently?
Thanks for the help!

---

### Post by MAFoElffen on 2013-02-24
Following those same instructions for the LiveCD... after you press F6, then <esc>... A bootline will appear on the bottom. After the characters "--", add a space then add:
```

Single --verbose

```
That should boot the kernel to text tty session and ask for a login. That would confirm the the kernel can boot or not...

From your photo, it was hanging at the kernel boot while it was probing the CPU. It may be that you don't have a good Ubuntu LiveCD ISO image on your USB device. Other's are running those versions of Ubuntu with no problem booting so I suspect that first.

If it got further than that, I would have suspected the ATI graphics... But it didn't get that far. (By your photo.)

EDIT-- Never mind the above... I saw the APCI=off reference... Go to my Grapahics Sticky link in my sig line, the first post and look down about 2/3rds into it for making the grub menu change (added parameters to bootline) permanent... There will be instructions there.

---

### Post by MAFoElffen on 2013-02-24
> **istealth shadow said:**
> IF THAT STILL does not work, go into your bios and reset it. its okay, it will do nothing its just correcting anything thats wrong. then try again and boot into the DVD.

If that still doesn't work. try wubi.
istealth- 
Look 3 posts up... and the edit on my post. 

We both overposted the OP before reading his last post...

The OP found an ACPI related fix and can now boot... I steered him to instructions to make that permanent.

Although- he could play with that further to tune that to another kind of fix besides completely turning off ACPI... 
one of which would be to try "acpi_osi=Linux"...

ACPI handles IRQ, backlight and such... so it could be debugged to turn off or adjust to just what the specific ACPI problem is... But more work involved.

---

### Post by MAFoElffen on 2013-02-24
> **istealth shadow said:**
> i don't know what ACPI is...

ACPI stands for/is the abbreviation for the **A**dvanced **C**onfiguraton and **P**ower **I**nterface.

---

### Post by takeit on 2013-02-25
> **istealth shadow said:**
> go into windows, type  partition in the start menu then press enter. then format the ubuntu partion. (save data first from ubuntu). then download imgburn from [http://www.imgburn.com/](http://www.imgburn.com/). its free so no crap.

then install imgburn then download a fresh x64 ubuntu 12.10 iso from [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

then open imgburn and click write image file to disk. select your iso then on the burn screen DESELECT ALL CHECK BOXES. then insert a blank DVD and burn it to the dvd.

then reboot, then boot into the dvd and install ubuntu :D

I have burned many DVD's in low speed and nothing worked.  I haven't tried with imgburn (I have it but I usual use nero) I will give it a try but I don't thing it will work. I have used DVD that are actually working in other computers!

---

### Post by takeit on 2013-02-25
> **istealth shadow said:**
> IF THAT STILL does not work, go into your bios and reset it. its okay, it will do nothing its just correcting anything thats wrong. then try again and boot into the DVD.

If that still doesn't work. try wubi.
I have tried this too, I even have flash the BIOS many times from the first BIOS version to the last one, nothing worked :(

---

### Post by takeit on 2013-02-25
> **MAFoElffen said:**
> istealth- 
Look 3 posts up... and the edit on my post. 

We both overposted the OP before reading his last post...

The OP found an ACPI related fix and can now boot... I steered him to instructions to make that permanent.

Although- he could play with that further to tune that to another kind of fix besides completely turning off ACPI... 
one of which would be to try "acpi_osi=Linux"...

ACPI handles IRQ, backlight and such... so it could be debugged to turn off or adjust to just what the specific ACPI problem is... But more work involved.
I will try this  "acpi_osi=Linux" (I have to do it in the same way I was trying with "ACPI=off"), is this correct ?

---

### Post by takeit on 2013-02-25
One more thing when I have used the "ACPI=off" it was working, booting in Ubuntu, but the WiFi was not working....:mad:

---

