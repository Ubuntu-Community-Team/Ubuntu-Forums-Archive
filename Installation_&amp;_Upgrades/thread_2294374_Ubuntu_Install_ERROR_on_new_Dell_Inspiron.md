---
title: "Ubuntu Install ERROR on new Dell Inspiron"
date: 2015-09-10
forum: Installation &amp; Upgrades
---

### Post by Gilson_Maciel on 2015-09-10
During my laptop first boot it crashed and restarted, after that it was showing the default dell recovery screen but wich didn't work.

What i did is that i've created a linux bootable usb with the 14.04.3 LTS version and booted with it and choosed the install option but i keeping getting this error:

[COLOR=#212121][FONT=Helvetica Neue]"ERROR:  This recovery media only functions on Dell and Alienware systems."

And the only option is a "Quit" button.

I've tried formatting the HDD and other partitions but still the same error occur. Any idea how can i solve this? I need this thing working!

Thank you in advance![/FONT][/COLOR]

---

### Post by Geoffrey_Arndt on 2015-09-11
That message does not sound like the wording that is found on any Ubuntu OS disk or flash-stick.   It sounds like something in the recovery partition of the hard drive.    In other words, i don't think you PC is seeing the bootable usb (disk or flashstick)?

Did you change your uefi/bios so it will boot from usb-stick first?   Is Windows still on the hard drive or did you format the whole drive?    What specific model of Dell laptop do you have?   What is your graphics chipset (like Intel or nvidia or amd/ati)?

---

### Post by chemist931 on 2015-09-12
Might have to try booting from DVD if you can't create a bootable USB.  You need a program to make a USB bootable with Ubuntu, such as [https://rufus.akeo.ie/](https://rufus.akeo.ie/).

---

### Post by Hectorcaceres on 2015-09-12
....

_________________________________________________________________________________________

Hector Dangelo Antoine Caceres

---

### Post by Gilson_Maciel on 2015-09-12
I think its some firmware conflicting. I do have the bootable USB, i can even run the ubuntu from the usb but when i try to install it i get that message. Any idea on how to solve it?

I can navigated through the HDD, i've formatted then but sill same error.

---

### Post by Hectorcaceres on 2015-09-12
......
_________________________________________________________________________________________

Hector Dangelo Antoine Caceres

---

