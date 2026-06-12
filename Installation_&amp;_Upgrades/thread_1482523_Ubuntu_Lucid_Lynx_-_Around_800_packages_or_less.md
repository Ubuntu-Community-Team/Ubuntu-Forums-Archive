---
title: "Ubuntu Lucid Lynx - Around 800 packages or less?"
date: 2010-05-13
forum: Installation &amp; Upgrades
---

### Post by Linkert on 2010-05-13
I want a slim USABLE/HUMAN Ubuntu system. That's the trick, your grandma should be able to use it. 

The way I want to reach my goal is by installing the basic cli ubuntu install and then adding the rest.

So I'm thinking gnome with all the admin features the normal LiveCD install have, and only firefox and the terminal installed as far as applications go.

Guides? I have seen one for 8.04, but I had problem with the GUI after logout (long story). What I learned from the tutorial is that it really isn't extremely much to do if you want to achieve this, the problem is that the tutorial was outdated or just not adapted for Lucid Lynx. (haha no i'm a noob)

How would you go about doing this?

---

### Post by wojox on 2010-05-13
Here's a good start:

```

sudo apt-get update && sudo apt-get install 
gdm xorg gnome-core gnome-codec-install 
indicator-session-applet update-manager 
firefox-3.6.3 gnome-themes 
network-manager gdebi

```

I'll warn you though it's pretty ugly until you pick your themes and what not loaded.

---

### Post by Linkert on 2010-05-13
> **wojox said:**
> Here's a good start:

```

sudo apt-get update && sudo apt-get install 
gdm xorg gnome-core gnome-codec-install 
indicator-session-applet update-manager 
firefox-3.6.3 gnome-themes 
network-manager gdebi

```

I'll warn you though it's pretty ugly until you pick your themes and what not loaded.

Thank you :)

I'm gonna try this out in VMware Fusion. Installing the basic ubuntu cli right now. And i'll just add whatever is gonna be needed for good ole grandma to start rocking the computer. (i'll ask what the packages names are :P)

---

### Post by Linkert on 2010-05-13
indicator-session-applet could not be found. Any replacement?

---

### Post by wojox on 2010-05-13
It should be indicator-applet-session

Sorry bout that.

---

### Post by Linkert on 2010-05-14
Got it running! (VMware atm, will try on machine soon)
You really get a good feeling when I know this install is just as functional as a LiveCD install but with something like 350-400 less packages. I think the feeling is called, control :)

---

