---
title: "Hangs during installation - Dell Celeron 500"
date: 2007-01-03
forum: Installation &amp; Upgrades
---

### Post by NMeyne on 2007-01-03
Hi, I'm new here, struggling with an install on a Dell Celeron 500Mhz i386 with 512k ram. An Intel 810 video chipset with 4Mb and a soundblaster 64 chip onboard.  Memory test works fine.  I've tried ubuntu 6.06, 6.10, 6.10 alternate, Fluxbuntu and now Edbuntu... but they all hang after the basic drivers load...  either frozen splash screen or a blue screen or 'kernel panic' text.

DSL and DSL-N load up and run very well on this machine... very stable.  The only clue I have is that they throw up an 'unknown graphics mode' returned during the boot and skip to a default 80 x 25 mode after a few seconds.  Could this weird graphics mode be what is causing all the Ubuntu distros to hang on my machine?

BIOS is up to date.  Are there any obvious bios settings to play with?

Help please...  this has taken ages to sort out so far!

Happy New Year.

Nick

---

### Post by taurus on 2007-01-03
How fast did you burn the alternate CD?  If you were burning it at a default speed, I recommend you try to burn it again at a slower speed like 4x.  Wouldn't hurt to check the integrity of the ISO image right after you've downloaded it to be sure...

---

### Post by NMeyne on 2007-01-03
They have all been burned reasonably fast, but Ok...  Checksums OK - md5 and bitTorrent report all OK.  All the distro cd's have problem at the same point I think. Other linux downloads and burned images work fine - e.g. DSL / DSL-N

---

### Post by taurus on 2007-01-03
Try burning it again at 4x!!!

---

### Post by NMeyne on 2007-01-03
Thanks - did that at slowest speed possible (8x) and with full verification.  Still have exactly the same problem at same point.

I'm still trying...  but I've got very limited knowledge of the boot options (e.g. I'm not sure I'm putting the 'acpi=off noapic nolapic' options in the right place).

When I take the 'quiet' option off the last things appearing after apparently successful device driver loads and just before kernel panic are:  init kernel....  unkown boot option + 0x0/0x270...  followed by a code dump 'EIP' etc

---

### Post by NMeyne on 2007-01-03
Are there any known Dell or Intel 810 issues here...  anyone?  Otherwise I'll have to revert to DSL-N!

---

### Post by NMeyne on 2007-01-13
I've come back to this for yet another go from scratch.

I've burnt another alternate cd (my third one), at 4X and still have the problem above.  On a graphical install it freezes as above, and on a text install it freezes after seemingly loading all the device drivers OK.

But I must be doing some idiot thing somewhere.  I've tried all the boot options that I can see in the documentation and in other threads.  I don't see how to get to dpkg-reconfigure xserver-xorg, because I think the kernel has fallen over before I  get that far.

What am I doing wrong?  There must be some sort of minimal boot I can get into to find out what is upsetting Ubuntu on this machine?

Regards to all,

Nick

---

