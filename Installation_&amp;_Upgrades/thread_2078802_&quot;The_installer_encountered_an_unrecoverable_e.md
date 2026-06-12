---
title: "&quot;The installer encountered an unrecoverable error&quot; when installing Xubuntu 12.10"
date: 2012-10-31
forum: Installation &amp; Upgrades
---

### Post by peyre on 2012-10-31
I'm trying to install Xubuntu 12.10 on an old laptop (HP Pavilion ze4125 w/80GB drive and 1GB RAM).  When I try to install it straight from the CD, after selecting a time zone I get "The installer encountered an unrecoverable error.  A desktop session will now be run so that you may investigate the problem or try installing again."  If I instead boot the live CD and double-click on Install Xubuntu, it starts, then (about the same distance into the install) kicks me back to Xubuntu running on the live CD, with a "busy" cursor symbol (but it just sits there, never completes the install).

I've had this problem before in earlier versions, so it's not new to 12.10.  Before, I got around it by installing using the Alternate CD, but now that's no longer an option.  Lubuntu used to always install on this machine, but I like Xubuntu a lot better.  Some have recommended booting to the live CD, then running sudo apt-get remove ubiquity-slideshow-ubuntu.  It says that's not installed, so I tried sudo apt-get remove ubiquity--which worked, but then double-clicking on Install Xubuntu gets me "Failed to run "ubiquity-gtkui.desktop", so that's a dead end.

---

### Post by ibjsb4 on 2012-10-31
You seem to be running the Athlon XP 1600+ cpu.  I have not been able to find any verification that it can run the PAE kernel that 12.10 comes with.

---

### Post by haresear on 2012-10-31
If you are trying to install the Xubuntu iso, and you want to remove the slide show first, look for the Xubuntu flavor of the slideshow, i.e. "ubiquity-slideshow-xubuntu".

---

### Post by peyre on 2012-11-01
> **ibjsb4 said:**
> You seem to be running the Athlon XP 1600+ cpu.  I have not been able to find any verification that it can run the PAE kernel that 12.10 comes with.

Dang!  I really like Xubuntu and it ran well on this thing before.  I hope it's not quite as hopeless as it's starting to sound.

---

### Post by ibjsb4 on 2012-11-01
If this is the problem, you can still run 12.04

[http://xubuntu.org/news/12-04-release/](http://xubuntu.org/news/12-04-release/)

---

### Post by peyre on 2012-11-01
> **haresear said:**
> If you are trying to install the Xubuntu iso, and you want to remove the slide show first, look for the Xubuntu flavor of the slideshow, i.e. "ubiquity-slideshow-xubuntu".

Of course!  Now why didn't I think of that?  It's simple enough it should have occurred to me.  Worked too!  So, for anyone else experiencing it, the thing to do is:

[LIST]
[*]Boot with the CD, and select Try Xubuntu.
[*]Open a terminal window, and type sudo apt-get remove ubiquity-slideshow-xubuntu.  When it's done, close the terminal window.
[*]Double-click on the Install Xubuntu icon.  Now the installer should run correctly.
[/LIST]

This is great.  Now if I can only figure out how to make it turn itself off--when I tell it to shut down or restart, it hangs before powering off.  It's been doing that since the 12.10 upgrade.

---

### Post by daedalas1981 on 2012-11-26
> **haresear said:**
> If you are trying to install the Xubuntu iso, and you want to remove the slide show first, look for the Xubuntu flavor of the slideshow, i.e. "ubiquity-slideshow-xubuntu".

I wish i read this thread earlier. I messed up my 12.10 O/S playing around with Compiz settings, after doing an upgrade. Tried re-install from the disk multiple times as everyone else did. But I did notice the first time that the installer crashed when i clicked on the slideshow... and that it hung up everytime the slideshow came on...but didnt think twice about it being the problem...ended up installing 12.04 and upgrading again from the alternate 12.04 disc.  :mad:

---

