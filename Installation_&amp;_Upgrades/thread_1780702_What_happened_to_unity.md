---
title: "What happened to unity?"
date: 2011-06-12
forum: Installation &amp; Upgrades
---

### Post by Mazate on 2011-06-12
I just burned the live CD to check out the unity desktop before installing and its Gnome 2.  Did I download the wrong iso?

---

### Post by coffeecat on 2011-06-12
Probably not. With some video chipsets, the live 11.04 CD will fall back to classic gnome because either the card cannot support the 3d acceleration needed to run Unity, or you need to install another driver. Older cards are the commonest cause of the first, but all (most) nvidia cards will not display the Unity desktop because they need either the proprietary nvidia driver or an experimental package to augment the capabilities of the default open source nouveau driver.

What is your graphics card? Also, if you want to be sure which ISO you downloaded, in the live session post the terminal output of:

```
cat /etc/lsb-release
```

I presume that is 11.04/Natty you downloaded?

---

### Post by Mazate on 2011-06-12
> **coffeecat said:**
> Probably not. With some video chipsets, the live 11.04 CD will fall back to classic gnome because either the card cannot support the 3d acceleration needed to run Unity, or you need to install another driver. Older cards are the commonest cause of the first, but all (most) nvidia cards will not display the Unity desktop because they need either the proprietary nvidia driver or an experimental package to augment the capabilities of the default open source nouveau driver.

What is your graphics card? Also, if you want to be sure which ISO you downloaded, in the live session post the terminal output of:

```
cat /etc/lsb-release
```I presume that is 11.04/Natty you downloaded?


Yep, Natty/11.04 it is.  My graphics card is a 9600GT, which should be more than sufficient.  I'm currently using Fedora 15 but I'd like to switch back to Ubuntu but I want to be able to try the unity desktop on the live cd but for some reason its showing me gnome2.  If I install anyway, will it install unity or gnome2?

---

### Post by cbowman57 on 2011-06-12
It will install Unity as well as Gnome, to access Unity though you will have to install either the experimental open source Nvidia, or proprietary driver.  It should automagically pop up an icon in the notification area to do that, if not look for 'Additional Drivers' in your menu, and run that.  When you login after installing the driver just select Ubuntu (Unity) desktop.

---

### Post by coffeecat on 2011-06-12
Yes, that card should be more than sufficient. But you'll have to install the proprietary nvidia driver or the experimental package once you've made you permanent installation. When you install 11.04, you will install both gnome2 and Unity. Unity is merely a compiz plugin working in gnome2

I'm not sure whether this will work, but try this from the live CD. Boot into the live desktop (which will be classic gnome), open Synaptic and enable the Universe repository. Click on Reload to download the package metadata. Now install the package libgl1-mesa-dri-experimental. It will, of course, be installed only to RAM so will lost when you power down, but it will be interesting to try.

You now have to logout and in again. Click on the shutdown button (top-right) to logout and at the login screen type "ubuntu" (no quotes) for user. Before you do the password, look at the bottom of the screen - there's a choice of desktops. Make sure "Ubuntu" and not "Classic" is ticked. Now you can enter the password, which is nothing at all - i.e. simply press enter. This *might* get you into the Unity desktop.

If that works, when you make a permanent installation, you'll have the choice of the proprietary driver or the "experimental" one - the package you've just tried out - in Jockey (Additional Drivers).

---

### Post by Mazate on 2011-06-12
Ok, I did the full install and after installing the proprietary driver, unity works just fine.  Thanks to all that helped me out on that.

---

