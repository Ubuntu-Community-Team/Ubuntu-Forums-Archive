---
title: "A couple of Edgy upgrade mysteries"
date: 2006-10-29
forum: Installation &amp; Upgrades
---

### Post by joshua neff on 2006-10-29
I upgraded to Edgy last night. By far the easiest, best Ubuntu upgrade I've done yet. So, I'm happy.

But...now that I've upgraded, there doesn't seem to be any way to add or remove programs from the application menus. Did the latest Gnome change this? I was looking at the documentation at the Gnome site and didn't see anything about this.

Also, I only seem to have Firefox 1.5. Synaptic Package Manager swears I have Firefox 2, but everytime I load it up--Firefox 1.5. I even uninstalled it and reinstalled it, and it's still Firefox 1.5 that loads up. Has anyone else had this problem? Does anyone know the solution?

---

### Post by jabudia on 2006-10-29
Hi
program for maintaining gnome menues is, I think, "gnome-app-install". What you descrive happens to me also: this option on the menu did not work at all after upgrading to edgy, nor did some other option, like openoffice-presentation, firefox, apt,... no name it.

I corrected some, but many still don't work. Afte lots of researching I found everything boils down to a problem with python packages which do not install properly; this is what I get when running "apt-get install -f":
Errors were encountered while processing:
 python2.4-minimal
 python-numeric
 python-cairo
 python-gtk2
 python-gtkhtml2
 python-glade2
 python-apt
 unattended-upgrades
 python-vte
 update-manager
 gnome-app-install
 language-selector

Beleave me, your problem with some menu options is that the programs behind are not properly installed due to wrong installation on some dependencies.  

I know, I just described the problem, not the solution... but, you know, a well described problem is half the solution :D 

Hopefully some other colleagues can follow up with this. Bye.

---

### Post by joshua neff on 2006-10-29
> **jabudia said:**
> I know, I just described the problem, not the solution... but, you know, a well described problem is half the solution :D

Heh. Yep, it's a start. 

> **jabudia said:**
> Hopefully some other colleagues can follow up with this. Bye.

I hope so.

---

