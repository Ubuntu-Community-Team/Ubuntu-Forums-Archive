---
title: "Ubuntu 10.04.2 LTS : How to upgrade to PHP 5.3.6?"
date: 2011-08-04
forum: Installation &amp; Upgrades
---

### Post by BillyBobThornton on 2011-08-04
Hi,

I'm running a Ubuntu 10.04.2 LTS server and I really don't know how to upgrade PHP to 5.3.6. I've tried by downloading source code and by recompiling it, but the installation did not replaced the former PHP installation but somehow screwed everything on my PHP server. 

Is there a Ubuntu package? I didn't find any.

And I'm not a *nix guru.

---

### Post by MrTuTu on 2011-08-06
Don't build PHP. Today, i see only 2 reasons to build something : if you are a developer or if you want to try something new and not stable (alpha or beta release).

I just downgrade my Laptop to Ubuntu 10.04 and found this repository for PHP 5.3.6:

In a terminal, try this:
```
sudo add-apt-repository ppa:bjori/php5
sudo apt-get update  
```

Then, you just need to install PHP (with Synaptic -> php5).
It is always better to look for a repository because you get new versions automatically and don't need every time to compile.

Enjoy !

MrTuTu

---

