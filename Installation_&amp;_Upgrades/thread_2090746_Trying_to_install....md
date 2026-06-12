---
title: "Trying to install..."
date: 2012-12-03
forum: Installation &amp; Upgrades
---

### Post by anichols on 2012-12-03
Computer: Toshiba P870 Laptop
Drives: 2x 500 GB SATA
USB Boot: XUbuntu 11.10 Live USB

First attempt: Blocked by 'Secure Boot'...powered down by itself 1 minute later.
Second attempt: 'No bootable device -- Please restart system' (With the 750 GB drive with Windows on it, that was a given, but the USB stick's activity light didn't even try to light up this time)
Attempts 3, 4, and 5 using the other USB ports, one by one: Repeat of second attempt.

No BIOS logo, just black screen until the above results.
What can I do to get Secure Boot to disable itself, and then recognize the USB stick as bootable once again so I can get to installing XUbuntu on this machine?

Already tried, in an attempt to access the laptop's BIOS to turn off Secure Boot and alter the boot order: Holding F12 on boot, Fn+F12, F2, Fn+F2, F1, Fn+F1, ESC.... all any of this does is wait until 'No bootable device -- Please restart system' is on the screen...and then makes it spam its' way down the screen until the entire screen is full.

Sincerely,
Frustrated XUbuntu user on his ancient and about to crap itself out Gateway laptop.

Edit #1: (Adding more information)
  According to this site ([http://www.linlap.com/toshiba_satellite_p870](http://www.linlap.com/toshiba_satellite_p870)), this laptop is compatible with XUbuntu (with some caveats)...but I can't even get the Live USB to work...and making a Live CD is not possible.  My only other laptop lacks a working optical burner.

---

### Post by ibjsb4 on 2012-12-03
I do not own one, but got some forum hits that may/may not help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+P870&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+P870&as_qdr=all&sa=Google+Search&lang=en)

---

### Post by anichols on 2012-12-03
> **ibjsb4 said:**
> I do not own one, but got some forum hits that may/may not help.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+P870&as_qdr=all&sa=Google+Search&lang=en]("http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=Toshiba+P870&as_qdr=all&sa=Google+Search&lang=en")

No love there...though I find it interesting that two of the results were my own postings to ubuntuforms.org.  I'll have to keep googlubuntu.com handy before I make future postings, but my issue is still an issue.  And I would prefer to not take the laptop apart again to swap in the 750GB drive to load into Windows 8. *shivers in disgust at the thought*

Edit - Updating...
I decided to put the 750GB back in the laptop and try to get into UEFI once Windows has booted...so I can disable and reconfigure what I need.  Apparently I cannot get into it without a 'genuine Windows 8 bootable partition'.  Grr....

Edit -Updating...
It turns out the BIOS is completely borked, and when I tried to get Toshiba support to help me over the phone, they tried to shake me down for $159 to get a fix.  I told them where they could stick it, and hung up.  After I cooled down a bit, I went to their site, got a rep on their live chat, and demanded a full refund.  I'm not going with Toshiba ever again.  Marking this thread as Solved.

---

