---
title: "Ubuntu not compatible with SLI?"
date: 2008-02-07
forum: Installation &amp; Upgrades
---

### Post by sgt_ferret on 2008-02-07
I'm trying to install ubuntu 7.1 on my 64 bit Alienware laptop, but when I load the live CD, when I'm supposed to see the boot screen and then the desktop, I instead merely hear the music and see a black screen. The videocards are NVIDIA GeForce 7900 GS, in SLI.  Can anyone help?

---

### Post by macabro22 on 2008-02-12
That happened to me as well.

You have to start gdm in low graphics mode(for me, if I waited long enough a message would appear letting me choose that), install ubuntu and then reboot. If the system hangs at the boot sequence, alternate to another tty by pressing CTRL + ALT + F3 and run gdm.

Then install the latest nvidia drivers via the ENVY script. (Google for ENVY and Milone).

Edit your /etc/X11/xorg.conf to enable sli and you are good to go.

I think you can get more info about that last item on the nvidia drivers readme file.

Hope that helps you get started at least.

---

