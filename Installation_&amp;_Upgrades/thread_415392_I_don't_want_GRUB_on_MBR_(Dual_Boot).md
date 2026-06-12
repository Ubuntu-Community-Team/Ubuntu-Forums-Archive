---
title: "I don't want GRUB on MBR (Dual Boot)"
date: 2007-04-20
forum: Installation &amp; Upgrades
---

### Post by iminj on 2007-04-20
I am installing Feisty (7.04) from the ubuntu LiveCD to dual boot with Vista - on 1 partitioned hard drive.

I'd like to keep Vista's bootloader (easily managed/edited with EasyBCD) on the MBR, and put GRUB in the ubuntu boot partition. When I get to the bootloader portion of the feisty installation, it doesn't provide me any options to place GRUB - other than the default (hd0,0) ... which is NOT where I want it. 

**Is there any way I can configure GRUB's location during the installation,** so I won't have to go in afterwards and figure out how to move it to a different partition? *(If I remember correctly, hoary and warty versions of ubuntu specifically provided user flexibility re: location of GRUB during installation).*

---

### Post by Nobber on 2007-04-20
I think that capability is provided only on the 'alternate' install disc.

Which sucks, yes.

---

### Post by galego on 2007-04-20
dont qoute me on this but i am pretty sure that has not changed. i just installed Fiesty yesturday and i only noticed (clean install BTW) one new screen. 

after you set your partitions and you are asked to confirm the location of grub and the install -- on that screen you can change the location of GRUB (same as on Edgy) just click on the box that specifies the location (hd0) and a dialog box opens and there you go. again, i wasnt looking for that in fiesty but im sure it is still there. definately in Edgy!

hope that helped?!

EDIT: this was with a LIVE CD!

---

### Post by Npl on 2007-04-20
On the last dialog in the installation-procedure you had an "Advanced Options" Button. Allows you to specify a hdd for the bootloader.

Im actually pissed because the Ubuntu-Installation detected my HDDs wrong and I then had to fix GRUB while not able to boot into Windows or Linux on the HDD.  No warning even its explicitely stated in GRUB`s manual that detection of HDDs is unsafe when run from within Linux, just quietly **** it up if in doubt.

---

### Post by FlyingCheese on 2007-04-20
I would love a little more detail on this. I want to dual boot Ubuntu and an already existing XP install.

I don't want to use GRUB on the MBR as I like to reformat XP every 8 months to a year or so and that would kill GRUB.

---

### Post by orb9220 on 2007-04-20
Then when you reinstall xp you just have to
[http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub](http://www.ubuntuforums.org/showthread.php?t=24113&highlight=blue+grub)

Works for me when I reinstall xp with a ubuntu already installed.

---

