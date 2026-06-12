---
title: "Help please with damaged installation."
date: 2012-11-13
forum: Installation &amp; Upgrades
---

### Post by johnknott on 2012-11-13
Help please with damaged installation.

12.04 running on Dell poweredge server with raid an 4X dual Xeon. Came with  12.04, dont know how installed, dont know I could answer all hardware questions for full reinstall.
I have damaged the  installation by trying different desktops, gnome and cinnamon.


I have a working system but any file in desktop folder does not show on desktop Cinnamon available in logon chooser list but will not run. Cant install gnome classic broken dependencies .

Clearly I need to reinstall or repair.
 But poweredge has CD drive (not DVD), Floppy drive (dont even own floppy to test!) 

I have 12.04 DVD,  12.04 alternate CD, a USB cd/dvd reader that poweredge recognizes and can view  12.04 DVD.

How best to proceed to get to repair option?

Thank you John Knott

---

### Post by darkod on 2012-11-13
Hold on, you have the Server or Desktop OS installed?

If it's a desktop OS, does the default Unity login work?

---

### Post by vandorjw on 2012-11-13
Is there anything of importance on this machine?
Documents, source trees, videos, etc?

> 
Clearly I need to reinstall or repair.

We are not dealing with a microsoft system here.

Unity is based on Gnome3, and by default the desktop is kept "clean". If you would like gnome/unity to show files on your desktop, do the following.

install dconf

then go to org.gnome.desktop.background
and check "show-desktop-icons"

Broken package dependancies make sense.
Some Enviroments depend on older software libraries than others. It is not always possible with ubuntu to install the every single desktop enviroment on the same machine. Older packages will conflict with newer ones but the older cannot be removed because they are still needed. However, if you are no longer able to update your machine, then you do have a problem.

Just decide on a single DE and stick with it for a while. Most are perfectly fine, and just take some getting used to.

---

### Post by johnknott on 2012-11-13
> **darkod said:**
> Hold on, you have the Server or Desktop OS installed?

If it's a desktop OS, does the default Unity login work?
thanks
 desktop 32bit 12.04
 I can select Ubuntu from "Gear Wheel" everything seems ok 
but any file in desktop folder does not show on desktop

---

### Post by lykwydchykyn on 2012-11-13
Did you add any PPAs or non-default repositories when installing these desktops?

If so, you might want to install ppa-purge and remove all the non-default repos and their packages.

If I had to guess, nautilus is probably messed up somehow, which is why desktop icons aren't showing up.

You might check your ~/.xsession-errors file for nautilus-related crashes, too.

---

### Post by johnknott on 2012-11-13
Guilty will purge PPAs 
ok unity is "different" i guess i can live with it without loving it it is not classic linux but it launches what we want to do!

---

### Post by lykwydchykyn on 2012-11-14
> **johnknott said:**
> Guilty will purge PPAs 
ok unity is "different" i guess i can live with it without loving it it is not classic linux but it launches what we want to do!

Nothing says you *have to* live with Unity if it's not what you want, but if stability matters (and I assume it does on a server), I would stick with options readily available in the default repos and not go adding PPAs.  You especially want to avoid desktop environments that fork GNOME components (e.g. Cinnamon) since that overlaps with Unity.

If you want to save some CPU cycles and use XFCE, LXDE, or just a window manager of some sort, there shouldn't be any problem with that.

---

