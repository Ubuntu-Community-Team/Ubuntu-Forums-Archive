---
title: "Getting upgrades when not connected to internet"
date: 2007-02-11
forum: Installation &amp; Upgrades
---

### Post by frobro390 on 2007-02-11
Hello everyone,

First post and I am stuck.  I have a laptop that simply is not going to be able to connect to the internet.  I have a USB wifi device that I need to get working.  The version of ndiswrapper on the 6.10 dvd I burned is not working w/ my windows drivers and I need to compile a newer version.  When I make on ndiswrapper I get errors up the backside and I need guidance.

I'm assuming it's because other packages on the install are out of date and won't work w/ the new ndiswrapper, but not sure.

So question is, how can I get updated packages to my crippled laptop?

---

### Post by itsmabus on 2007-02-11
I tried for a long time to do things like this, because I was in the same situation as you for months with my laptop.

There really just is no easy way; the easiest being to go on an ubuntu computer with the internet, use synaptic to download the package files only, and then put them on removable media and install them with dpkg on your unconnected laptop.

Otherwise, you'll have to get all the dependencies manually, and that is never fun. Especially if you don't already have build-essential.

---

