---
title: "Can't boot from CD"
date: 2011-06-01
forum: Installation &amp; Upgrades
---

### Post by eeonz on 2011-06-01
Sorry for the long thread guys - i'm a total IT novice, but thanks in anticipation!

I've got a horrible virus on my windows Vista laptop and need to reformat and start over again. Seems as good a time as any to swap over to ubuntu linux.

I downloaded ubuntu linux version 11.04 32bit from here:

[http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

And followed the directions to put it on to a CD-RW (700MB - 80 min, 1x 4x compatible if thats important?) following the directions on the above link and using infra recorder.

I start my laptop up (a maxdata eco 4511 IW) with the CD in and windows loads as normal.

So.... instead i press "F12" during start up. I get a screen with "Boot Menu" and the option to "Enter Setup"

I go to enter setup, then "Boot" There's "LAN BOOT" (Enabled)" and "Boot options"

Boot options reads:

1: USB CDROM
2: IDE CD: HL DT ST DVD RAM GSA T20n
3: IDE HDD TOSHIBA MK1637GSX
4: USB HDD
5: PCI BEV: Realtek Boot agent
6: USB FDC
7: USB Key

Excluded from boot order:

PCI SCI
Other USB
PCI:

Looks like CD rom is at the top right? Still won't boot from CD, even after restarting. Also, won't boot an XP installation disk either.

I know there are other options - boot from flash drive etc, but i thought this would be the easiest! Any ideas please folks? Have i missed something obvious?

Thanks!
Ian

---

### Post by binkles on 2011-06-01
How did you burn the ISO image of ubuntu to the CD?

---

### Post by eeonz on 2011-06-01
I used the "infra recorder" suggested in the download guide.

Actions -> Burn image -> open -> ok Pretty much followed it word for word.

However, when i tried the XP disk, I manged to get to the "press any key to boot from CD" screen, but I get the message "cannot complete installation - cannot find HDD". I'm really just using the XP disk to trouble shoot my problems with the linux installation. It's linux that I want!

Edit: [http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/](http://www.howtogeek.com/howto/windows/resolving-setup-did-not-find-any-hard-disk-drives-during-windows-xp-installation/) 

That solves the XP problem - could it be something similar going on thats blocking my linux installation perhaps? Also, i'm looking in to using a memory stick to install now as i'm all out of CDs - will the file be under 2GB?

---

### Post by baarn on 2011-06-01
i would recommend to get rid of some devices in that boot order (disable) just for security purposes.

i am not sure about your problem... but i often had problems with CD-RW, regarding other purposes than booting an OS, but i would never choose one of those for critical stuff.
either try a standard CD-R or if you have an USB stick, there is a simple tool called UNetBootin which does all the stuff for you to create a bootable USB-Stick (only thing you might have to do is format it to Fat32, but most USB-sticks are from factory). Available for Win/Linux/Mac.

---

### Post by eeonz on 2011-06-01
Thanks for the reply - any chance that it would all fit on a 2GB memory stick? Thats all i've got handy at the minute.

Also, what did you mean by this please:

> i would recommend to get rid of some devices in that boot order  (disable) just for security purposes.

Honestly, they're just words to me!

---

