---
title: "Minimum RAM????"
date: 2007-09-20
forum: Installation &amp; Upgrades
---

### Post by pieisgood4589 on 2007-09-20
Hello! I am trying to install Ubuntu Linux 7.0.4, as I have heard that it is very very good. The only problem is, I have 192 mb of RAM. Is this enough for an installation? Because this thing takes a bloody long time just to load up into the desktop.......... any alternatives? NOT XUBUNTU!!!:confused::confused:

---

### Post by linuxwizard on 2007-09-20
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

---

### Post by yabbadabbadont on 2007-09-20
It is enough if you use the alternate installation cd.  Once installed, you'll have swap space available, so it should be OK if you use XFCE, Openbox, Fluxbox, IceWM, or such as your window manager/desktop environment.

---

### Post by Pumalite on 2007-09-20
With that RAM, if you want a fast system>Xubuntu Alternate CD: 
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)

---

### Post by Herman on 2007-09-20
> Hello! I am trying to install Ubuntu Linux 7.0.4, as I have heard that it is very very good. The only problem is, I have 192 mb of RAM. Is this enough for an installation? Because this thing takes a bloody long time just to load up into the desktop.......... any alternatives?128 MB of RAM is enough for Ubuntu, I have installed Ubuntu many times in my old PC chips 'Book PC' with 128 mb of RAM, although I have upgraded it to 190 mb and now 256 mb.  You may even get away with less than that as long as you have the patience to wait a little longer each time you want to open something.
As the others have already said, Xubuntu or Fluxbuntu or other light desktops are will be faster if you like using those desktops, but I still prefer the Gnome Desktop even if I have to wait for it a little.
With that small amount of RAM, you will be relying on your swap area a lot, and I found that using the swapoff command (to umount the swap area before using Gnome Partition Editor) can slow the system down to a near frozen state. As long as you avoid doing something like that it will run okay though. That's about the only real problem I have noticed. It depends on other details about you hardware too though, like how much L1 and L2 cache your processor has and other things like that. When my Book PC only had only 128 mb of RAM it could still run Ubuntu better than other computers I have installed Ubuntu in for friends that have had 256 mb of RAM and more installed.

Here's a link about my PC Chips Book PC, in case you're interested, [Book PC Gets Big Power Supply]("http://herman543.googlepages.com/bookpcgetsbigpowersupply2")
That computer is the original computer that I used to test the 'Alternate CD' installers, and tricks with Linux bootloaders to make the Illustrated Dual Boot website. It has had every version of Ubuntu in it beginning with Warty Warthog 4.10, which was the very first version of Ubuntu, and now that it has a new power supply, the good ol' Book PC is still going strong! :). It will be ten years old soon, but it was second hand when I got it.

I would recommend the 'Alternate CD' to install with, but if you want to might be able to use the 'Desktop' Live/Install CD as long as you pre-partition first with a GParted LiveCD and make a swap area for the Ubuntu LiveCD to use. When there is a swap area on your hard disk, the Ubuntu LiveCD will work a lot better! :)
Look in my first sig link for a website about how to use the 'Alternate' Cd if you decide to use that.

Regards, Herman :)

---

