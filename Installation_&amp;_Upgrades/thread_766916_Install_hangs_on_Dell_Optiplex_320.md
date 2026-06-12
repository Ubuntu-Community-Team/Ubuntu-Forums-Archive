---
title: "Install hangs on Dell Optiplex 320"
date: 2008-04-25
forum: Installation &amp; Upgrades
---

### Post by jeitzen on 2008-04-25
Hello all,

Well I just starting playing with Ubuntu a few weeks ago. I downloaded the new version yesterday and was hoping to install it on my workstation.

So when I try to install it just hangs after booting. When I run the installer in verbose mode these are the last three things it says before it hangs;

[30.787553] PNP No Ps2 controller found. Probing ports directly.
[30.790295] serio: i8042 KBD port at 0x60, 0x64 irq 1
[30.790399] serio: i8042 (I forgot to write this down) at 0x60, 0x64 irq 12

Any ideas? I am running a P4 @ 3.0 Ghz with 2 gig of mem. I have 2 hard drives that are SATA. I have removed all my devices save my USB mouse and keyboard. I also have ati radeon 7000 video card.

I am at a loss. I used the CD to image another system so I know it works. :confused:

Thanks in advance!

---

### Post by 47_MasoN_47 on 2008-04-25
Apparently we both posted at the same time.  I already have Fiesty installed on my 320, it was a pain though, I had to change some options on the installer and use the alternate (text-based) install CD.  I haven't tried doing a CD install with Hardy yet (somewhat afraid to).  Do you already have Fiesty on it or will this be a fresh install?

Also, if your 320 is the same as mine, they don't have PS2 ports at all.  I'm not sure if there is a way to turn off checking for PS2 ports with the installer using one of the options, but that's probably the only way to get around that error.

---

### Post by jeitzen on 2008-04-25
I am trying to do the install with windows already on the box. 

As for the PS2 ports, I dont have any ether.

---

### Post by XplOzIOn on 2008-04-25
I installed Hardy on a DELL Optiplex 745

No problems at all... 

How about any weird setting in the BIOS?
Try using factory defaults, just an idea.

---

### Post by zgoda on 2008-04-28
> **XplOzIOn said:**
> I installed Hardy on a DELL Optiplex 745

No problems at all... 

How about any weird setting in the BIOS?
Try using factory defaults, just an idea.

This is completely different machine. 320 has ATI SATA controller and many other quirks. In short, it does not boot with default GRUB, one has to use either LILO or GRUB2. Which both are bad alternatives. I'm currently running 7.04 on Optiplex 320, booted with GRUB2, but installing it was real pain in the ***. In few days I'll try to install 8.04 and see if it runs at all (7.10 had buggy kernel and refused to start). If not, I'll trash this crappy machine and shop for something more linux friendly. All that said, it's a shame on Dell, not on Linux. It's not that easy to build incompatible hardware these days and Dell clearly succeeded.

---

