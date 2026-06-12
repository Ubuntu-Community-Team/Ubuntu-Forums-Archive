---
title: "LiveCD X won't start - Compaq nw8240 ATI FireGL 5000"
date: 2007-05-16
forum: Installation &amp; Upgrades
---

### Post by quietas on 2007-05-16
Howdy folks, finally getting around to dual booting Ubuntu on my laptop since I'm now using Ubuntu at work as well. Easy installs on the many computers I have used it on previously, I ran into a snag though on this machine. I'm sure it has to do with the ATI drivers for the newer x### based ATI Cards.

Here's the specs:
[LIST]
[*]Compaq nw8240 Mobile Workstation
[*]Intel Pentium M 770
[*]Mobile Intel 915PM Express Chipset
[*]ATI MOBILITY FireGL V5000 graphics controller with 128 MB of video memory
[*]Intel PRO Wifi
[*]1.5 gb RAM DDR2-5300
[*]80gb 5400 rpm
[*]15.4-inch wide screen
[*]... blah blah blah
[/LIST]

Here's the scenario; Feisty Fawn 7.04, laptop install attempt from cd. black screen when running the LiveCD.

I know the disc is good, I reinstalled from scratch on my old IBM T22 with a P3 600. It worked beautifully. When I load it on the Compaq I get the initial boot screen choices, I choose one, any of them really. I see the console text scrolling by as it loads, then it blacks out as X loads. I do here the startup sound though, so I know it is running. From there X is dead, I can Ctrl-Alt-FX between consoles, when I get to X I see a white bar on the left for a fraction of a sec then back to black.

Console access works great and I suppose a command line installer from the LiveCD would work great if it is there. 

Any ideas?

~Culley Morrow

---

### Post by quietas on 2007-05-16
I seem to have found the issue.

[http://ubuntuforums.org/showpost.php?p=2494165&postcount=2](http://ubuntuforums.org/showpost.php?p=2494165&postcount=2)

That post was exactly what I needed. A couple hours of searching here at work while I waited for my server install to grab and install the desktop resulted in no luck, 2 minutes after I ask for help I found it.

Thanks all.

---

