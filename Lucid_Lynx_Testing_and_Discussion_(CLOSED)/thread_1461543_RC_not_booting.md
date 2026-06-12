---
title: "RC not booting"
date: 2010-04-24
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by schmolch on 2010-04-24
After Beta1 and Beta2, RC still does not boot on my amd/nvidia Desktop
I chose expert-mode with nomodesetting and after a crapload of IO-Errors the kernel panics.

I am booting from a Live-usb stick which works fine on another machine.

How do I file a bug about this?

---

### Post by Unicast on 2010-04-24
No love here either with the RC.

I get the Ubuntu boot splash with the 5 red dots and then the screen blanks out and the CD spins down and it just sits there. Same with nomodeset.

Wondering if there's something with the latest kernal -20 boots on my setup when I did a dist-upgrade from beta2, but -21 dies in the same way that the RC does.

---

### Post by Unicast on 2010-04-24
Just had to update grub2 to change the default kernel to -20-generic on Lucid where I did a dist-upgrade from beta2.


At least I have a working system - no idea what's going on with the RC iso.

---

### Post by dino99 on 2010-04-24
> **schmolch said:**
> After Beta1 and Beta2, RC still does not boot on my amd/nvidia Desktop
I chose expert-mode with nomodesetting and after a crapload of IO-Errors the kernel panics.

I am booting from a Live-usb stick which works fine on another machine.

How do I file a bug about this?

ha ha Lucid installer have found your stupid avatar :lolflag:

---

### Post by schmolch on 2010-04-24
So how do i file a bug from a system that does not even boot?

---

### Post by WishMaster on 2010-04-24
Same here...

Doesn't boot on laptop, nor on desktop...

_Laptop_: Pentium-M 1,4 Ghz - 512 MB RAM (2 x 256) - Intel i855GM chipset 400 MHz FSB with integrated graphics - 15" TFT display designed for 1400x1050 with 1 ext. VGA port - Broadcom 4401 10/100 Ethernet Card - Intel PRO/Wireless 2100 802.11b card

_Desktop_: _CPU:_ [COLOR=Gray]INTEL CORE i5 750 45nm (2.66)[/COLOR] - _RAM:_  [COLOR=Gray]PATRIOT 4GB  1333Mhz DDR3[/COLOR] - _PSU:_ [COLOR=Gray]CORSAIR VX550W[/COLOR] - _Graphic:_[COLOR=Gray]  Radeon HD 5750 1024MB GDDR5[/COLOR] - _Monitor:_ [COLOR=Gray]SAMSUNG  P2350 Black 23 inch 1920X1080[/COLOR] -  _Wireless:_ [COLOR=Gray]LINKSYS WMP600N-EU Wireless-N Dual Band PCI Adapter

[COLOR=Black]Ubuntu fails to boot when monitor is connected through DVI. It accepts only analog cable to boot.[/COLOR]
[/COLOR]

---

### Post by keithpeter on 2010-04-24
Hello All

Lucid RC live CD pops up a little alert box and reports that the 'installer has crashed' after reaching the purple haze background, so past the Ubuntu logo with the dots, but before the drum sound and the Gnome bars appear. Doesn't matter if I press the space bar when the keyboard and stick person is displayed or if I let it time out. Beta 2 booted to live CD ok.

Alternate install CD boots fine and I've installed from that CD.

Lenovo T42: 1400 by 1050, 1 Gb ram, 1.7GHz centrino chip set, ATI graphics.

So how do we find out what is happening and what information can we give the bug squashers? This make of laptop is cheap to buy reconditioned in the UK.

---

### Post by schmolch on 2010-04-25
bump

---

### Post by VMC on 2010-04-25
> **schmolch said:**
> So how do i file a bug from a system that does not even boot?

Before you file a bug report you have to know whee the problems lays.

Have you removed "quite" linux boot string? If so what error messages do you see.

edit: also I don't know about why your getting those IO errors. You might do a *fsck* on the partition in question using the livecd.

---

### Post by schmolch on 2010-04-25
> **VMC said:**
> Before you file a bug report you have to know whee the problems lays.

Have you removed "quite" linux boot string? If so what error messages do you see.

edit: also I don't know about why your getting those IO errors. You might do a *fsck* on the partition in question using the livecd.

yes i removed quiet, otherwise i would see nothing.
I get those IO-Errors when i boot from the rc-live-usb-stick.
the stick works fine on other machines.

btw. i filed a bug already.

---

### Post by schmolch on 2010-04-25
marked as solved.
i/io errors had been caused by the usb-hub and the failed boots by my shitty bios.

---

### Post by schmolch on 2010-04-25
marked as solved.
i/io errors had been caused by the usb-hub and the failed boots by my shitty bios.

---

