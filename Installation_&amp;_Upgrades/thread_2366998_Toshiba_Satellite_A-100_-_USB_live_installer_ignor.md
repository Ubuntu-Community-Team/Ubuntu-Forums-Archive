---
title: "Toshiba Satellite A-100 - USB live installer ignored"
date: 2017-07-24
forum: Installation &amp; Upgrades
---

### Post by M_Mynaardt on 2017-07-24
Hi!


I wanted to try a live install of Lubuntu 17.04 on an old warhorse of a laptop.
It's a Toshiba Satellite A100.  It is old, and a 32 bit machine.
But made to last.  Living by "waste not want not", I wanted to see how it does running Lubuntu on it.


I got to the BIOS to switch the boot order.  Which was easy enough.
That's when things started looking a  bit odd.


Instead of showing something like "Kingston Data Traveller" for my USB stick, all I saw was "USB Memory".
So, I put that at the top of the boot order.
Then the USB stick was ignored and it went straight to booting up off the old OS (Peppermint 7) off the driver.


I also tried live installs from USB sticks with both antiX 16.1 and Mint 18.2 Xfce.
Same result each time; the USB stick is ignored for the lot.


I'm not sure if the hard drive in this Toshiba is relevant or not.
The hard drive is a Kingston 120 GB solid state drive.
I popped that in because the old HDD was failing.


Can anyone tell me if this might be a hardware issue specific to this older 32 bit computer having an SSD?
Or maybe if it's a GRUB issue?


Thanks in advance!

---

### Post by Autodave on 2017-07-24
If that machine has a DVD drive, I would try that.

Did you put the install file on the USB as a .iso file? (You cannot simply copy the file onto the stick. Same goes for putting it on a DV D disc.)

If no internal DVD, do you have access to an external USB one? (I have had to resort to that a couple of times.)

---

### Post by BenginM on 2017-07-24
Salutations!

well , if it failed also booting with other ditro it seems like it's not the usb faults .. isn' there a function key for this model to boot from usb!

a web search results to this :

[https://forum.toshiba.eu/showthread.php?17504-Boot-from-USB-on-Satellite-Pro-A100](https://forum.toshiba.eu/showthread.php?17504-Boot-from-USB-on-Satellite-Pro-A100)

---

### Post by sudodus on 2017-07-25
If the machine has a CD drive (but not a DVD drive), you can try to chainload from a Plop CD to the USB drive. See this link,

[https://www.plop.at/en/bootmanagers.html](https://www.plop.at/en/bootmanagers.html)

---

### Post by M_Mynaardt on 2017-08-03
> **Autodave said:**
> If that machine has a DVD drive, I would try that.

Did you put the install file on the USB as a .iso file? (You cannot simply copy the file onto the stick. Same goes for putting it on a DV D disc.)

If no internal DVD, do you have access to an external USB one? (I have had to resort to that a couple of times.)

Hi there!

Sorry I'm a bit slow responding.

I used UNetbootin to create the pen drives I tried.
Never had a problem with that before on this computer, though.

Someone suggested I try booting another computer with these live installs.
I can boot another computer with it, but not the Toshiba.

That's why I was wondering if it might be a grub or hardware issue.

---

### Post by M_Mynaardt on 2017-08-03
> **sudodus said:**
> If the machine has a CD drive (but not a DVD drive), you can try to chainload from a Plop CD to the USB drive. See this link,

[https://www.plop.at/en/bootmanagers.html](https://www.plop.at/en/bootmanagers.html)

Hi there!

I haven't tried to boot the computer from a CD or DVD.
I try to avoid that, so I'm not wasting CDs for a one-off.

I'll try the other suggestions from that link when I get home.

But, as I told Autodave, the same USB sticks that won't boot the Toshiba will boot another computer.
Now that I think of it; the Toshiba BIOS boot order only showed "USB Memory" as an option.
But the other computer I tried (a Samsung N150) showed "USB HDD (brand name)" as a boot option in BIOS.

Even though the Samsung is a 64 bit machine, I definitely created a 32 bit version with UNetbootin.

---

### Post by Rex Bouwense on 2017-08-05
Look in the BIOS and see if the flash drive is listed under hard drives.  If it is move it to the top.  Some laptops recognize the data stick as an additional hard drive.  I have an old Dell that does so.

---

