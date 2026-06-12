---
title: "Gnome/X lock ups"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by orb360 on 2008-05-27
I run an Intel QX6700, 4GB Ram, 8800GTX, etc.. so my system is fairly recent.

Previously I was running Gutsy (compiz and all), no problems.

I recently upgraded to Hardy, which initially screwed up my xorg and driver setup which I ironed out eventually (after upgrading a couple outdated packages).

Ok so now about 4 hours after booting and moderate use, Gnome stops  responding. All new apps launched just hang or don't even show a window. All previously running apps continue to work normally. The panel and desktop do not react to clicks (although the running man on the panel lights up on mouseover). The only way I can correct this issue it seems is to go to my first console, log in, and restart X (or shutdown restart the PC).

Any ideas on what might be going on?

I am running Prism apps, and it's usually when executing a Prism app that I first notice the symptoms, but not exclusively, and it's fairly random but usually within 4-6 hours of boot.

---

### Post by orb360 on 2008-05-28
Also, I'm running the 32-bit Ubuntu.

I tried installing the latest kernel upgrades... still have problems with it.

---

### Post by James_mtl on 2008-05-28
what is your video card ? I have the same problem with my laptop using Nvidia 7900.  After you restart X, look a the logs.  I usually just type dmesg in a terminal.  In my case I see a bunch of npviewer segfault and then Nvidia Xid.  I had this issue in Gutsy but it was resolved installing the Nvidia driver 169.12 from Nvidia.  This is the same driver I'm using in Heron but the problem is back ( i'm not using the one from Nvidia but the on in Heron ).  I might try installing the one from Nvidia, who knows.

Your problem might be totally different but it's a place to start.

---

### Post by orb360 on 2008-06-09
I have a BFG nVidia 8800GTX

I'll see if the dmesg turns up anything next time it occurs.

---

### Post by orb360 on 2008-06-21
Nope, nothing shows in dmesg for me.

Although, I did notice that the audio cuts out just before things go bonkers...

Mabye a problem with Pulse Audio?

---

