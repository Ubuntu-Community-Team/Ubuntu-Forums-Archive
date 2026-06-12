---
title: "Installation woes using Ubuntu 20.04.1"
date: 2020-09-02
forum: Installation &amp; Upgrades
---

### Post by lonesheep on 2020-09-02
Hi,

I'm trying to install Ubuntu 20.04.1 on a clean system;

Asus Prime B450 motherboard
GTX 1060 gpu
250GB SSD

I've enabled UEFI only on the m/b and disabled secure boot.

When booting from USB, I get the grub install menu.  Selecting;

1) Ubuntu, presents me with a blank screen
2) Ubuntu, safe graphics mode, presents me with a blank screen.

Using the "nomodeset" override didn't seem to make any difference.

Using Fedora - all is OK.  

Any advice would be most welcome.  If not, Fedora it will be then!

Many thanks

---

### Post by lonesheep on 2020-09-02
It would seem that if I enable legacy boot mode - i.e. non UEFI, I can boot into a GUI.  All secure boot is disabled in the BIOS.

Why I have no idea.  But I'll see if I can install Ubuntu and see what happens.

---

### Post by lonesheep on 2020-09-02
Well...no!

UEFI on or off seems to make zero difference.

Interesting thing, is on boot, when the screen goes black, USB also seems to die - well, the keyboard and mouse lights turn off.

---

### Post by lonesheep on 2020-09-02
Installing Windows 10!

I'll wait a 6 months to see if the next release of Ubuntu fixes the issue.  For the record, I managed to get Fedora installed (first time), however that was unstable - locked up a few times over the afternoon before finally entering maintenance mode (which it wouldn't leave)

---

### Post by ubfan1 on 2020-09-02
Check with Asus for any firmware updates for the B450.  the acpi=0 may get you around some issues, but at a huge cost, breaking things like multi-cpu support.

---

### Post by mastablasta on 2020-09-03
that's Ryzen + nvidia right? what is the monitor? do you have a GPU chip on the CPU?

i assume you get to grub. can you boot to text mode only or nothing is showing up on monitor?

it could be that the output is sent to another plug or that os doesn't see the monitor. i though that the HDMI cable was faultiy. then i used another cable and it worked. i tested the cable that came with monitor at hardware store and it worked. so i replaced it and it is still working.

did you check the downloaded ISO file (MD5SUM or SHA5)?

we have ASUS board ( i think with B450 chipset), with Ryzen 7 2700 on one PC with nvidia GTX 1650 and 18.04 installed there just fine.

---

