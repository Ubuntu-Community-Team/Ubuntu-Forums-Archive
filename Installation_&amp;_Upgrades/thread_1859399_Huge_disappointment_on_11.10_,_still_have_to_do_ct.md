---
title: "Huge disappointment on 11.10 , still have to do ctrl + alt + fn to get the screen."
date: 2011-10-13
forum: Installation &amp; Upgrades
---

### Post by bbmak on 2011-10-13
The graphic card problem seems never fixed. 

Just install new 11.10 on my laptop, and the screen goes blank after reboot. 

Why is Ubuntu never fixed the problem? I see many people complain in 11.04 release already, and now the problem just keeps carrying into the next release, 11.10.

---

### Post by markymark64 on 2011-10-13
Have you tried reinstalling your graphics drivers?

---

### Post by hongquan1987 on 2011-10-13
> **markymark64 said:**
> Have you tried reinstalling your graphics drivers?

With the black screen, how can you see the desktop in ordrer to reinstall the driver?

---

### Post by Quackers on 2011-10-13
Which graphics card?
Have you tried boot options like nomodeset?

[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by MAFoElffen on 2011-10-13
> **bbmak said:**
> The graphic card problem seems never fixed. 

Just install new 11.10 on my laptop, and the screen goes blank after reboot. 

Why is Ubuntu never fixed the problem? I see many people complain in 11.04 release already, and now the problem just keeps carrying into the next release, 11.10.
You want the good honest truth right? Unbias, simple and undiluted?

The "problem" you are describing is happening in all current distros of linux do to upstream changes in Grub, the Linux Kernel and Xorg-server.  (Those changes were graphic related trying to take advantage of advances in graphics techonlogies.)

As for working aronnd it, see the first 3 posts of my Graphics Resolution sticky:
**[B]Sticky:**[/B]                                      [COLOR=#008C00]**[all variants]**[/COLOR]                          [Graphics Resolution- Upgrade /Blank Screen after reboot]("http://ubuntuforums.org/showthread.php?t=1743535")

Which the short form as relate to your particular problem, depending if you have NVidia, ATI or Intel Graphics:
- For NVidia, add "nomodeset" as a kernel boot parameter.
- For ATI, add "radeon.modeset" as a kernel boot parameter.
- For Intel, add i915.modeset=-0" as a kernel boot parameter

Boot, then go to additional driver through system settings and add the driver you need...

As for graphics issues.  We been fooling with that in Linux for years.  At least now "we have drivers" available and don't have to go look for them ourselves ... compile and install them manually and hope they work for the version of the distro we're using.  For the most part, a lot of that "is" automated within the install process.  

Mostly I think the immediate challenge is with nVidia and Radeon cards.  They do both VESA, but not natively (not automatic)--> Meaning they have to be told (differently for each) to go into that mode.

---

### Post by bbmak on 2011-10-14
> **markymark64 said:**
> Have you tried reinstalling your graphics drivers?

Have fixed. I feel disappointed because just can't believe that this problem has last for several releases already, and Ubuntu still hasn't taken any action to fix it.

---

### Post by uRock on 2011-10-14
> **bbmak said:**
> Have fixed. I feel disappointed because just can't believe that this problem has last for several releases already, and Ubuntu still hasn't taken any action to fix it.

The ubuntu devs do not write the graphics drivers.

---

