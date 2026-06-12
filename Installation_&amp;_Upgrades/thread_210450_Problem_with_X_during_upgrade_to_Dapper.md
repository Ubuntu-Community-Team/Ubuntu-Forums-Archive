---
title: "Problem with X during upgrade to Dapper"
date: 2006-07-06
forum: Installation &amp; Upgrades
---

### Post by Elim on 2006-07-06
I decided to upgrade to Dapper yesterday.  I couldn't figure out how to upgrade via the Update Manager GUI, so I did it by hand (following [http://psychocats.net/ubuntu/dapper.php](http://psychocats.net/ubuntu/dapper.php)).  You're a lifesaver, aysiu.  So, I upgraded aptitude, changed my sources.list file, and ran dist-upgrade; all of that went without a hitch.  When I rebooted, the usual scrolling white text seemed to start okay, too.  I got all the way to the text login (something like username@computer), right before the GUI login pops up, when the screen blanked for a minute, then a very elementary dialogue box appeared.

The message read:

I cannot start the X server (your graphical interface).  It is likely that it is not set up correctly.  Would you like to view the X server output to diagnose the problem?
	<Yes>		<No>

Unfortunately, my keyboard will not work at this point.  I tried both, my USB and PS/2, and neither would function nor, even, light up (e.g. Caps lock and Num lock LEDs).  At this point my only option is to hit the power button on the monitor.

Thanks for your time.

---

### Post by linear on 2006-07-07
[LEFT]Are you sure dist-upgrade ran without a hitch? I ran into a similar problem, finally discovered that broken dependencies had prevented some upgrades from completing. The instructions [here]("http://www.ubuntuforums.org/showthread.php?t=186672") helped me fix things.[/LEFT]

---

