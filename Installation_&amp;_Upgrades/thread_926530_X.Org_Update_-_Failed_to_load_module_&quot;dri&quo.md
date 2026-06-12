---
title: "X.Org Update - Failed to load module &quot;dri&quot; (fixed)"
date: 2008-09-22
forum: Installation &amp; Upgrades
---

### Post by FJGamer on 2008-09-22
I got an update notification for x.org, in Intrepid, and I went ahead and updated. Everything seemed fine, but after a restart, I lost my resolution. I fixed that, and another restart locked me out of the GUI entirely, saying:

> (EE)Failed to load module "dri" (module requirement mismatch, 0)
I looked all over the net for a quick fix, but nothing helped. I played around for a while, and I just took the leap and uninstalled (and reinstalled) X.Org:

```
sudo aptitude remove xserver-xorg-core
sudo aptitude install xserver-xorg-core
```
This let me back into the GUI, and Ubuntu handled the rest on its own.:lolflag:

Basically, I fixed my own problem. I'm posting here just to help anyone looking for a quick solution. You don't really lose anything from the reinstallation. You do need an internet connection, though, to reinstall the packages.

---

### Post by LepeKaname on 2009-06-24
Thank you, that fixed also my problem. (just in case I reinstalled all the xserver-xorg packages that I had).

---

### Post by Kamargov on 2010-05-05
> **FJGamer said:**
> I got an update notification for x.org, in Intrepid, and I went ahead and updated. Everything seemed fine, but after a restart, I lost my resolution. I fixed that, and another restart locked me out of the GUI entirely, saying:


I looked all over the net for a quick fix, but nothing helped. I played around for a while, and I just took the leap and uninstalled (and reinstalled) X.Org:

```
sudo aptitude remove xserver-xorg-core
sudo aptitude install xserver-xorg-core
```
This let me back into the GUI, and Ubuntu handled the rest on its own.:lolflag:

Basically, I fixed my own problem. I'm posting here just to help anyone looking for a quick solution. You don't really lose anything from the reinstallation. You do need an internet connection, though, to reinstall the packages.

I tried that with Lucid Lynx and it worked. However, it created another problem as it corrupted fglrx and I could not access X, which meant I did not have a graphic interface.

Using the command line sudo apt-get install fglrx fixed the problem

---

### Post by anderoy on 2010-08-11
FJGamer,

I am so happy right now thanks to you. I was having problems with just about everything related to my graphics card after updating from 9.10 to 10.04. All of my fun desktop effects with compiz stopped working and any game I tried to load just laughed at me and failed to open. In trying to fix them I made a poor decision to install the fglrx drivers, which did more harm than good, and it took me another two hours to be able to uninstall the damn thing. Once I got it uninstalled, my computer went batty and I could only start my computer up in recovery mode.

By this point I just wanted to go directly to the GUI and I had basically forgotten about compiz. Then I tried your simple (I am fairly new to Ubuntu) solution and it not only brought me straight to the GUI, but the splash at the login menu was fancier AND my desktop effects started working again. You aren't the only one I should be thanking I suppose, but this is my first post and my way of saying thank you to the Ubuntu community for making seemingly impossible problems (fairly) easy to resolve.

Thanks!:D

Running:
IBM Thinkpad T40, 1.5mHz Intel M, 2gb RAM, ATI Radeon Mobility 7500 32mb, 60gb hard drive

---

