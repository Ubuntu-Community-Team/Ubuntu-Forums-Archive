---
title: "Updater says Error: 'Fix broken packages first!' but no broken packages."
date: 2010-04-24
forum: Installation &amp; Upgrades
---

### Post by mattyd24 on 2010-04-24
My OS is Mint 8 (Helena) main, Gnome, but it is very similar to Ubuntu so I'm seeking some help here.

I've been trying to fix this problem  for quite a few days now and have done a lot of searching on these forums, Linux Mint Forums and some others Google lead me to and have has some  success, but am now stuck.

I have posted a thread on this same topic on the Linux Mint Forums, but have had no success (if you want check it out at: [http://forums.linuxmint.com/viewtopic.php?f=34&t=46343](http://forums.linuxmint.com/viewtopic.php?f=34&t=46343))

Originally I received error messages when  trying to update involving certain repositories which couldn't be  accessed (because they either didn't exist or had been moved) and I  hunted these down and changed or removed them.

Then I received  simply:
 E: Could not get lock /var/lib/apt/lists/lock - open (11  Resource temporarily unavailable)
which I somehow managed to fix  along the way.

Now I simply receive this:
Could not apply  changes!
Fix broken packages first.

I have done much  searching, etc. and cannot find any broken packages. I have tried many  many different commands which have mostly done nothing.
I seem to be  in a similar boat to this person: [http://forums.linuxmint.com/viewtopic.php?f=34&t=44949](http://forums.linuxmint.com/viewtopic.php?f=34&t=44949)
Please  help!

SOLUTION: See the above link for the solution, I simply had repos added for different dists, not knowing that this was bad.

---

### Post by zvacet on 2010-04-24
**Synaptic>edit tab>fix broken packages**

---

### Post by mattyd24 on 2010-04-24
> **zvacet said:**
> **Synaptic>edit tab>fix broken packages**

Thanks for your reply, I tried this already, but just to be sure I tried it again. It doesn't appear to do anything, then after a second it says at the bottom something like 'Fixed broken dependencies', but I still the same error message :(

---

