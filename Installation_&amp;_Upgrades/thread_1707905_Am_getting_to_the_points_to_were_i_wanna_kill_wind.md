---
title: "Am getting to the points to were i wanna kill windows..."
date: 2011-03-15
forum: Installation &amp; Upgrades
---

### Post by 4an1 on 2011-03-15
And am thinking about upgrading to ubuntu, i play lots of wow and cs, what drivers do i need to get everything running smooth.

i have and amd x64
a msi motherboard
with 1 gig of ram
msi k9n6pgm2-v2 motherboard

---

### Post by wojox on 2011-03-15
Couldn't tell you being you didn't post your graphics card/chipset. :P

---

### Post by kagerato on 2011-03-15
World of Warcraft and Counter-Strike were written exclusively for proprietary Windows APIs.  The only ways to run them on other operating systems is through reimplementations of those APIs (for example, Wine), or under virtualization (ex: VirtualBox).

As to "drivers", the Linux kernel ships with the vast majority of drivers you may need out of the box.  The only typical exceptions are high-performance 3D graphics drivers and some wireless network cards.

I would recommend setting up a dual-boot system if you really need to play Windows-specific games.  It's usually faster and easier than configuring Wine.  Most Windows graphics drivers get better 3D performance, as well.  (Although Nvidia's proprietary Linux driver is nearly as good as the Windows one, and the ATI drivers are slowly catching up bit by bit.)

Some people demand a pure Linux system, though.  Typically they use a higher-end GPU in Wine, and reduce the game's graphics settings.  That works decently, at least if the game is already well supported ( see [http://appdb.winehq.org/](http://appdb.winehq.org/) ).

---

### Post by 4an1 on 2011-03-16
its a Geforce 7025 integrated

---

### Post by wojox on 2011-03-16
> **4an1 said:**
> its a Geforce 7025 integrated

It looks like all you need is an nvidia driver and you can install those after you install the system.

---

