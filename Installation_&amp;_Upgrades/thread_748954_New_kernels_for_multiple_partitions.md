---
title: "New kernels for multiple partitions"
date: 2008-04-07
forum: Installation &amp; Upgrades
---

### Post by BrownieBoy on 2008-04-07
I'm currently quadruple booting between:

* Ubuntu Gutsy 7.10
* Ubuntu Hardy 8.04  (beta)
* Kubuntu Hardy 8.04 (beta)
* Windows XP

The Kubuntu partition was the last one installed, and so Grub's /boot/grub/menu.lst file resides there.  So far, so good.

When I upgrade that Kubuntu install to a later kernel, the new kernel appears in my boot list next time, and I can choose to run it or an older one.  My problem is that this is *not* happening when I install a new kernel for the Ubuntu Hardy install; the list of "other" operating systems remains locked to how it was when I installed Kubuntu, so I can only see the old kernel for Ubuntu Hardy.

Q1: is this normal?   I'm guessing that it is: only the "live" Grub install (i.e. the Kubuntu installation)  gets extra kernels added to its boot list automatically.

Q2: if I'm right, is there an easy way to get the other installations to find all their new kernels and get them added to the boot list, even though the menu.lst file is stored on another partition?

Q3: assuming "no" to Q2, how do I a)find and then b)add the new kernels for the "other" partitions to the "live" Grub partition's  menu.lst?

Thanks in advance for any help.

---

### Post by Oldsoldier2003 on 2008-04-08
> **BrownieBoy said:**
> I'm currently quadruple booting between:

* Ubuntu Gutsy 7.10
* Ubuntu Hardy 8.04  (beta)
* Kubuntu Hardy 8.04 (beta)
* Windows XP

The Kubuntu partition was the last one installed, and so Grub's /boot/grub/menu.lst file resides there.  So far, so good.

When I upgrade that Kubuntu install to a later kernel, the new kernel appears in my boot list next time, and I can choose to run it or an older one.  My problem is that this is *not* happening when I install a new kernel for the Ubuntu Hardy install; the list of "other" operating systems remains locked to how it was when I installed Kubuntu, so I can only see the old kernel for Ubuntu Hardy.

Q1: is this normal?   I'm guessing that it is: only the "live" Grub install (i.e. the Kubuntu installation)  gets extra kernels added to its boot list automatically.

Q2: if I'm right, is there an easy way to get the other installations to find all their new kernels and get them added to the boot list, even though the menu.lst file is stored on another partition?

Q3: assuming "no" to Q2, how do I a)find and then b)add the new kernels for the "other" partitions to the "live" Grub partition's  menu.lst?

Thanks in advance for any help.

Q1 yes this is normal
Q2&Q3 see this tutorial for an in depth explanation

---

### Post by Rocket2DMn on 2008-04-09
Oldsoldier, you forgot to link to the tutorial, buddy!

BrownieBoy, it is a little strange to dual boot between Kubuntu and Ubuntu Hardy - you can install two desktop environments on one system, then just choose which one you want from the login screen (under Sessions).  If you are worried about conflicting configurations, you could just create two different usernames, one for each session, but it shouldn't be necessary.
To install KDE in Ubuntu, run
```
sudo aptitude install kubuntu-desktop
```
and to install Gnome on Kubuntu, run
```
sudo aptitude install ubuntu-desktop
```
Check out these 2 pages for more details (newly updated with screenshots!)
[http://www.psychocats.net/ubuntu/gnome](http://www.psychocats.net/ubuntu/gnome)
[http://www.psychocats.net/ubuntu/kde](http://www.psychocats.net/ubuntu/kde)
Psychcats is a great resource, it is run by one of the forum mods, aysiu.

---

### Post by Oldsoldier2003 on 2008-04-10
ack- i missed the link to bodhi's extremely comprehensive tutorial. [http://ubuntuforums.org/showthread.php?t=724817](http://ubuntuforums.org/showthread.php?t=724817)

---

### Post by BrownieBoy on 2008-04-29
@OldSoldier

Thanks for the link.  I will take a look.



@Rocket,

Ubuntu + KDE <> Kubuntu.  There's a different file managers (Nautilus vs Dolphin), different package managers (Synaptic vs Adept)and so on.  Yes, I know that KDE apps will run under Gnome, and vice versa, but I wanted to see what Kubuntu actually *gives* you, rather than installing the KDE apps all in Ubuntu for myself.

---

### Post by Rocket2DMn on 2008-04-29
I know BrownieBoy, but what I'm telling you don't need a completely separate installation for Kubuntu.  Installing kubuntu-dekstop gives you the ability to run your session in KDE instead of Gnome.  This means you don't have to reboot the whole computer to switch between them, and you don't have to waste space with a double install since the systems are the same except for the desktop environment.  I am not saying to run KDE apps under Gnome, I'm saying to log out and choose KDE as your session and log back in, then you have your KDE desktop.  Same applies to getting back into Gnome.

---

