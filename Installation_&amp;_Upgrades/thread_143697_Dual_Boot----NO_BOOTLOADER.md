---
title: "Dual Boot----NO BOOTLOADER"
date: 2006-03-12
forum: Installation &amp; Upgrades
---

### Post by Nathan Murray on 2006-03-12
I recently tried out a verison of Linux, Mepis. I wasn't too happy with it and I just spent the day getting it off my PC. I decided however that I still want to run linux and try it out some more. My friend worships it. I was wondering first of all why Ubuntu is the 'best' distro out there in anyone's opinion. Most importantly, I would like to know if there was a way that instead of using Grub, or w/e Ubuntu uses for dual booting, I could use a floppy boot disc. With my past experience today getting GRUB off my PC i know that it's possible, but does anyone know what to input for the commands. 

My Specs (Hard Drive) :

---120 GB Drive---
C: Windows
D: Multimedia content for windows

---160 GB Drive
E: More multimedia
E: Partition (20 GB) (Linux)---

If anyone can help me, that would be great:KS

---

### Post by aysiu on 2006-03-12
[QUOTE=Nathan Murray]I recently tried out a verison of Linux, Mepis. I wasn't too happy with it and I just spent the day getting it off my PC.[/quote] Can you be specific as to your dislikes with Mepis? If you say what you *don't* like about it, perhaps we can shed some light on whether Ubuntu would be a good choice for you. > I decided however that I still want to run linux and try it out some more. Again, can you explain a bit as to what appeals to you about "Linux," and maybe we can explain how Ubuntu does or does not fit your ideas about Linux (maybe even another distro--not Ubuntu *or* Mepis might better suit your needs). > My friend worships it. I was wondering first of all why Ubuntu is the 'best' distro out there in anyone's opinion. The support on these forums. That's the major reason. Nothing about the operating system itself makes it superior to other distros, as far as I know. > Most importantly, I would like to know if there was a way that instead of using Grub, or w/e Ubuntu uses for dual booting, I could use a floppy boot disc. With my past experience today getting GRUB off my PC i know that it's possible, but does anyone know what to input for the commands. What don't you like about Grub on the MBR? Just curious. I believe you can install it to an external source, but I'm not sure how. Some distros (Xandros, for example) prompt you specifically for a floppy disk. Ubuntu allows you to specify a device location (/dev/hda1, for example). I'm not sure how that works with floppies...

P.S. You may want to read the [Is Ubuntu for You? thread](http://www.ubuntuforums.org/showthread.php?t=63315).

---

### Post by eriefisher on 2006-03-12
I used Mepis 3.3.2 for awhile, solid distro. I beleive it has a utility that you can put the bootloader on a floppy from windows. I think it's for machines that have trouble booting from a cd.

eriefisher

---

### Post by dermotti on 2006-03-13
You can duel boot using Windows Boot loader, but imho its more trouble than its worth. Google it theres a few how-toos out there.

I would use the mepis live CD, im pretty sure it will let you write grub out to a floppy.

---

### Post by eriefisher on 2006-03-13
If you load the Mepis live CD and click "Install Me" there is an option to load grub and where, just choose floppy. Or you can create a boot disc in windows from it

Not sure this will help with Ubuntu though.

eriefisher

---

### Post by dermotti on 2006-03-13
Wonder if you can edit the menu.lst once its on the floppy? Then it would be easy to modify it to boot ubuntu

---

