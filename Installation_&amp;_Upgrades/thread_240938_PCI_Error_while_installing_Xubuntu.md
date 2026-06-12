---
title: "PCI Error while installing Xubuntu"
date: 2006-08-21
forum: Installation &amp; Upgrades
---

### Post by alex.hendrickson on 2006-08-21
Hello,

I'm trying to install Xubuntu on a AMD Athlon 64 system with the x86-64 build.

I keep getting a PCI error which I believe has something to do with my video card, an nVidia GeForce 6200 Turbocache, in the PCI Express slot.

After it's finished the first graphical screen ever with the 4 steps it takes care of, it gives me the error in the first picture below. Attempting to install it with the "Safe Video" option gives me the result in the second picture. 

I've also tried booting with the "live command, which sends it into a never ending memory test that loops itself over and over, and also the "no apci no lapci", which gives me the same PCI error.

Anybody got any ideas? 

Thanks,

Alex

[IMG]http://img106.imageshack.us/img106/7660/xubuntuho2.jpg[/IMG]

[IMG]http://img181.imageshack.us/img181/6908/xubuntu2qs9.jpg[/IMG]

---

### Post by alex.hendrickson on 2006-08-21
Is there perhaps the possibility that there is a feature inherent of the video card that should or shouldn't be disabled in the bios?

I know SOMEBODY knows what the problem is. This has stopped ANY progress at all now.

Alex

---

### Post by taurus on 2006-08-21
The first thing you need to worry about is GRUB!!!  Apparently, you forgot to include "root= " in /boot/grub/menu.lst so it can't boot...  If your / partition is on /dev/hda2, then you need to include this line in your kernel that would look something like

```

kernel   /kernel-version root=/dev/hda2

```

---

### Post by alex.hendrickson on 2006-08-21
So you're saying the entire line of code you quoted is what I need to put in the boot command line that I get by hitting F6 at the first screen? Remember I'm installing by booting the computer up and selecting the boot to CD-ROM option.

I had always typed "root=/dev/ram" before, thinking it would load it like a live installation. I will try what you've said and boot back to Windows and see if it works.

Thanks, and any more ideas are appreciated,

Alex

---

### Post by alex.hendrickson on 2006-08-21
The Xubuntu install is STILL not working yet, and the information above apparently wasn't relevant to the method of installation I'm doing.

I'm an idiot to Linux, however I'm good with computers and Windows. This must be some dumb thing I've not thought to do yet, because I see many other people with the x64 build and GeForce6200 cards on theirs.

Any further help is GREATLY appreciated.

Alex

---

