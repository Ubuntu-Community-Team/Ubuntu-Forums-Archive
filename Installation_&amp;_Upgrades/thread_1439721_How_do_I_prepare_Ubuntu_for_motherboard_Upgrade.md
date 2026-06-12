---
title: "How do I prepare Ubuntu for motherboard Upgrade?"
date: 2010-03-26
forum: Installation &amp; Upgrades
---

### Post by SNYP40A1 on 2010-03-26
I am planning to upgrade my system's motherboard tonight.  I am going from a Via chipset and ATI graphics to Intel G41 chipset with onboard graphics.  What do I need to do to Ubuntu in order to handle the upgrade?  I'm running an updated version of 9.10.

---

### Post by jocko on 2010-03-26
Which driver do you use for the graphics card?
If you use an open source driver (ati/radeon/radeonHD), you just need to make sure you remove any static configuration (i.e delete /etc/X11/xorg.conf if it exists).
If you use the proprietary driver (fglrx), you need to uninstall that and remove /etc/X11/xorg.conf.

---

### Post by tgalati4 on 2010-03-26
It should work out of the box.  The kernel will detect your hardware and load the needed modules.  Deleting (or renaming) xorg.conf is a good idea.  Let us know what issues you encounter.  I'm going to guess it will run well with few issues.

---

### Post by SNYP40A1 on 2010-03-27
> **tgalati4 said:**
> It should work out of the box.  The kernel will detect your hardware and load the needed modules.  Deleting (or renaming) xorg.conf is a good idea.  Let us know what issues you encounter.  I'm going to guess it will run well with few issues.

I am happy to report that the upgrade went flawlessly.  After running memcheck, I connected the hard drive, got to the GRUB loader and Ubuntu booted fine.  I did not have to change a single thing.  I did have to update a bunch of drivers for the WinXP install and I have a wierd issue where it refuses to use the DVI port, but other than that, no major issues.  Very impressed with how well Ubuntu handled the upgrade.  Truly plug and play in this case.  Wish I had the same experience installing Ubuntu on my parent's MSI board a few months ago.

---

### Post by tgalati4 on 2010-03-27
Your DVI is on the motherboard?  Is there a BIOS switch to turn it on?

My next prediction is that the US stock market will be higher on Monday.   ;)

---

### Post by SNYP40A1 on 2010-03-27
Both DVI and VGA are on the motherboard.

I looked in the BIOS and I think it's on by default.  It boots up using DVI without having to do anything in Ubuntu.  It starts to boot with DVI in windows, but half-way through bootup, it switches back to VGA.  

tgalati4, keep sending me your predictions.

The hardest part of the install was installing the CPU fan.  Intel chose their worst design for the heatsink mount on the LGA775 socket.  The previous 478 pin P4 design was far superior.

---

### Post by tgalati4 on 2010-03-27
I agree.  I think Intel changed the fan design for cost reduction.

So we know that DVI works since the boot-up gives you output (but probably only text/console graphics).

There's probably an option switch in xorg.conf to turn it on.

What is the xorg video driver that get's loaded?

less /var/log/Xorg.0.log

---

### Post by SNYP40A1 on 2010-03-30
> **tgalati4 said:**
> I agree.  I think Intel changed the fan design for cost reduction.

So we know that DVI works since the boot-up gives you output (but probably only text/console graphics).

There's probably an option switch in xorg.conf to turn it on.

What is the xorg video driver that get's loaded?

less /var/log/Xorg.0.log

Oh, no DVI works flawlessly in Ubuntu, no problem there.  My problem is with Windows XP.

I asked around and Intel changed the fan design at the request of high-volume manufacturers.  The 478-pin P4 fan was easier to install for custom system builders, but harder for someone like Dell or HP to automate than the current fan.  The new design is simple, but too cheap in my opinion.  It's very easy for the plastic clip pins to not adhere securely or snap off.

---

### Post by blur xc on 2010-03-30
> **SNYP40A1 said:**
> 
The hardest part of the install was installing the CPU fan.  Intel chose their worst design for the heatsink mount on the LGA775 socket.  The previous 478 pin P4 design was far superior.

My first build was w/ the lga775 and the idiotic push pin oe intel cpu fan.  I couldn't stomach installing that fan (by the time I got three pins installed, my mobo had a nice bend in it), so I tossed it and bought a nice Zalman unit.  It has a threaded bracket that mounts on the back side of the mobo, and another bracket that goes on the front side.  Then the screws go in, sandwiching the mobo between the two brackets.  Then to that, with a nice spring steel clip, does the actual cooler attach.  Very solid sano design...

I don't need that much cooling, but it looks cool, and wasn't expensive ($50, could have been $35 but I missed the sale :-( ).

BM

---

### Post by tgalati4 on 2010-03-30
Makes perfect sense for the cheapo Intel fan/heatsink design.  Can't help you with DVI on Windows.  No offense, I just don't use Windows, and have no clue how to troubleshoot in XP. 

(And the market was up on Monday.)

---

