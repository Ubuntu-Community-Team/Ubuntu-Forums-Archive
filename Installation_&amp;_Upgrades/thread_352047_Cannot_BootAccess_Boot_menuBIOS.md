---
title: "Cannot Boot/Access Boot menu/BIOS"
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by puer on 2007-02-02
I'm hoping someone here can help me.

Awhile ago, I had a failed Arch-linux installation.  It froze during the install, so I was forced to just pull the plug.

I assumed I could easily fix it, but, I cannot load ANYTHING.  When I turn the computer on, I can get as far as that initial boot screen where you can access your BIOS and all that junk, but at that point it freezes.  As such, I can't change the booting order, or do anything that I could think would help.

Other things I cannot do:
Live CD's
General Installation CD's
GRUB 'repair' cd's
Command line
BIOS
Boot Menu
etc.

Because I can't do anything, I don't think it's an MBR problem.

What I'm wondering is:

A) does anyone have any idea how I could fix the problem
B) does anyone have any idea who could fix the problem
C) if I were to replace the entire hdd, would I still run into the same problem?
     -I'm hoping that the problem is somewhere on the disk itself, so if I buy a new one and swap the old one out, I should be able to start fresh.  But, I don't want to waste my money if the problem is located somewhere else, and a new hdd won't fix it.

Anyways, Thanks to anyone who can help.

Jacques

---

### Post by kairu0 on 2007-02-02
A quick way to diagnose if it's the hard disk would be to physically unplug the computer, turn the computer on, and see if you can get into the BIOS. If you can, then it must be the problem.

---

### Post by logos34 on 2007-02-02
> When I turn the computer on, I can get as far as that initial boot screen where you can access your BIOS and all that junk, but at that point it freezes. As such, I can't change the booting order, or do anything that I could think would help.

Sounds like a bios problem...You could try resetting/clearing cmos settings by removing the jumper on the board, then go back into the bios and set it for 'optimized defaults'...check you manual...Could also have bad sectors on the disk, which is what happens when you suddenly cut the power (by pulling the cord or hitting the main power button).  Run e2fsck or fsck from the live cd if and when you can manage to get that far.

---

