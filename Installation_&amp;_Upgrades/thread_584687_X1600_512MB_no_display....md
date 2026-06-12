---
title: "X1600 512MB no display..."
date: 2007-10-21
forum: Installation &amp; Upgrades
---

### Post by Tsume on 2007-10-21
**SOLVED**

**drama1981 in the freenode IRC channel #ubuntu just helped me figure out the problem.  Apparently, this card does not like the vesa driver.  Unfortunately, Ubuntu detects this card as "Generic Video Card" and uses vesa instead of detecting it as "ATi Radeon X1600 Pro" and assigning it the ati driver.  This can be fixed by running "sudo dpkg-reconfigure xserver-xorg" and choosing not to autodetect, and instead pick the ati driver.  Hopefully they decide to fix the detection of this relatively common card.**

I have no display output on my x1600 Pro 512MB PCIe edition...

I tried the LiveCD... it loads, and when the bar is 100% it goes black and doesn't go back.  You hear the startup noise and everything go.

I did the alt install and as soon as it loads X the screen goes black (you never see X).  I can get to console just fine.  It looks like I am having the same problem as this person: [http://ubuntuforums.org/showthread.php?t=579053](http://ubuntuforums.org/showthread.php?t=579053) except my card is PCIe.  Must be the large amount of memory on these cards?

Note, I am using AMD64.  My chipset is an Intel P965.  I have tried from the console sudo apt-get install xorg-driver-fglrx and sudo apt-get install xserver-xgl to no avail.  This Ubuntu install is located on the same drive as Vista.  Grub works fine.

---

### Post by Tsume on 2007-10-21
This reply is so people will not disregard this thread for having 0 posts and forever not know the solution.

Solution is above.

---

