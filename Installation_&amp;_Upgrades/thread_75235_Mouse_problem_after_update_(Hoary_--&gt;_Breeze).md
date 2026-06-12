---
title: "Mouse problem after update (Hoary --&gt; Breeze)"
date: 2005-10-13
forum: Installation &amp; Upgrades
---

### Post by marmolro on 2005-10-13
Hi all,

after the update the mouse wheel don't work and I don't find the problem.

The Mouse section in xorg.conf:

[I]Section "InputDevice"
        Identifier      "Configured Mouse"
        Driver          "mouse"
        Option          "CorePointer"
        Option          "Device"                "/dev/input/mice"
        Option          "Protocol"              "ImPS/2"
        Option          "Emulate3Buttons"       "true"
        Option          "ZAxisMapping"          "4 5"
EndSection[/I]

Any idea of the problem?

Thanks,
Marmolro

---

### Post by metoo on 2005-10-13
This looks good, have the same here and it's running strong (even in UT2004 :-) ).

xserver-xorg-input-mouse installed and properly configured?

apt-get install --reinstall xserver-xorg-input-mouse

Best to delete the package in /var/cache/apt/archives if it is in there. This way you force a re-download, so be on-line!

---

### Post by marmolro on 2005-10-13
I delete the package in /var/cache/apt/archives and execute apt-get install --reinstall xserver-xorg-input-mouse but nothing...

I also download and try the live cd of Breezy and I have the same problem. The hardware is ok (tested in windows...).

Anybody knows how i can debug this problem?

Thanks,
Marmolro::

---

### Post by TrentAdams on 2008-07-19
I found a possible solution to this problem, as I had a similar problem.  After installing ubuntu 8.0.4, everything worked peachy.  Then, after updating all of the packages, the system would not boot.  To solve that, I edited the grub config by adding "acpi=off".

The next problem I had was the mouse was not working.  So, I went to the console (Ctrl-Alt-F1), to try and solve it there by editing xorg.conf.  No good.  So then, I rebooted as suggested, still nothing.  I rebooted again, and happened to notice on boot it complained about my pnpbios, and told me to enable "pnpbios=off" on the grub kernel line.  So, I did, and the mouse now works just fine.

---

### Post by TrentAdams on 2008-07-19
Oops, sorry, I didn't realize this was such an old post.  Maybe it should be moved to a new post?

---

