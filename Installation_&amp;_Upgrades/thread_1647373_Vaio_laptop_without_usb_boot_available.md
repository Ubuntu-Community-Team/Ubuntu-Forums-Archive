---
title: "Vaio laptop without usb boot available"
date: 2010-12-17
forum: Installation &amp; Upgrades
---

### Post by grey1beard on 2010-12-17
I've just acquired a Vaio PCG-FX801 with Phoenix bios version R0121K5.
In the boot order, it lists "+Removable Devices", but on expanding the menu, only gives "Legacy Floppy Drives".
I only discovered this after unsuccessfully trying to boot from a stick with the 10.10 netbook iso on it.

Is it possible to get round this, or should I put the iso on a cd, or should I download the desktop iso onto a cd, and use that ?

I want to try it out on this laptop before installing it.

MITA
John

---

### Post by grey1beard on 2010-12-17
I've just tried copying the usb version onto a cd, only to discover it's about 120 Mb too big :(
So it looks like a new download is the only way to go, but which version ?
John

---

### Post by BlueSpecial on 2010-12-17
> **grey1beard said:**
> I've just acquired a Vaio PCG-FX801 with Phoenix bios version R0121K5.
In the boot order, it lists "+Removable Devices", but on expanding the menu, only gives "Legacy Floppy Drives".
I only discovered this after unsuccessfully trying to boot from a stick with the 10.10 netbook iso on it.

Is it possible to get round this, or should I put the iso on a cd, or should I download the desktop iso onto a cd, and use that ?

I want to try it out on this laptop before installing it.

MITA
John

I assume that when you say "stick with the 10.10 netbook iso" you refer to having extracted the iso to the stick... not placing the ISO file directly onto the stick right? The same question for the CD... did you burn the ISO to the CD?

Sometimes USB drives are listed under "Hard Drives" units.. which have the local disk and any usb disk attached.... did you try to check it out on the "Hard Drive" instead of "Removable Devices"?

---

### Post by grey1beard on 2010-12-17
I used the instructions on 
[http://www.ubuntu.com/netbook/get-ubuntu/download](http://www.ubuntu.com/netbook/get-ubuntu/download)
to create the bootable usb, so I assumed it was the correct version that was installed.
Certainly checking the contents of the stick in windows showed it as an install version, not just an iso.

Re the hard drive entry, that only lists the named hdd that is present, nothing else.
John
PS not sure about the cd as I was tripped up by the size !

---

### Post by grey1beard on 2010-12-17
OK
I've downloaded the netbook to cd version and that is booting up now.
At least the splash screen has appeared.
I'll post this solved when it's actually running ;)

John

---

### Post by BlueSpecial on 2010-12-17
> **grey1beard said:**
> 

Re the hard drive entry, that only lists the named hdd that is present, nothing else.


Do you have Legacy USB Support enabled on BIOS?

---

### Post by grey1beard on 2010-12-17
> **BlueSpecial said:**
> Do you have Legacy USB Support enabled on BIOS?
Is this a setting elsewhere in the Bios ?
The only place legacy is mentioned is in the removable devices - floppy drive !
John

---

### Post by grey1beard on 2011-01-05
All is sweetness and light. 10.10 is installed, and a wireless card plugged into the slot was instantly recognised.
So now SWMBO is finally getting connected and doesn't need to read the news over my shoulder.  ;)
John

---

### Post by jaythedogg on 2011-01-05
Just a quick note, my sister's netbook didn't have "boot from USB" but had removable drives & no option for USB, BUT when you plug in the USB *then* power on, it may show up in removable devices. It did for us anyway.

Hope this helps for any future peeps!

---

