---
title: "Cirrus Logic graphics adaptors ?"
date: 2005-07-03
forum: Installation &amp; Upgrades
---

### Post by wookie on 2005-07-03
I'm trying to install 5.03 on an old NCR server with twin P/Pro 200 MHz CPUs.

I seem to be able to get most of the install done OK, and it even offers me a choice of plausible looking screen resolutions during the install, but when it comes to starting X, it fails and asks if I want to see details of the error.

Even if I ask to see the details, there seems to be no reall account of the problem encountered, just an anouncement that an attempt to start X was made.  It then stops X, mucks about installing some more stuff, tries starting X again which fails again, and so it loops interminably.

I'm assuming this somewhat deranged behaviour is possibly down to the [lack of ?] driver support for this chipset which is seen by the previous OS (windows 2000) as a Cirrus Logic 64xx / 542x.

Is this chipset supported, or have I actually found something that windows does better than linux ?

I guess I could just make this a server install and do without X, but I'd rather not, and am happy to look at all options including the use of a remote networked x terminal if that's easy to set up ?

Un fortunately I can't upgrade the video chipset as it's soldered firmly to the motherboard, and I can see no way to disable it either by hardware jumper or through the bios.

Any help / comments much appreciated !


Many thanks, J/.

---

### Post by wvslkr on 2005-07-04
Try running > sudo dpkg-reconfigure xserver-xorg   
Choose the cirrus driver.  If it doesn't work try the vesa driver.  You may also have to change the color depth from 24 to 16.

If you still have problems post the xorg.conf file and your monitor.  It should work under linux.

Some info on the chipsets.  It's dated but will give some relevent info.
[http://www.xfree86.org/3.3.6/cirrus1.html](http://www.xfree86.org/3.3.6/cirrus1.html)

---

