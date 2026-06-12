---
title: "X11 crash using fglrx when I setup multiple screens"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by egandt on 2011-04-29
After the installation I have 3 screens setup, on DVI, HDMI (to DVI) and DisplayPort this is using and AMD HD5570 video card.  With this configuration mirrored everything is fine and I can see all three displays.  However having 3 copies of the same display is worthless, so I want a separate desktop per display.  This is when everything goes wrong, after making the change to have 3 displays it fails to work, ie it crashes with the message below (full log is attached as well).  

Now I can use any 2 monitors independently with the third one mirrored, but I can not have 3 independent monitors configured on the card without X crashing.  The exact same config, did work fine in Windows (where I verified the setup).

Backtrace:
[   352.624] 0: /usr/bin/X (xorg_backtrace+0x26) [0x4a2626]
[   352.624] 1: /usr/bin/X (0x400000+0x6219a) [0x46219a]
[   352.624] 2: /lib/x86_64-linux-gnu/libpthread.so.0 (0x7f21c8aaf000+0xfc60) [0x7f21c8abec60]
[   352.624] 3: /usr/lib/xorg/modules/drivers/fglrx_drv.so (0x7f21c5006000+0x8ec2bf) [0x7f21c58f22bf]
[   352.624] 4: /usr/lib/xorg/modules/drivers/fglrx_drv.so (0x7f21c5006000+0x8ebe1d) [0x7f21c58f1e1d]
[   352.624] 5: /usr/bin/X (0x400000+0x1451b2) [0x5451b2]
[   352.625] 6: /usr/bin/X (0x400000+0x145301) [0x545301]
[   352.625] 7: /usr/bin/X (0x400000+0x143d58) [0x543d58]
[   352.625] 8: /usr/bin/X (miPointerUpdateSprite+0x18c) [0x45b5dc]
[   352.625] 9: /usr/bin/X (mieqProcessInputEvents+0x199) [0x4a2009]
[   352.625] 10: /usr/bin/X (ProcessInputEvents+0x9) [0x46c6d9]
[   352.625] 11: /usr/bin/X (0x400000+0x2e023) [0x42e023]
[   352.625] 12: /usr/bin/X (0x400000+0x21a7e) [0x421a7e]
[   352.625] 13: /lib/x86_64-linux-gnu/libc.so.6 (__libc_start_main+0xff) [0x7f21c79f8eff]
[   352.625] 14: /usr/bin/X (0x400000+0x21629) [0x421629]
[   352.625] Segmentation fault at address (nil)
[   352.625] 
Caught signal 11 (Segmentation fault). Server aborting
[   352.625] 
Please consult the The X.Org Foundation support 
	 at [http://wiki.x.org](http://wiki.x.org)
 for help. 
[   352.625] Please also check the log file at "/var/log/Xorg.0.log" for additional information.


I have a second x1300 video card which I could use in addition to the 5570, but the ATI driver does not recognize it.  Any ideas?

---

### Post by pedro.flynn on 2011-04-30
Hi egandt.

    I'm not an Ubuntu user, I'm a Slackware user, but I think I'm facing the same problem as you. I've upgraded my Slackware box from 13.1 to 13.37 yesterday and then the bug appeared. I also have a three monitor setup (but I have 2 x 4850). I've filled up a bug report in the Unofficial AMD Linux Bugzilla (bug 117):

[http://ati.cchtml.com/show_bug.cgi?id=117](http://ati.cchtml.com/show_bug.cgi?id=117)

I found some other users with the same problem. 
  The awkward part is that I noticed that everything works well if I setup the default desktop environment to KDE, but the bug shows up with any other different desktop/window manager (like XFCE or Fluxbox).

---

### Post by egandt on 2011-05-03
Solved: The problem is that Compiz causes the crash, switching to genome classic without effects fixes the issue.

ERIC

---

