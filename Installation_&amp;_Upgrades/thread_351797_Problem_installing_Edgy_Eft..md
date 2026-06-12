---
title: "Problem installing Edgy Eft."
date: 2007-02-02
forum: Installation &amp; Upgrades
---

### Post by LowFatCannibal on 2007-02-02
I've tried to install Edgy so far with 4 different burned discs, 3 different ISOs, and 2 different DISC DRIVES.

It hangs everytime on the graphical "loading bar" screen, and doesn't progress. I've left it a good hour just incase it needs to be left, but no progression.

Help?

---

### Post by glabouni on 2007-02-02
have tested your disc ? there's an option to go this in boot menu.

removing the "quiet" parameter from boot command will show onscreen output of boot process.

---

### Post by dbqp on 2007-02-02
Also, have you tried to run it as a Live CD?  If that works, you could go into the GUI install right away.

---

### Post by xVariable on 2007-02-02
It sounds like you're having the same problem as I.  I boot from the Edgy CD and select "Start or Install Ubuntu".

At first everything is fine: the bar sweeps left-right, then the bar starts to fill-up from left-right.  With about 2 "segments" left before the bar is entirely filled, two lines of blueish dots appear just below the Ubuntu logo.  A few second after that a couple of thin bright green lines appears below that.

I'm assuming what's happening there is that it's trying unsuccessfully to switch screen resolutions, and the thin green lines are distorted text output.

Of course the disc boots fine in VMware (which is useless to me.  I mean, I'm trying to *get away* from Windows...).

I've tried safe graphics mode, acpi=off, vga=771, gdth=disable:y, and aic7xxx=no_prob, but they all yeild the same result.  I haven't tried them in combination since obviously there is thousands.  I've also tried connecting only one display at a time to no effect.  Fedora Core 6 and Suse 10.2 both boot and install OK on this system.

I've posted a cellphone [video]("http://www.youtube.com/watch?v=FsaXNfKaHfs") on YouTube documenting the problem.  My system specs are:

Dell XPS Gen 4
Latest BIOS revision (A07 I think)
Pentium 4 HT 3.4 Ghz
3 GB DDR2 RAM (533)
ATI x850 XT Platinum Edition w/256 MB RAM (r480 5d4d)
Displays: Dell 2407WFP (via DVI), and 2001FP (via VGA)
SATA 2
WUSB54GC

I'm downloading Herd 3 and will maybe have better luck with that (of course the download speed is atrocious on my 7 Mbps connection.  All this friction in getting this installed really sucks ;) ).  Regardless, does anyone know what's happening here?

---

### Post by xVariable on 2007-02-03
Yeah, so Herd 3 works.  Dapper and Edgy suffered from this exact same problem.

Its utterly pointless to express my displeasure over these sorts of problems ALWAYS appearing in Linux and never in Windows.  There's always an excuse.  I don't know why I keep coming back or recommending it.  People must think my advice sucks when they encounter the same problems I do.

---

### Post by LowFatCannibal on 2007-02-03
Dapper Drake did the same thing, except it hangs at the "decompressing linux, booting kernel" phase.
It hangs booting the kernel with both.

So I'm stumped.

---

