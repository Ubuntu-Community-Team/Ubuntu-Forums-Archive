---
title: "New install locks up constantly"
date: 2006-12-03
forum: Installation &amp; Upgrades
---

### Post by archer75 on 2006-12-03
Starting with the install, locks up before it even reaches the GUI. Restart and try again and it gets into the GUI and I start the install process. Locks up at 15%. Restart and try again and it completes the install.

Now i'm into the system and trying to download and install updates. But it hard locks as it begins downloading them.

So I say screw it and move on to something else. I download easyubuntu and launch it. But nothing it happens. It doesn't launch.

So then I move onto install ATI drivers. First thing the ubuntu guide tells me is to install the restricted modules. Locks up during install again. 

And that is where I gave up. 

Any ideas?

I'm using version 6.10 i386 32bit.
System specs:

Core 2 Duo e6600
DFI Infinity 975x
Soundblaster X-Fi
Radeon x1900xtx
2x160gb Seagate
2x250gb Seagate
150gb WD Raptor
74gb WD Raptor
Belkin PCI-E SATA card
2x NEC 3550a

---

### Post by drphilngood on 2006-12-04
Did you try, and if so have problems with, running from the live CD?  Have you verified the installation media you are using.  You might want to try using the alternative installer, as I´ve seen that solve many people´s problems.

It could also be a hardware problem.  I say this because it seems to fail under load.  You could try the following:

**1.** test the ram with memtest
**2.** check for overheating
**3.** try another power supply or at least unhook all but the essentials(all but one HDD, for instance) to lessen the load on the one you have.

Try these and then post back.

Good luck!

---

### Post by archer75 on 2006-12-04
It's certainly not a hardware issue. I run windows on this system and game heavily and it's never been a problem. And I have tested all of my hardware.

No issues running the live CD. It's during the install as well as after the install that things become a problem. 

I can try a different installer and see how that goes.

---

### Post by drphilngood on 2006-12-06
> **archer75 said:**
> ...I can try a different installer and see how that goes.

I believe that may very well be your problem.  Try the ¨alternate installer CD¨ that can be found here:

[right click, save as]("http://releases.ubuntu.com/edgy/ubuntu-6.10-alternate-i386.iso")

---

