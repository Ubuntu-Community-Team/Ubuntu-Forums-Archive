---
title: "New Install Feedback and problems"
date: 2010-12-06
forum: Installation &amp; Upgrades
---

### Post by hertzog on 2010-12-06
I installed xubuntu to an ancient laptop earlier this week. Just in case it's helpful, here's my experience of it.

The install went fine - really fast, no errors, and all devices installed. Dual booting with windows XP, which didn't get broken in the process, but did want to do a disc check on first boot, presumably because the xubuntu install added partitions and shrunk the XP partition.

First problem: 

Horrible intermittent wireless connection fault. Some pages on some sites seemed to load fine, others would partially load and then pause forever. Some pages would fully load on hitting refresh, others wouldn't. Some pages on some sites were totally inaccessible always. Couldn't get to Google at all!

I tried a few things, but the problem turned out to be the atheros wireless driver for my chinese made Netgear WPN511 card installed by xubuntu as default. Installing ndiswrapper and using the netgear windows 2000 driver on the netgear install disc fixed it instantly.

Second Problem:

Tiny, almost unusable right hand scroll bar on Firefox. Fixed by adding a 'run as root' command to Thunar file manager to enable editing of xubuntu themes (in usr/share/themes/themename/gtk-2.0/gtkrc) - lots of trial and error and careful notation of what I changed finally did the job. It seems that the themes used by xubuntu carry on to the theming of Firefox. 

Other than that, everything has been just hunky-dory and I am delighted with it. It runs much better than XP on this old laptop...

I am liking the Ubuntu Software Centre a great deal. Who said linux is hard work?

---

