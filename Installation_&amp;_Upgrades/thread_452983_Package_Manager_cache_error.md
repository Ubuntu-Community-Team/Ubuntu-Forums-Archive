---
title: "Package Manager cache error"
date: 2007-05-23
forum: Installation &amp; Upgrades
---

### Post by GregoYatzee on 2007-05-23
I don't recall doing anything to cause this, but I get the following error anytime I use anything requiring Package Manager (add/remove, Synaptic and update manager):

E: Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse)
E: The list of sources could not be read.
Go to the repository dialog to correct the problem.

The update notifier icon gives me the following info when I mouse over:

A error occured, please run Package Manager from the right-click menu or apt-get on a terminal to see what is wrong.  The error message was: 'Error: Opening the cache (E:Malformed line 2 in source list /etc/apt/sources.list.d/edgy-universe.list (dist parse), E:The list of sources could not be read.)'

I followed those instructions, but was clueless as to what could be wrong.

---

### Post by mikewhatever on 2007-05-24
Can you post the output of the following command from the terminal
> cat /etc/apt/sources.list

---

