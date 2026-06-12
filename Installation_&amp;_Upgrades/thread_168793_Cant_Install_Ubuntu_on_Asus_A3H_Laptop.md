---
title: "Cant Install Ubuntu on Asus A3H Laptop"
date: 2006-05-01
forum: Installation &amp; Upgrades
---

### Post by westvleteren on 2006-05-01
I am unable to install Ubuntu on my Asus A3H Laptop.
It seems installation is complete, but when I boot into Ubuntu It freezes up, and is unable to enter the Login screen.

---

### Post by westvleteren on 2006-05-01
I booted up again into Ubuntu and it freezes at "Starting hotplug subsystem"

---

### Post by zolero on 2006-06-26
Hi westvleteren!

I've have the same problem on same laptop, but it can be figured out. This prob is from the Intel HDA soundcard in Ubuntu Breezy.

Press F2 during boot disable the modem/sound in BIOS, restart. Upon this open this file with gedit: /etc/modprobe.d/blacklist and blacklist the soundcard (insert this line at bottom of the file: snd-hda-intel), then save the file, restart, and enable sound from BIOS.

It won't freeze boot process anymore at blacklist!

U need now to compile a new ALSA driver in kernel. See [here]("http://www.alsa-project.org/alsa-doc/doc-php/template.php?company=Intel&card=ICH+southbridge+HD-audio+and+modem.&chip=ICH6%2C+ICH6M%2C+ICH7%2C+ESB2&module=hda-intel") for more info on this. U may have to create some files, and everything's gone to be OK.

Note that this soundcard is an HDA Intel (ICH6) with Azalia controller chip (ALC880) from Realtek. (But don't try their driver! It is damn buggy and shitty, man... I've tried it of course. :x) )

Finally U need to reenable soundcard from blacklist too (for doin' this comment in the line inserted above by inserting a # before it, and if alc880 is blacklisted too make same thing with it!). Restart one more time, and now U got sound.

This is only needed in Ubuntu Breezy on this Asus notebook. With Dapper all hardwares works (almost) perfectly. Only the SPDIF OUT must be configured for listen music on headphones. For do this U need to insert this line at the bottom of file /etc/modprobe.d/alsa-base, and then make a restart ;-)

          options snd-hda-intel model=z71v position_fix=1

Good luck, Zolero.

---

### Post by mdz on 2007-01-17
This laptop is not well supported by Ubuntu 5.10 (which is over one year old now).  We recommend installing the current release, Ubuntu 6.10, instead, or Ubuntu 6.06 LTS if your circumstances require a longer maintenance and support lifetime.

---

