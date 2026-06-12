---
title: "[DR-DOS] A:\&gt; and something about caldera when i start"
date: 2006-08-12
forum: Installation &amp; Upgrades
---

### Post by avynth on 2006-08-12
Hi, i'm about as new and green to linux as they get, haha, but my old win98 machine in the other room is just a plain b****, so i decided, well, i'm probably not going to be using it anymore, why not put linux on it! yay! so i decided to install xubuntu, i burned the iso image to a cd with cdburner XP pro3 in a bootable format, but when i start my computer up with that in the cd drive, it just comes up with a black DOS screen and spits out a bunch of stuff, and i notice the word "Caldera" is repeated multiple times as if it's important or soemthing, and then it comes down to a prompt that says [DR-DOS] A:\> and that's it! it doesn't tell me what to do or anything, and i can't boot up the iso while having the computer on normally and insterting the cd, so yeah... from what i've read and been told, i don't think this is supposed to happen, any helpful suggestions? thanks a bunch!

---

### Post by Anduu on 2006-08-12
AFAIK when you burn the iso you do not need to set any special flags(ie bootablr...)....just do a straight "burn image to disk" and it should work...

Also make sure you burn your cd at the lowest speed possible to avoid any errors.

---

### Post by orb9220 on 2006-08-12
For the boot problem to run and or install ubuntu you need to be ablec to boot from cd. This is in the bios which you enter at bootup and it says   to hit del key or a function key to enter setup. In there should be a boot from device order menu.

Which allows you to select which devices are first in the boot order which you want cdrom as first boot device.
    

At some time when you installed a program caldera,dr. dos it wrote to your mbr which is the MasterBootRecord whcich tells the hd how to boot. You can fix this with a w98 startup disk at the a>fdisk /mbr

Will restore your mbr or if you do an install from the ubuntu liveCD than that will also take care of that when it writes the grub loader to the mbr.

---

### Post by avynth on 2006-08-13
that was the first thing i checked was the bootup, and my cd drive is set up to be the first thing that's checked, and i haven't installed anything called "caldera", i recently formatted and reinstalled win98 on that machine, and since then it's been screwed up, i couldn't install anything if i wanted to

---

### Post by linear on 2006-08-14
Odds are that the iso was not burned to the CD as an image. Whatever you used to burn the CD made a bootable DOS disk.

---

