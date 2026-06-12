---
title: "Upgraded to 10.10 - Can't start Gnome"
date: 2010-10-11
forum: Installation &amp; Upgrades
---

### Post by mrteatime on 2010-10-11
I've just upgraded my PC from 10.04 to 10.10 using the update manager. After the system asked me to restart it rebooted into a command line login, and any command I type to start Gnome brings up errors.

Any version of gdm comes up with 'Failed to acquire org.gnome.DisplayManager'

startx seems to have a problem with the Nvidia drivers ie 'Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so'

When I restart the computer the Gnome loading screen starts and then it gives a list of errors the only one I can make out being 'no usable aperture found' then loads the command line login.

Im sure Im missing something simple so any help would be appreciated. Cheers.

---

### Post by gatorbrit on 2010-10-13
> **mrteatime said:**
> I've just upgraded my PC from 10.04 to 10.10 using the update manager. After the system asked me to restart it rebooted into a command line login, and any command I type to start Gnome brings up errors.

Any version of gdm comes up with 'Failed to acquire org.gnome.DisplayManager'

startx seems to have a problem with the Nvidia drivers ie 'Failed to load /usr/lib/xorg/extra-modules/nvidia_drv.so'

When I restart the computer the Gnome loading screen starts and then it gives a list of errors the only one I can make out being 'no usable aperture found' then loads the command line login.

Im sure Im missing something simple so any help would be appreciated. Cheers.

I have the same problem.  10.10 is not loading the correct nvidia drivers (I think).  
Any ideas?

---

### Post by mrteatime on 2010-10-13
I managed to solve it by deleting the nvidia drivers from the command line. It works ok although there are some occasional minor graphics glitches. There is no longer a driver for my card in the drivers option, and I cant get nvidias legacy driver to install. I think I just have to accept the fact that my (8 year old) graphics card is too old.

To be far windows 7 wont run at all with it so I cant really complain.

---

### Post by gatorbrit on 2010-10-13
Solution is here...

[http://ubuntuforums.org/showpost.php?p=9949419&postcount=9](http://ubuntuforums.org/showpost.php?p=9949419&postcount=9)

---

