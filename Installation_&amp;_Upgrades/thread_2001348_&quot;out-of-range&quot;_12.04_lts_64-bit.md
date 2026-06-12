---
title: "&quot;out-of-range&quot; 12.04 lts 64-bit"
date: 2012-06-10
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2012-06-10
I just installed 12.04 LTS 64-bit on a new homebuilt PC (alredy tested with Win XP Pro SP3, also residing on hard drive).  PC is built around a BioStar N68S3B motherboard with Sempron 130 CPU, 8 GB RAM, and nVidia GeForce 7025 video.  After original install which cuased Upgrade Manager to load numerous programs, the mandatory restart resulted in back screen with video "out-of-range".  If I hit the "Enter" key, normal logon appears.  I have right nVida driver loaded and set for 60 Hz, which I know works for Viewsonic VA926 monitor.  I have loaded the grub-customizer program, but nothing is apparent in the instructions (appear to be written for experts) on how to solve problem. The xorg-conf file looks reasonable.  I would think that Grub so behave nicely with recently up-to-date motherboard, so what am I doing wrong?

John

---

### Post by drs305 on 2012-06-10
If GRUB isn't working:

If you are still booted on a LiveCD, try installing Boot Repair and go to Advanced, Grub Options and *tick* the GRUB_GFXMODE and see if that helps.

It's possible your Grub is being told to use a resolution it's not capable of. You can see the GRUB resolutions at a grub prompt with "vbeinfo", but that's for when you can see the menu in the first place. ;-)

Boot Repair link is in my signature line.

If GRUB is working, I'm not an expert at video problems so I'll leave this to others.

---

### Post by YannBuntu on 2012-06-11
Hello
> **drs305 said:**
> untick the GRUB_GFXMODE

it is unticked by default. I think you meant "tick" ;) . (and this is what i would have recommended too)

---

### Post by drs305 on 2012-06-11
> **YannBuntu said:**
> Hello


it is unticked by default. I think you meant "tick" ;) . (and this is what i would have recommended too)

Yes - I was thinking 'change' but as you say, that would mean *ticking* it. Thanks. I've corrected the previous post.

---

### Post by cigtoxdoc on 2012-06-11
A big thank you to YannBuntu and drs305 for recommending boot-repair-disk iso.  I tried followingthe suggestions to download and install it via the command line, but that gave the usual error messages that must be designed to be interpreted only by Ubuntu experts.  I then downloaded the ISO image from sourceforge and burned it to a CD-ROM with brasero.

When it booted, a got numerous lines of what may have been disk errors.  It finally booted into a graphical display.  It asked to connect to the internet, but connection to Ethernet to my DSL liones was already active.

I let the program do an "automatic" fix and when it was done, PC booted into something that looked like it gave me several boot options, including Win XP Pro, which is on the other half of the hard drive.

John

---

### Post by YannBuntu on 2012-06-11
good job :) 
you can use the tool on top of this page to set this thread as "Solved".

---

