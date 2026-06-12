---
title: "realtime kernel 2.6.22-14-rt broke X"
date: 2007-10-15
forum: Installation &amp; Upgrades
---

### Post by raydar on 2007-10-15
UbuntuStudio (Gutsy release candidate) installed kernel 2.6.22-14-rt tonight, and X failed to start upon rebooting.  Went back to the generic version of the kernel and everything was fine.  Maybe more's to come that'll right it . . . .

(I'm running 2 monitors with the restricted nvidia driver & had had similar trouble before the Gutsy nvidia driver was ready.)

---

### Post by MetalMusicAddict on 2007-10-17
You're most likely missing the restricted modules. **sudo apt-get install linux-rt**

---

### Post by raydar on 2007-10-18
Many thanks--that solved it.

This was related to another issue, see [http://ubuntuforums.org/showthread.php?t=576537](http://ubuntuforums.org/showthread.php?t=576537) , so maybe I ought to give a little detail:

I'd received the kernel (whose description at [http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-14-rt](http://packages.ubuntu.com/gutsy/base/linux-ubuntu-modules-2.6.22-14-rt) indeed suggested not installing it by itself, but doing so via linux-rt) as a result of having to uninstall "audacious-plugins-extra" so that I could update it and "audacious-plugins."  Synaptic wouldn't let me uninstall the plugins without also uninstalling "ubuntustudio-audio," and after I did so and then ran the update manager for the new drivers, Synaptic showed "ubuntustudio-audio" and "audacious-plugins-extra" not installed.  When I then reinstalled them, the above-mentioned kernel got installed too, but without the "linux-rt" package.  

So for UbuntuStudio users, this could be a pitfall others might encounter if they run into the "audacious-plugins" and "audacious-plugins-extra" update problem mentioned in the that the above url.  If that is solved, then this should be solved too.

---

### Post by woodrow4821 on 2007-10-30
I ran into an issue with my wireless card after loading ubuntustudio-audio.  After finding this post I ran the **sudo apt-get install linux-rt** and that seems to have fixed it.

Thank goodness.  Music weighs pretty heavily on the scale but against the ability to connect to the outside world on my laptop...probably not.

Thanks, guys!

---

