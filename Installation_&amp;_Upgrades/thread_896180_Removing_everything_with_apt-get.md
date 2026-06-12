---
title: "Removing *everything* with apt-get?"
date: 2008-08-20
forum: Installation &amp; Upgrades
---

### Post by Igtenio on 2008-08-20
I'm not sure if this's even possible, but I figured I'd ask...

Is it possible to remove everything, minus a few packages, without having to specify them individually in apt-get?

Here's my current predicament;

I'm making a script that applies certain templates of packages to a machine. I'd like to include an option to remove everything but the command-line installation that's at the base of every Ubuntu installation and variant. And I mean *everything*.

Would this be possible? Is there some argument or method I'm missing?

I essentially want the equivelent of this;

apt-get remove --purge * +ubuntu-standard

---

### Post by Vivaldi Gloria on 2008-08-20
You must go the other way round. First install a base system and add the packages you want. See the first link in my sig.

---

### Post by Igtenio on 2008-08-21
The issue isn't making a minimum system. I know how to go about installing a Command-line System and adding packages.

I need to go the *other* other way. :P

I'm just checking if it's possible, mostly. It'd be nice to include an option that strips the current installation down, but even if it's possible, I imagine it'd be better to do a fresh install.

Doesn't stop me from wanting to add it. :P

Push comes to shove, I can get a package list for each major variation and remove that.

---

