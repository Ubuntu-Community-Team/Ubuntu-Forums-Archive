---
title: "GRUB Package failed to install into /Target/."
date: 2008-01-28
forum: Installation &amp; Upgrades
---

### Post by KidBomba on 2008-01-28
The grub package failed to install into /Target/. Installing grub as a boot loader is a required step. The install problem might however be unrelated to grub, so continuing the installation may be possible.

grub installation failed, continue anyway?

> I say yes...

looking for other operating systems...

it seems that this new installation is the only operating system on this computer... ...Install grub boot loader to the master boot record?

> I say yes....

Executing 'grub-install (hd0)' failed. This is a fatal error.

> I continue

...The failing step is: Install the GRUB boot loader on a hard disk

> Now, I also tried hd0,1 and nothing.... I tried LILO and same, it wont do it.

I was having issues before the installation so I ran this:

[I]"What worked for me (alternate CD):
- proceed with install until the keyboard selection dialog
- select your keyboard if not American English but DO NOT proceed to next step (hardware detection)
- disable DMA support: Alt-F2, Enter, hdparm -d0 /dev/hdc
- proceed with install: Alt-F1, Enter

The install might be slower because DMA is off, but any attempt to re-enable it freezes the install.

Note: you might want to add the line 'hdparm -d0 /dev/hdc' to your /etc/rc.local once the system is installed."[/I]

You think this might be causing it? should I renable dma? :confused:

Any solution here? I am going to leave my compute, hopefully one of you ppl have a solution :) I totally appreciate it. BTW, this is an installation of Ubuntu-studio on an old old celeron 800 socket 370. It has an IDE drive and its pretty generic nevertheless, live boot of debian works fine. Not sure what is going on here. I also picked to install Ubuntu on the entire drive. was that a bad thing to do?

I appreciate any advice or further intstructions to proceed. :):)

---

### Post by KidBomba on 2008-01-29
*bump*

:( any ideas anyone? :(

---

### Post by GoatTuber on 2008-01-31
I just got a problem very similar to yours today, might be the same thing. I was trying to install ubuntu on a 2.5 GB partition, and it made it up to the grub part and then would fail. I could try to skip over it and go with lilo instead, but that would fail too. I did the "proceed with install" option, then it gave me the message about booting with those parameters, then finished up and rebooted. At that point, when it would boot up, it just left me with a flashing cursor and nothing else. I booted up with a LiveCD after that, and saw the /target drive on my desktop with everything installed in there, sans bootloader. Turns out I was just shy of the minimum disk size that I needed, so after a little cleaning and repartitioning, I was able to bring it up to 4 GB. I went through the installation process again , and everything worked out fine.

Since you're installing UbuntuStudio, it's gonna require a bit more space than the plain vanilla Ubuntu installation I did, so make sure you've got plenty of room for yours. Also, if you're doing manual partitioning, Grub and Lilo would fail if /boot was too small, and I think now they require a bit more space than they did a year or two ago.

---

