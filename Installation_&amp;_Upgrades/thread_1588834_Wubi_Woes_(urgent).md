---
title: "Wubi Woes (urgent)"
date: 2010-10-05
forum: Installation &amp; Upgrades
---

### Post by ceverett on 2010-10-05
Lost my DJing laptop in a Beijing taxi.  Trying to whip my girlfriends Windows 7 laptop into shape to do some dates in Shanghai this weekend.

I'm running Wubi 10.04, on a DEl E6410 with a Core i5 processor, 2 GB RAM and the integrated Intel graphics.

First issue was the Wubi Black Screen of Uselessness.  I bypassed it by changing the linux boot line, removing "quiet nosplash" and putting in "nomodeset".

That helped, but now Linux crashes hard, with blinking numlock and capslock lights.  With the original setup, I could hear the sound Gnome makes when it says it's ready for me to login.

Please help, I have to get a working laptop going, and this Windows 7 box has severe latency issues I am not going to be able to work around without making this box useless for anything but DJing.

TIA for helping me get this hunk of junk going.

---

### Post by Rubi1200 on 2010-10-05
Well, you are not really giving us that much to go on, but I suggest you start by trying this:

[http://ubuntuforums.org/showpost.php?p=9927967&postcount=11](http://ubuntuforums.org/showpost.php?p=9927967&postcount=11)

Obviously, this has to be done from a LiveCD and please substitute the partition numbers with whatever is relevant for your machine. This fix is also applicable in your situation as far as I know.

Alternatively, if you installed via Wubi then restore the Windows bootloader:
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)

---

