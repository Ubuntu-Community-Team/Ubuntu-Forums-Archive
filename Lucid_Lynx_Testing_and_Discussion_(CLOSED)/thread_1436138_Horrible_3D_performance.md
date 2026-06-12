---
title: "Horrible 3D performance"
date: 2010-03-22
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by Aurum on 2010-03-22
Well, I've just updated to the Lucid Lynx beta from Intrepid Ibex (waited to the last minute, ergh), and I've noticed a rather significant slowdown in 3D rendering. For example, I used to be able to run Warzone 2100 without any lag at all with both the fglrx and radeon drivers, but now gameplay is so much slower. I've tried glxgears and I'm getting ~600fps in windowed mode, and ~80 in fullscreen. I tried to check my xorg.conf, but then I remembered that KMS is now used instead. Any ideas what's causing this, and how to fix this? I'm attaching the output of glxinfo.

lspci line for my graphics card: 01:00.0 VGA compatible controller: ATI Technologies Inc RV350 AP [Radeon 9600]

---

### Post by Seren on 2010-03-22
You can disable kernel mode setting by modifying your kernel bootline in grub.

You have to add something like "nomodeset" or "radeon.modeset=0", I am not exactly sure which should work.

Google around and you'll find something.

---

### Post by _h_ on 2010-03-22
Could be a bad driver support packaged with Lucid for ATI.

I had horrible performance from my integrated Intel GM965 in Karmic, and boosts in performance from the Lucid drivers (but blast, can't still play WoW at all).

Could maybe try reverting back to the drivers used on Intrepid?

---

### Post by Aurum on 2010-03-22
> **Seren said:**
> You can disable kernel mode setting by modifying your kernel bootline in grub.

You have to add something like "nomodeset" or "radeon.modeset=0", I am not exactly sure which should work.

Google around and you'll find something.

I'm not quite sure it's KMS causing the problems - it seems quite unlikely. Also, I just did a [FONT="Courier New"]dmesg | grep drm[/FONT] and found mentions of framebuffer devices being set up - could this be it?

---

### Post by psyke83 on 2010-03-22
It sounds to me that your problem is that you need to use the fglrx driver to get adequate performance. 

Lucid was unable to use the fglrx driver (as a version compatible with Lucid's version wasn't available until quite recently), so you're using the open-source radeon driver (with different performance characteristics).

---

### Post by Rob2687 on 2010-03-22
The fglrx driver no longer supports the Radeon 9600. Open source is your only option now.

---

### Post by Vanishing on 2010-03-22
The open source driver imo is not that bad..actually its pretty good.
If you really want some "good" performance, I suggest you wait until the last minute before lucid is officially out.:popcorn:

---

### Post by emarkay on 2010-03-22
> **Rob2687 said:**
> The fglrx driver no longer supports the Radeon 9600. Open source is your only option now.

Where's the list of cards/graphic chips obsoleted since Karmic's FGLRX?

---

### Post by alphacrucis2 on 2010-03-22
> **emarkay said:**
> Where's the list of cards/graphic chips obsoleted since Karmic's FGLRX?

There aren't any but IIRC the 9600 was dropped by ATI before Jaunty came out.

---

### Post by Aurum on 2010-03-23
> **Vanishing said:**
> The open source driver imo is not that bad..actually its pretty good.
If you really want some "good" performance, I suggest you wait until the last minute before lucid is officially out.:popcorn:

It's just the *slight* issue of a **1999** game not being able to be run on **2002** hardware.

---

### Post by disco_stew on 2010-04-05
I'm also experiencing a significant performance drop in Warzone 2100 after upgrading to Lucid Beta1. I used to be able to play quite smoothly, but now it is almost unbearable. 

Interestingly, I'm using the nvidia-96 driver. Perhaps this isn't only affecting fglrx?

---

### Post by Aurum on 2010-04-06
> **disco_stew said:**
> I'm also experiencing a significant performance drop in Warzone 2100 after upgrading to Lucid Beta1. I used to be able to play quite smoothly, but now it is almost unbearable. 

Interestingly, I'm using the nvidia-96 driver. Perhaps this isn't only affecting fglrx?

I'm not using the fglrx driver - ATI dropped support for the R300 chipset series for X.org 7.5, so I'm unfortunately forced to use the significantly less complete radeon driver.

---

### Post by disco_stew on 2010-04-11
Found **[this]("http://wz2100.net/faq#MyWarzoneisrunningveryslowlywhyHowcanIfixit")** on the Warzone 2100 project website. I followed the last suggestion and turned off desktop effects (compiz). That made a huge difference and the game is now running smoothly again with no lag.

I used to run the game and desktop effects with no problem, so I still think something has gone wrong when upgrading. For now, this could be a work-around.

---

### Post by amano on 2010-04-11
> **Aurum said:**
> I'm not using the fglrx driver - ATI dropped support for the R300 chipset series for X.org 7.5, so I'm unfortunately forced to use the significantly less complete radeon driver.

You know that ATI is to blame here for dropping support for their older cards?

---

