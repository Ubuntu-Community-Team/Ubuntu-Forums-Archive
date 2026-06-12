---
title: "kernel upgrade"
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by noorez on 2009-12-12
Hi,

I'm currently running ubuntu 9.10 and an update is currently available to the kernel image 2.6.31-16. 

The last time I tried to do the kernel upgrade, my graphics driver broke and the X server wouldn't start and the terminal screen started flickering nonstop. The problem was described here: [http://ubuntuforums.org/showthread.php?t=1305459](http://ubuntuforums.org/showthread.php?t=1305459)

Is there any way to prevent this from happening again? Is there a way to make sure that the nvidia driver can be smoothly moved to the new kernel image?

---

### Post by Shazaam on 2009-12-12
If you are using the drivers from the nvidia website you will have to re-install them after every kernel update. In the past versions of Ubuntu (Hardy, Intrepid) there was a script you could use (posted here on the forums) to reload the drivers but I don't know if it works with Karmic.

---

### Post by noorez on 2009-12-13
Hey,

So I tried to uninstall the nvidia driver using the installer I had downloaded from the nvidia website. The uninstaller told me it ran successfully.

However as soon as I had rebooted, I ran into exactly the same problem as I had before with the flickering terminal login screen. The only way I could get out of this was to boot into the recovery terminal and change the entry in xorg.conf from 'nvidia' to 'nv'. I was then able to boot successfully into the graphical login but the resolution was extremely small ( less then 800x600 ).

I do I reconfigure the X server so that the settings are all refreshed back to the default state?

---

