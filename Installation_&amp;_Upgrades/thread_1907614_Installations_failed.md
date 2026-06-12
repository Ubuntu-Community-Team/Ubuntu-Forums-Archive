---
title: "Installations failed"
date: 2012-01-11
forum: Installation &amp; Upgrades
---

### Post by Jhaemes on 2012-01-11
Hi, built a pc earlier today and got around to installing an OS.

I've tried to install Zorin via usb stick. The stick itself is fine, checked the sum and that. Initially I thought kernel error, so I got the Lite version. I can't install that either.

Basically, I hit f12 for the boot menu, then usb=zip, get a gray screen, then a black screen with white text that ends with the error about failed handling.

I can get to the boot menu for the OS, but no matter which option I choose I get nothing.

---

### Post by IWantFroyo on 2012-01-11
Try using the "nomodeset" and "acpi=off" booting parameters. You should be able to get to them from the boot screen (typically you can), although I've never used Zorin OS in my life.

---

### Post by Jhaemes on 2012-01-11
How do I do that?

I don't have a boot screen, only the Zorin blue installer thing.

---

### Post by IWantFroyo on 2012-01-11
Hit the "ESC" key. You should get several menus at the bottom of the screen accessible by the function keys at the top of your keyboard, and a language selector. (going off of my non-Zorin-OS knowledge)

It should be F6. Hit "Enter" over nomodeset and acpi=off.

Edit: Well, hit the "ESC" key while the "Zorin blue thing" is up.

---

### Post by Jhaemes on 2012-01-11
I can get a black screen saying boot: when I hit esc on the Zorin light screen.

Anything I type gets "could not find kernel image"

---

### Post by IWantFroyo on 2012-01-11
That's not what it's supposed to be showing.

Maybe Zorin doesn't support GRUB? That's what regulates those settings to my knowledge.

Does anything other than Zorin work? It's possible that since it's a new computer, it's a hardware error and some part isn't getting enough electricity or something.

---

### Post by Jhaemes on 2012-01-12
I haven't tried any other OS.

Specs are : i3 2100, Gigabyte Z68-P, OCZ 700w ModXStream PSU, GTX 550 Ti superclocked, 300gb hard drive (bought new), 160gb hard drive, sony dvd-rw.

I was looking into trying a different OS, but Zorin had all the features I wanted, mainly plenty of windows compatibility.

---

### Post by Jhaemes on 2012-01-12
Sorry for bumping, but I'm getting desperate here...

I downloaded then made a boot from usb using Lili, of the latest Ubuntu. Got it all going, got to splash then installed it, it said restart which I did. I can get to a purple splash screen, but when I pick Ubuntu it just goes to a blank, black screen.

---

