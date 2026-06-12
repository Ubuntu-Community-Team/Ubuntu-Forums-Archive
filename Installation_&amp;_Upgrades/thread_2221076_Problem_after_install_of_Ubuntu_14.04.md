---
title: "Problem after install of Ubuntu 14.04"
date: 2014-04-30
forum: Installation &amp; Upgrades
---

### Post by dvlnchrs on 2014-04-30
Ok, so I've installed 14.04 (clean install) and it seems to have worked fine, and tells me to restart for the updates to take.

When it reboots though, after the initial Ubuntu logo, the screen either stays black screen or gets to the desktop and freezes or the screen tears and I can't do anything.

Help!

I'm thinking it's the graphics drivers not installed (they are onboard Nvidia 7025/nForce 630a chipset)

Thanks in advance

---

### Post by kc1di on 2014-04-30
Hi dvlnchrs,

When ubuntu just begins to boot hit the left shift key. this should bring you to a screen that has several f key options at the bottom.
hit F6 from that menu select nomodeset and hit the esc key followed by enter.  this should get you to the login and gui But you won't be using the correct driver for your card so the resolution may only 600x800 or so.  next go to a terminal and install Nvidia-304 driver like this ```
sudo apt-get update && sudo apt-get install nvidia-304
``` logout and back in it should work.

---

### Post by dvlnchrs on 2014-05-02
Hi kc1di,

Thanks for replying.

I found the shift method, but worked it slightly differently. Choosing boot in recovery mode, then resume boot, which got me round that bump.

I've installed the graphics driver now and that's working ok...

However, now I'm trying to get ndiswrapper to work, so I can install the wireless driver for my netgear WNA3100.

I've installed ndiswrapper, but it doesn't seem to be showing or I can't find it. So, I'm currently trying to figure out this at the moment...

---

### Post by dvlnchrs on 2014-05-02
Ok, so for the ndiswrapper problem, I had to install gksu.

Then add ndiswrapper to this via gksu gedit /etc/modules, reboot and ndiswrapper was accessible.

Then the driver bcmn43xx64.inf.

And hurrah so far I think all good...

Next on the menu, I may have to uninstall the graphics drivers and install new ones when I place the HDD back into my PC...

---

