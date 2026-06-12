---
title: "Deleting Packages"
date: 2005-03-23
forum: Installation &amp; Upgrades
---

### Post by HyperDevil on 2005-03-23
Hello everybody,

I have ubuntu running on my laptop for quite a while now and i really really love it!
The only distro where my cisco A/B/G wireless card works  =P~ 
At this moment i want to delete some unused packages from my laptop.
When i do apt-get remove gnome-games and reboot.
The whole Ubuntu Desktopenvoirement is gone...  #-o 
Why cant i just delete the package games for example?
Anyone that has an answer to do this?
Every package that i find unusable for me i want to delete but apt then wants to delete ubuntu desktop to  [-( 

Help!  :-o

---

### Post by az on 2005-03-23
Ubuntu-desktop is a metapackage.  You do not need it to run the ubuntu-desktop - just to install it.

It is a bunch of dependancies.  If you remove one of the dependancies, it removes the meta-package, but not its' other dependancies.  Don't worry.


Anyway, it is really really hard to bork up your system likie that.  You would have to remove libc6 or something.  It will ask you about seven times if you are sure before letting you do that.

Even if you end up not being able to get back into Xwindows (for some reason you remove xserver, or something), you can still type

apt-get install ubuntu-desktop

and get everything back.

---

### Post by wernst on 2005-03-24
If you're looking to just clear out old .DEB files and unused packages, do:

sudo apt-get clear

It cleared off close to a gig of stuff after I updated from Warty to Hoary.

-Warr

---

### Post by ubuntu_demon on 2005-03-24
But it's more handy if you wait with removing packages that break ubuntu-desktop untill hoary gets released because that way if something new gets into main you'll get it too when you dist-upgrade (although it isn't very likely new things will pop up)

---

