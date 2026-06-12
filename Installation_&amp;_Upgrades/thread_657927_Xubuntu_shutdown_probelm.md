---
title: "Xubuntu shutdown probelm"
date: 2008-01-04
forum: Installation &amp; Upgrades
---

### Post by StevePepple on 2008-01-04
I just got Xubuntu on the latest Linux Format magazine DVD.  I drug out a 500MHz machine, with 256Mb or RAM, and installed the OS.  The install went smoothly, and it boots up cleanly.  The problem is that when I try and shutdown, the splash screen comes up, the progress bar advances to the end, then it hangs up.  Yesterday, I hit shutdown, turned off my monitor, and went to run errands.  When I came back four hours later, I turned on the monitor, and it still hadn't shut down.  I had used this system in the past with Win98, an older version of Ubuntu, with no similar problems.  I put in a Damn Small Linux CD, and was able to shut down cleanly yesterday.  I'd appreciate any clues.    Thank you, Steve Pepple, Seattle, WA USA

---

### Post by jan quark on 2008-01-04
I am not that experienced yet... and perhaps my advice is to straight forward... but

I solved every issue with shutdowns and booting by using the alternate CD version... 
I am using Xubuntu 7.10. In the past while installing via the Live CD sometimes my laptop just hanged up during boot time or during the shutdown.

Perhaps it was my specific problem on my specific Dell laptop, but since I install via the alternate CD no problems whatsoever..

but wait for other experienced players... perhaps they find the gremlin in your system without a fresh install:)

---

### Post by perixx on 2008-01-04
did you by chance leave a cd/dvd in your drive? then Xubuntu is likely to ejecting and wait for you to remove the medium at shutdown...
any other visible message/indication for an error or hangup?

perixx

---

### Post by volkswagner on 2008-01-06
I am having the same problem with shutdown on pentium 2 400mhz.  Worked fine in Win98.  Had harsh shutdown in Xubuntu 6.06 (but would power off).  I was trying to get WOL working so I performed a clean install of Xubuntu 7.04.  I see many people with shutdown issues in Xubuntu.  Found this thread helped others  I will try later today.

[http://ubuntuforums.org/showthread.php?t=397252&highlight=xubuntu+shutdown]("http://ubuntuforums.org/showthread.php?t=397252&highlight=xubuntu+shutdown")

Good luck

:)

---

### Post by volkswagner on 2008-01-06
Adding the following to my /boot/grub/menu.lst after the kernel line.  Works for me!

acpi=force



So it looks like this.

kernel          /boot/vmlinuz-2.6.20-15-generic root=UUID=e58815c0-850f-40b1-a410-3b4e79161326 ro acpi=force quiet splash

I also have an ACPI compliant BIOS and it is enabled.

What joy!

:)

---

