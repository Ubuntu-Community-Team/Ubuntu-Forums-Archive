---
title: "Video Anomaly Help Needed"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by ti1ion on 2007-02-11
Hi folks.  I have a small issue that is annoying me every time I fire up the machine.  I posted a similar question on linuxquestions.org and got some good suggestions, but I am still looking for help.

For background information, I ran Dapper on my P3 laptop with ATI Mobility video card.  Everything was fine.  No video problems.  I did install some themes to make the desktop prettier.

Upgraded to Edgy after reading every upgrade guide I could find and followed the official instructions.  Everything upgraded fine, as far as I could tell.  However, now when I log into Gnome, or KDE using GDM, or KDM, I get a small square appearing in the top left corner of the screen.  It stays there until I open a terminal and type something.  Then it disappears and everything is fine.  It will also disappear if the screen goes to sleep and then I wake it up, or I open the right number of tabs in Firefox, or whatever else the system feels like responding to.

I tried re-configuring xorg.conf to no avail (including changing the depth from 24 to 16 bits.  With some playing around I found the following:  

Changing the video driver to VESA removed the square, but the driver is so painfully slow I can't use it.  I installed XDM for a different reason and the block no longer showed up!  But, XDM is useless without a shutdown icon so I removed it.  Not using a login manager and starting X from the shell gives no square on the screen.  If I can figure out how to make the system shut down using CTRL+ALT+DELETE, I could live with using this method.  Changing the -r to a -h in inittab did nothing.  

So, that about covers it, I think.  I am going to try to include a small picture of the square.

Any suggestions are welcome.

---

### Post by ti1ion on 2007-02-14
Well, at least I found information on where to modify the ctrl+alt+delete function to allow me to shut the PC down.  So, I can avoid seeing that square, but have to log in without GDM/KDM.

What's the best way to make Ubuntu do a fresh install of GDM and related packages?

What's the best way to make Ubuntu install a newer version of the ati driver?  I forced an install of the Debian ati driver, but it broke Synaptic.  One thing that bugs me is how finicky the package management system is.  If I tell the system to remove GDM, it wants to remove Gnome!

Any tips on properly installing and removing individual packages?

And, generally speaking, are there any guides to removing obsolete packages?  If Edgy no longer uses inittab, is it safe for me to remove it?

---

