---
title: "Need advice on installing Xubuntu over Ubuntu"
date: 2012-04-08
forum: Installation &amp; Upgrades
---

### Post by dkolars on 2012-04-08
Running Ubuntu 11.04 (Natty Narwhal) and will NOT upgrade to 11.10 because of Unity!!  Put XUbuntu 11.10 on my laptop and like it a lot!  Since my laptop is not my main "working" computer (used only when I travel), I simply installed XUbuntu over Ubuntu, deleting all my data, programs, settings, etc.  then re-loaded Chrome, Krusader, etc. and copied the settings that I could see on my desktop, imported bookmarks, etc.  Not too hard. 

BUT, with my desktop, I want to SAVE all my programs, settings, etc.  I popped in the Disc and attempted to install it alongside Ubuntu, but it wants to put it on one of my external drives.  I don't ~want~ it on my external drive!  

So, is there a procedure for switching OS and keeping the existing data/programs/links/etc./etc.???  A list of directories to save so that all my settings can be put back into the programs?  etc. etc. etc.

TIA....

---

### Post by PhantomTurtle on 2012-04-08
I pretty sure if you upgrade from 11.04 to 11.10 using the update manager, the programs you have come with it. Also after you upgrade Ubuntu, install xubuntu-desktop(if you had not already in 11.04). If you had xubuntu-desktop package installed on 11.04, that will also be upgraded.

---

### Post by Bucky Ball on 2012-04-08
If you don't want to add the Xubuntu packages, just the desktop environment, install xfce4 from Software Centre/Synaptics. That will install the desktop environment used by Xubuntu only. ;)

---

### Post by jerrrys on 2012-04-09
You should be able to upgrade in terminal.

sudo do-release-upgrade -d

But keep in mind upgrades can break.

---

### Post by dkolars on 2012-04-09
Thanks for the replies...  however, the point that obviously didn't get made clear enuf was that I want to CHANGE my OS to Xubuntu...  When I installed it on my laptop, replacing Ubuntu 11.04, I noticed that it loads quicker, it runs faster, etc., etc., etc.

So, once again, I need to be able to SAVE my current Ubuntu (customized by me) program settings so that when I uninstall Ubuntu and install XUbuntu, I'll be able to (sort of) pick up from where I was.   There is nothing in the install settings, or that I've found on-line, that lets me believe that any upgrade will preserve what I have when I change the OS from Ubuntu to Xubuntu.

So, any hints?

---

### Post by Elfy on 2012-04-09
Your program settings are all in your home in hidden files/folders.

Back them up and copy across.

I did the same thing a year ago - copied the necessary things and then put them back in a clean install.

I also copied my fstab and a couple of other system files.

When you do the install it is likely that you want to use the something else option - this will allow you to pick where to install to.

---

