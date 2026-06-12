---
title: "When ever I install I get Error 15 for the grub bootlauncher"
date: 2007-11-08
forum: Installation &amp; Upgrades
---

### Post by Lord Antares on 2007-11-08
I've tried both fiesty and Gutsey, but any time I try to install ubuntu onto my USB hard drive (which has worked for months when using prior releases) I get error 15 after installing and starting to boot into Ubuntu. Beyond BIOS all that shows up is "Grub loading stage1.5, the welcome line, then just "error 15". Now I can't boot into either Ubuntu (installed over the old linux on the USB 120 GB hard drive) or onto the 60 GB main hard drive on the computer.

What can I do to fix the problem, and how do I boot into windows?

---

### Post by Pumalite on 2007-11-08
[http://users.bigpond.net.au/hermanzone/p15.htm#15](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by Lord Antares on 2007-11-08
That didn't work, so I tried the suggested [editing of the grub files]("http://users.bigpond.net.au/hermanzone/p15.htm#Grub_loading_stage1.5"), but there was no way to actually boot into linux, no matter what I did it still gave an error 15- file not found.

I don't mind (terribly, it'd be really nice if I didn't have to) reinstalling Windows and Ubuntu, is there a way that I can boot using the windows boot loader with out grub?

Edit: I've tried reinstalling grub from supergrub and that hasn't made any difference.

Edit2: I've tried booting into just the ubuntu partition through Supergrub, but then I get error 12, "invalid or unsupported executable format". I can boot into windows at least though. Is there a way to edit linux files in Windows, attempt to fix GRUB from there?

---

### Post by Pumalite on 2007-11-09
You can use Super Grub to fix Windows MBR.
Or XP Installation CD: hit 'r' for Recovery>FIXMBR>FIXBOOT

---

