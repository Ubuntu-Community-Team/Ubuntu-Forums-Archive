---
title: "Is it possible to use windows bootloader?"
date: 2010-02-11
forum: Installation &amp; Upgrades
---

### Post by linuxdude7 on 2010-02-11
I was wondering if it's possible to use the windows bootlaoder instead of GRUB to choose between Windows and Linux? If so how?

---

### Post by nuffink666 on 2010-02-11
There are a number of articles on the web that do allow you to do this I found some when i was searching for Windows 7 / Ubuntu dual booting. I would have to ask why you would want to specifically use the windows bootloader over GRUB though, as I say I have windows and Ubuntu dual boot and find GRUB to be no worries.

---

### Post by kansasnoob on 2010-02-11
If it's Vista or Win 7 the answer is yes! Easy BCD:

[http://en.wikipedia.org/wiki/EasyBCD](http://en.wikipedia.org/wiki/EasyBCD)

I don't like it!

---

### Post by linuxdude7 on 2010-02-11
I was just wondering because when I removed linux after being on my other HDD last time and before, I would always have to pull out my windows vista disc and do FIXMBR and FIXBOOT and what not to be able to boot back into windows.

---

### Post by stlsaint on 2010-02-11
You could possible use easyBCD but I STRONGLY SUGGEST AGAINST DOING THAT!! Grub handles linux and windows very nicely and is very stable. If you want to get rid of grub than just use a windows disc to re-install windows bootloader to the master hdd in your system (if desktop) or internal hdd in laptop.

---

### Post by Mark Phelps on 2010-02-12
> **linuxdude7 said:**
> I was wondering if it's possible to use the windows bootlaoder instead of GRUB to choose between Windows and Linux? If so how?

As already mentioned -- yes, using EasyBCD.  I use that on one multi-boot machine and it works great.

But, before you do anything else, you should use the Win7 builtin backup function to create and burn a Win7 Repair CD.  That takes the place of the the Vista DVD (at least, for repairs) and could come in handy later if you ever need to repair your Win7 boot (e.g., restore the Win7 MBR after installing GRUB).

But, I also use GRUB2 to boot other multi-OS machines (some containing Win7), and it works just fine.

---

