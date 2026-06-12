---
title: "ATI Radeon X700 PRO wont work"
date: 2005-05-14
forum: Installation &amp; Upgrades
---

### Post by 25738 on 2005-05-14
ubuntu worked great with my computer's on board video (intel).

then i installed an ATI radeon x700 pro, and all i get, even after a re-install of ubuntu is the blue screen saying, among other nasty things, "no screens". 

i found another thread that seemed to address this issue, (sort of), but all the fixes there assumed Xfree86; my version of ubuntu, which i downloaded and burned less than 4 weeks ago, installs xorg.

even the ubuntu live cd, which worked great before, hangs at "logical volume ...".

anyone else have this problem and know what i should do, or where i can find some howto information?

other info: computer is intel D915GAV motherboard, Celeron 2.5Ghz, 1Gig ram, SATA 200gig HD with windows XP on one partition.

thanks, 

rod

---

### Post by 25738 on 2005-06-03
I found another thread where someone said he had this problem when he went from Warty to Hoary, so I tried the following:

First I got the warty live cd, and X worked fine. So I downloaded Warty and installed it, but X fails: 'no screens'. So i rebooted the live cd and copied its /etc/X11/XF86Config-4 onto the hard disk.

This will not enable any of the graphics acceleration, but at least I can start X, search the web, use Synaptic Package Manager, etc.

rod

---

### Post by sunscape on 2005-07-08
I had the same problem and it was easily fixed by using the vesa driver instead of ati. I have no idea why, but use the vesa driver to get x started and then install and configure the the latest fglrx drivers.

---

### Post by GazaM on 2005-07-08
I have had big problems with my X700Pro, very similar to yours. As sunscape says, use the vesa drivers to get into X. To use vesa, just type 'dpkg-reconfigure xserver-xorg' in the terminal when you are left there after X fails to start, then select vesa for the driver and all other appropriate settings. Do NOT try to use any fglrx versions, even the latest, as you will be left at a black screen and then must go into recovery mode to change back to vesa. The only way I have 3d acceleration working is to install the latest fglrx drivers from ati's site, then configure 2 xorg.conf files using fglrxconfig, one with dri disabled and one with dri enabled. I have to enable the one without dri when shutting down so that I can boot without a lockup, then when in X I just replace the xorg.conf with the dri enabled one and press ctrl+alt+backspace to restart X and I then have 3d until I must shutdown. This is due to differences in the way fglrx is loaded with and without dri, so hopefully it will be fixed in the next release. If you want to know more feel free to IM me on msn prefferably, my address is in my profile.

---

