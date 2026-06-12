---
title: "Adding packages to Ubuntu installation CD"
date: 2007-02-10
forum: Installation &amp; Upgrades
---

### Post by bash on 2007-02-10
As described in [this thread](http://ubuntuforums.org/showthread.php?t=356234), I have an old laptop on which I want to put Ubuntu. Since that thing is so old I decided to use the server install and then in the end just install a graphical desktop/window manager. 

Problem now is that that laptop only has a 56k dial-up connection and the windowmanager of my choice is Fluxbox since its small and fast and should still be able to run on that laptop. So my question is now how can I add the Fluxbox package to the installation .iso. I doubt that it will be enough to just add the .deb file to the CD and later just "dpkg -i /media/cd/fluxbox.deb" it. And besides that package, any other dependencies I need to get the desktop to work. Coz probably I have to install X as well. My point is just that I have the old machine with no Internet connection, and running a normal Live CD Desktop install won't work since this thing is just to damn old. Any solutions?

---

### Post by linear on 2007-02-10
Well, the process for customizing a LiveCD is described [here]("https://help.ubuntu.com/community/LiveCDCustomization/6%2e06"), but you'll have an uphill battle finding all the packages you'll need.

It might be possible, if you can find the packages, to load them on a second CD and use that as a repository - but I'm afraid I can't tell you how.

---

