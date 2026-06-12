---
title: "consistent problem with installation from ISO disk"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by bradshej on 2011-04-07
I'm having a consistent problem with installation of a Ubuntu Lucid 64-bit iso image. What I mean by 'consistent' is that I'm seeing the same behavior on 2 separate machines, though the 2 machines differ substantially in their hardware.
The first is a Intel Core i5 processor recent enough to have Windows 7 as the base OS. Here, I've tried to use VirtualBox to allow me to run Lucid in virtual mode. I made a number of reasonable guesses for configuration of VirtualBox, then  tried to boot the Lucid iso, only to reach a fatal error "x86 is expected, but found only an i686 processor. Find a kernel appropriate for your processor". However, this is ridiculous, as the processor in use is barely 1 year in service.
The related instance is this: on another machine, I currently run Maverick 10.10 as the base OS. I thought it would be worthwhile to try using the Lucid 64-bit booting from the DVD drive, just to try it out on this machine (the reason for doing the install of an earlier release has something to do with pre-bundled software for biological analysis on the iso disk, and this represents functions that are not currently installed on my 10.10 setup). Anyway, when I boot on the DVD, I get the same error as above, to the effect of 'you have selected the wrong kernel for this machine'. However, as I stated, I run Maverick on the same machine daily, and I'm certain that the processor is also a 64-bit, x86 architecture one. Thus, I consider the problem 'consistent'.
One other feature that is relevant: the iso image itself works fine, as I've used my newer machine to boot from the iso image several times. As stated above, the only thing that doesn't work is the effort to install this in a virtual environment.
Any insights?

---

### Post by An Sanct on 2011-04-07
Did you choose 64bit Ubuntu as the guest OS?

The way I see it, you want to run a 64bit Ubuntu on a Virtual machine with 32Bit support.

Note the little "64" in the top left corner of the OS icon (see attachment)

---

