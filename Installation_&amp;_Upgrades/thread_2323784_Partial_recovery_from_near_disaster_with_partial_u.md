---
title: "Partial recovery from near disaster with partial upgrade after 16.04 install"
date: 2016-05-08
forum: Installation &amp; Upgrades
---

### Post by cigtoxdoc on 2016-05-08
After a near disaster (almost non-working PC after partial upgrade), I got my laptop (DELL Vostro 3500) working with Gnome desktop.  On a reboot a couple of days later, I found the following options on login>
Gnome Default
Gnome Classic
Gnome Flashback (Compiz)
Gnome Flashback (Metacity)
Ubuntu

Okay, I am back with Ubuntu desktop.  I really have no use for any of the Gnome desktops except for what ever can keep me going if the Ubuntu desktop (Unity) crashes without a way to recover.  How do I clean up my laptop?

Also, my normal desktop colors don't show all features.  Have to use Adwaita for scroll bars on evolution 3.19.90 to show up.

Thank you,

John

---

### Post by grahammechanical on 2016-05-08
Do you have Synaptic Package Manager installed? Synaptic is useful because whenever we install or remove a package it will tell us what other packages are to be installed or removed as dependencies. We can make sure that something important like ubuntu-desktop is not going to be removed. Or if it is we can re-install it afterwards.

Gnome Classic is an extension of Gnome 3 shell. So, when we install Gnome Classic we also get Gnome 3 shell as a dependency. So, removing gnome should remove the Gnome & Gnome Classic options. I have Unity + Gnome Flashback and Synaptic shows me that gnome is not installed. So, it should be safe to remove.

As you can see, with Gnome Flashback we get a Metacity option. This is useful to have for any time we have a problem with Unity + Compiz. We will still be able to log in to a Metacity session. And make repairs from a desktop environment instead of having to do it from a Linux console.

Regards

---

