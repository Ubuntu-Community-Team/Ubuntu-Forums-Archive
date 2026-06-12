---
title: "How to install Debian testing, anyone?"
date: 2010-04-04
forum: Installation &amp; Upgrades
---

### Post by Laxman_prodigy on 2010-04-04
I wanted to check it out.
 
Anybody please help me. I want to install the minimum gnome environment.
 
Please suggest me in detail.:lolflag:

---

### Post by blueshiftoverwatch on 2010-04-04
I'm not sure what you mean by minimum Gnome enviroment. Theirs the standard install, the net install, and the snapshot install.

Standard and snapshot both come with the regular install. You install from the snapshot and than upgrade the packages if you want. But both come with all of the standard stuff.

If you only want to install the apps that you want, try the business card/minimum install or netinstall. I think they allow you to pick what packages you want during installation. But it would also require you to setup a lot of stuff by yourself I would assume, kinda like Arch.

---

### Post by Laxman_prodigy on 2010-04-04
Sorry, I could have been more specific.
 
I want to install Debian testing through netinstall and do not want to install full Gnome Desktop environment.
 
I do not want all those packages which I am never gonna use in future. Somebody suggested me to install the standard system on installing and later on gnome-core etc. but I couldn't figure out.
 
Anybody?

---

### Post by Laxman_prodigy on 2010-04-04
Anybody here installed Debian testing netinstall with minimum gnome packages?

---

### Post by cascade9 on 2010-04-04
This should help (yeah, I know they are talking about lenny, but from what I remember the process is the same)-

[http://www.raiden.net/print/articles/600/1/](http://www.raiden.net/print/articles/600/1/)

*edit- I havent done a minimal install with gnome, but I have with Xfce

---

### Post by Laxman_prodigy on 2010-04-05
> **cascade9 said:**
> This should help (yeah, I know they are talking about lenny, but from what I remember the process is the same)-

[http://www.raiden.net/print/articles/600/1/](http://www.raiden.net/print/articles/600/1/)

*edit- I havent done a minimal install with gnome, but I have with Xfce


Hi.

I have installed Debian testing netinstall  with minimum gnome(gnome-core).


But, what do I install or do to make sound working. I have soundcard and 4.1 speakers?
Also, how do I install Nvidia drivers?

---

### Post by NightwishFan on 2010-04-05
As for sound it should be similar to Ubuntu. Perhaps you need specific alsa firmware. Look around synaptic for it. I am unsure how to help you there.

To install Nvidia drivers is complicated. Here is the Debian specific way:
[http://wiki.debian.org/NvidiaHowTo](http://wiki.debian.org/NvidiaHowTo)
[http://wiki.debian.org/NvidiaGraphicsDrivers](http://wiki.debian.org/NvidiaGraphicsDrivers)

You could also do it the Nvidia way:
[LIST=1]
[*]Install the linux-headers package for your kernel.
[*]Download the Nvidia drivers from here and save them onto your desktop. [http://www.nvidia.com/Download/index5.aspx?lang=en-us](http://www.nvidia.com/Download/index5.aspx?lang=en-us)
[*]Log out and press Ctrl+Alt+F5 to get to a console. Log in as root. Run this command to stop GDM and Xorg. ```
/etc/init.d/gdm stop
```
[*]Change directory to your desktop. ```
cd /home/*username*/Desktop/
``` Then run this command to start the Nvidia installation. You may get a warning, however, just proceed with the installation anyway. ```
sh NvidiaFileName.bin
```
[/LIST]

Notes: Please change your username and the name of the Nvidia drivers above to fit their actual names, use the TAB key to autocomplete the name.

---

### Post by lisati on 2010-04-05
Moved to Installation/Upgrades

---

