---
title: "Can we Change from 1 Flavor to Another?"
date: 2014-08-13
forum: Installation &amp; Upgrades
---

### Post by Rick St. George on 2014-08-13
Say I have UbuntuStudio installed but want to switch to Kubuntu or Xubuntu. Is there a command to initiate this or do we have to download another distro and do another complete Install ???

Thanks!
Rick

---

### Post by kc1di on 2014-08-13
Yes you can, 

say you want to install Xubuntu just do the following in a terminal ```
sudo apt-get install xubuntu-desktop
``` 
you can do the same for kubuntu, lubuntu , ETC.  if you should want Mate you can follow the instructions [here.]("http://www.webupd8.org/2014/03/how-to-install-mate-18-in-ubuntu.html")
then at the login screen you can select the DE you want. 

Good Luck :)

---

### Post by vasa1 on 2014-08-13
But do note that ...

You may end up with a more complicated menu tree and with more than one application for the same job. Also, and I'm not sure if this "feature" still exists, some users who installed several "flavors" found that it wasn't possible to see all the choices at login.

---

### Post by kansasnoob on 2014-08-13
> **vasa1 said:**
> But do note that ...

You may end up with a more complicated menu tree and with more than one application for the same job. Also, and I'm not sure if this "feature" still exists, some users who installed several "flavors" found that it wasn't possible to see all the choices at login.

+1!

It's really not as slick as it used to be. Like I've tried installing 'ubuntu-gnome-desktop' in Ubuntu and found that neither Unity or GNOME Shell perform very well (at least not compared to their out-of-box state) so in that case I prefer just adding 'gnome-shell-extensions' to Ubuntu which provides both GNOME Shell and the new GNOME Classic sessions.

Or if I want LXDE I install either 'lubuntu-core' or 'lxde-core' using the "--no-install-recommends" option. I'm not familiar with Xfce or KDE but I'm sure there are similar methods for all DE's :)

And, yes I've seen times with both gdm and lightdm with the unity-greeter where the session list extends beyond the bottom of the screen. It's better with the lightdm-gtk-greeter.

---

### Post by vasa1 on 2014-08-14
Here's another example of a mix-n-match gone wrong: [http://ubuntuforums.org/showthread.php?t=2239362](http://ubuntuforums.org/showthread.php?t=2239362)

It looks like OP had Ubuntu and then added Xfce. That's clear in posts #4 and #19.

---

### Post by kc1di on 2014-08-14
I'll admit it may have isssues - But haven't had the problems here some have suggested, Still the very best approach is to download each and burn to live media and try them all live for a day or so and make up your mind which one suits your personal taste the best. 
the only trouble I've had here is there is some interaction with Gnome3 and Unity.  when both are installed on the system. 
The other way would be to install them all in a virtual machine such as Viritual box and try them all that way for a while.  You'll find after a week or two that you tend to run one version over the others. and that's the one you should go with.

---

