---
title: "Synaptic and Update Manager"
date: 2005-06-05
forum: Installation &amp; Upgrades
---

### Post by Leav on 2005-06-05
Not sure if this is the correct forum, so be kind to me if it isn't  :) 

First Let me Point out that i'm almoist a complete linux newbie so, again, please be non-brutal...

1)my friend who is helping me into the deep end of the computer world has stressed that it is very important that i install everything from synaptic, is this the correct approach?
2)how do i update firefox? i'm using 1.0.2 because the newer versions havn't shown up on synaptic yet...
3)same as above for Gaim.
4)when I install new programs, such as games, through synaptic they do not show up in the "Gnome menu" (i'm not sure of the real name, i'm talking about the linux equivalent of the "start menu"...)

that's it for now....

Thanks for helping the newbie!
-Leav

---

### Post by netrattler on 2005-06-05
Yeah installing your programs with Synaptic is a good way, there is also apt that you can use with a Terminal. But use what works best for you

For firefox and gaim I use the backport repositories for this and have version 1.04 for firefox installed and the latest gaim. If you want to add the backport repositories to your /etc/apt/sources.list file do this.

1)Click Applications -> and select Run Application... -> type this gnome-sudo gedit and press the Run button.

2)Now click File -> Open -> double click Filesystem -> double click etc -> double click on apt -> and double click on sources.list -> now add the following to the bottom of your file.

## Backports
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-backports main universe multiverse restricted
deb [http://ubuntu-backports.mirrormax.net/](http://ubuntu-backports.mirrormax.net/) hoary-extras main universe multiverse restricted

3) Now click on File -> Save -> and close gedit out

4) Now open up Syanptic and click the Reload button and click the Mark All upgrades button and select the default upgrade or smart upgrade. Then you can just click the Apply button to apply all the new updates.

Now for start menu thing not everything will be added to it automatically you can either install a program like smeg which is the simple menu editor for gnome which will allow you to do it yourself. Or there is another solution if you really want everything added to a menu then you need to install a package called menu. Basically what this does is add a debian menu to your Applications menu which will add anything that you install or have installed under this Debian menu. Some people like and others dislike it. Here is the link for the howto if your interested in it.

[http://www.ubuntuforums.org/showthread.php?t=32220&highlight=debian+menu](http://www.ubuntuforums.org/showthread.php?t=32220&highlight=debian+menu)

Hope this helps,
Joe

---

### Post by Leav on 2005-06-05
yes! this was very helpful! thanks! :)

Thank you for taking the time to detail the steps of editing the sources.list file  :grin: 

-Leav

---

