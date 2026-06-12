---
title: "Set Ruby 1.9 as standard"
date: 2008-11-06
forum: Installation &amp; Upgrades
---

### Post by gary_emms on 2008-11-06
I'm not sure whether this is the correct forum for this so please bear with me.

I've installed Ruby 1.9 and would like to use this, along with gems and IRB1.9 as the standard on my PC(instead of 1.8).
I don't want to remove 1.8 (the list of programs that synaptic wants to delete is too long for me to take the chance).
How do I set it so the plain command 'Ruby some program' or IRB launches Ruby 1.9 and gems runs the correct version for 1.9?

Thanks for your help
Gaz

---

### Post by guigs on 2008-11-06
There is the symlink /usr/bin/ruby that points to ruby1.8.
I guess you'll just need to make it point to ruby1.9

---

