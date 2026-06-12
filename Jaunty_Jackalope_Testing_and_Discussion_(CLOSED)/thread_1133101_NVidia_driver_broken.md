---
title: "NVidia driver broken"
date: 2009-04-22
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by xaenyx on 2009-04-22
My computer motherboard is by Zotac, and has an onboard GeForce 8800.  Now, initially, Xorg would turn on and it would work, but at the wrong resolution and without compositing.  I then installed nvidia-glx-173, and was able to get compiz working (and the right resolution)--however, there were some issues with a couple of programs, so I tried to update.

nvidia-glx-177 was unavailable in add/remove (it said that it wasn't compatible with i386?), so I tried downloading 180 from the nvidia website (my graphics card was listed as compatible).  I shut off Xorg (including gdm) and installed the 180 driver, ran nvidia-xconfig, and tried to start gdm.  The screen turned off an on a few times, and then crashed.  I also tried the v180 driver from the repos, and encountered the same problem.

Now I can't even get it back to where it *worked*.  I uninstalled nvidia-glx-180, and did dpkg-reconfigure nvidia-glx-173.  I also tried varying combinations of dpkg-reconfigure xserver-xorg and nvidia-xconfig (and also restoring my original xorg.conf file), but it won't even start Xorg now...  Any idea what's up?

---

### Post by cl333r on 2009-04-22
I would find the nvidia logs to try to figure out who's guilty (nvidia or the X server) and file a bug on launchpad and see what the ubuntu devs say about it. Till then use 8.10. Don't forget to report your arch (x32 or x64).

---

### Post by xaenyx on 2009-04-22
Nevermind, fixed it.  I did something like:

# nvidia-uninstall
# dpkg-reconfigure -phigh xserver-xorg
# gdm

# apt-get uninstall nvidia*
# apt-get install nvidia-glx-173
# nvidia-xconfig

(reboot)

---

