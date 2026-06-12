---
title: "problems booting 7.04 from CD"
date: 2007-08-05
forum: Installation &amp; Upgrades
---

### Post by nacho_newbs on 2007-08-05
Ok, I know there are a number of other threads about boot problems, but none seem to really deal with the same issue.  

I am running an old machine that I have assembled out of hodge-podge used parts (so hardware defects are not an impossibility).  I'm running a 750Mhz AMD, 128 MB RAM, have one 8.4 GB ATA drive, old as hell STB nitro video card, and a brand new 40X DVD burner.   

I boot up into BIOS, it recognizes my hard disk as the primary IDE, configure BIOS to boot from CD, have a brief annoying message from the PROMISE on-board RAID controller about not finding an array (does anyone know how to turn that cr*p off?) and then it starts to boot from the Ubuntu CD and hangs.  Sometimes I get barely recognizable fragments of the grapical menu, sometimes just a blank black screen.  

Here's what I know.  md5 checksum was good, and besides I can use the CD to open ubuntu on my dell laptop.  I also mistakenly burned a copy of the 64-bit version, and when I boot from that CD it can open fine on the old machine, although if I try to install it tells me not to be a jackass because my weeny old processor is ony 32-bit.  (meh, not exactly in those words) 

So does anyone have any theories about why the 64-bit can open the graphical menu and the 32-bit cannot?  Is there some difference is drivers between the two?  Any help will be appreciated.

---

### Post by logos34 on 2007-08-05
you need a min of 256MB ram to run the live cd...get the text-mode alternate install cd.

---

### Post by merlinus on 2007-08-05
What logos34 said, but I would recommend xubuntu with so little RAM.

Quote from ubuntu.com --

If you have an old or low-spec computer, using a lightweight desktop system such as **Xubuntu** is recommended, as it should make more efficient use of your system's resources. 
 If your system has less than 192 MB of system memory, use the *Alternate Installation CD*. 

-merlin

---

### Post by logos34 on 2007-08-05
yeah, go with xubuntu (or even fluxbuntu--not sure though what the current status of that project is...need to check up on it)

edit: no, looks like it's been delayed until Oct.  But you can always try out the Fluxbox window manager (vs. Xfce)

---

### Post by nacho_newbs on 2007-08-05
erm... I meant 256, not 128.  Well actually I have three sticks of 128 each, and it says in the BIOS splash screen that there is memory in DIMM slots 0 1 2, but at the very beginning of bootup it only counts 256Mb of memory.  I will try the text-only installer and see what happens.

As for Xubuntu, I know it's a slimmer version but are there limitations ot the kind of software it will be able to run?  And if not, why do they even bother making a heavy version?

---

### Post by logos34 on 2007-08-05
>  Xubuntu shares the same package sources as Ubuntu and Kubuntu. This has the following advantages:

    *

      All of the thousands of programs in the Ubuntu Software Archive are easily installable on Xubuntu.
    *

      Turn a Ubuntu into a Xubuntu System - or vice versa - by simply installing some additional packages.

Technically, Xubuntu tries to avoid dependencies to Gnome and KDE libraries by using GTK+ 2 only applications wherever possible. 

I believe this means that basically you can run just about anything available in the Ubuntu repos--subject, of course, to your hardware limitations (some programs will require too much in terms of system resources to be viable on your machine).  

Have you done a memtest86+ on your RAM?  (If I'm not mistaken you can do it from the alt cd as well).  Maybe you have a dead stick or bad dimm slot.

---

### Post by oppewala on 2007-08-06
I have this (basically) same problem too, except it's on a new computer. It works on My laptop (Fujitsu Lifebook), but not on my Dell or New computer with the Dell's hard drive. I tried the Alternate Disc, but it doesn't even register that its in the CD drive. I've done a CD check, comes back fine. Memory check shows no problems either.

The only difference is i have no idea how to check those files you said, and that it stops at the loading screen.

Laptop
RAM:     1gb DDR2
CPU:      1.6GHz Dual Core
GPU:      Integrated
Mobo:    N/A
DVD:      DVD/RW of some sort
Floppy:  None
HDD :    80gb

Dell
RAM:     512mb DDR
CPU:      2.4GHz (not Dual Core)
GPU:      5200FX
Mobo:    N/A
DVD:      DVD/RW drive of some sort
Floppy:  None
HDD:      Now in new computer

New computer
RAM:     1gb DDR2
CPU:      E6600
GPU:      8500GT
Mobo:    P5N32-E (using its sound card)
CD:        32x, Salvaged from old old computer
Floppy:  Salvaged from old old computer
HDD:      160gb SATA2 Western Digital (ex-Dell Hard Drive)

---

