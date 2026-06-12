---
title: "Dell Dimension 2400 - blank screen after login."
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by flipngenius on 2008-11-03
Hello!

I'm trying to install Ubuntu on my Dell Dimension 2400.

When done.  I get the login screen.  Only Failsafe xterm works.  Gnome or Gnome Failsafe gets me to a blank tan screen then a blank black screen.  Mouse cursor is visible and movable.

Any thoughts people?

Also on the media:  to ensure it wasn't the issue:

I downloaded and created two ISO images: default install and alternate install CD.
- I tried both: same issue.

I went to a second machine and downloaded and created two new ISO images: default install and alternate install
- I tried both: same issue.

Regards,
Flip

---

### Post by dmitriyp13 on 2008-11-03
Your problem might be related to the fglrx driver.  If you have an ATI video card, chances are you are affected.

---

### Post by flipngenius on 2008-11-03
I'll check and see.  

I did the following to get the screen up:

selected failsafe term
sudo apt-get remove compiz
sudo apt-get remove compiz-core
exit

What was the compiz and compiz-core app?  Do you know?

Regards,
Dave

---

### Post by dmitriyp13 on 2008-11-03
compiz provides a lot of the 'eye candy' (it makes pretty animations) in ubuntu.  you dont need it to get your system in a completely working state, but it is a nice to have.

---

### Post by flipngenius on 2008-11-03
Thanks Dmitriy for the explanation!  

Since this dell server has been given 2 gigs of ram and is here to serve up vmwares I think I'm ok.  

On my home laptop - which is pretty new and has a good graphics card -  I'll enjoy my eye candy there instead! :-)

Thanks again!
Flip

---

