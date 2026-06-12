---
title: "software center issue in Xubuntu 13.04"
date: 2013-07-10
forum: Installation &amp; Upgrades
---

### Post by goodbye-windows(tm) on 2013-07-10
I just got done installing Xubuntu 13.04, and starting loading necessary software (from my notes). 

The problem happens when I try to install 'gnome desktop utilities'. 

Gnome Desktop Utilities is necessary (for me) as the stock search utility that comes with Xubuntu (Catfish) is nearly useless. Catfish finds hte files, but after the files are located, nothing can be done with them (AND ALSO) individual files that meet the criteria of the search cannot be selected (only one file can be selected at a time). 

So, I NEED 'Gnome Desktop Utilities' for it's search function even though it is NOT a 'stock' Xubuntu program.

Here's what happens when I try to install from the Software Center.

I locate the program in the Software Center search function without difficulty. However, after clicking on it to bring up the install dialog box, the install dialog box is missing from the screen!!! The dialog box is always on the right hand side of the screen, but now it is missing!!!! So, I can't download and install it.

I have attached a screen capture showing the missing 'install' link.

All the other non-stock programs that I run with Xubuntu appear normally and are installable from the install link in the Software Center.

I do not know if this is a 13.04 only error, or whether it is a recent error that also occurs in older versions as well.

Any ideas what's going on???

TIA

Art

---

### Post by The Cog on 2013-07-10
No idea. But it you can get the software centre to tell you the package name, you might be able to install it with the command:
sudo apt-get install whatever-package-name-is

---

### Post by Toz on 2013-07-10
If you click on the "More Info" button, it looks like the package is no longer available. According to [https://apps.ubuntu.com/cat/applications/quantal/gnome-utils/]("https://apps.ubuntu.com/cat/applications/quantal/gnome-utils/"), the 13.04 entry seems to lack the information the earlier versions do, so I'm wondering if it no longer exists.

However, if you look at the 12.10 entry, you'll see what individual packages made up the meta-package. All those individual packages exist in the repositories so you can install them all individually or just the one that you want (gnome-search-tool).

---

