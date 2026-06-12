---
title: "Excluding a package when dist-upgrade'ing"
date: 2011-02-06
forum: Installation &amp; Upgrades
---

### Post by Koffeehaus on 2011-02-06
Is there a way of excluding a software package when issuing the 'apt-get  dist-upgrade' command? For example the newer 'pm-utils' packs are  incompatible with my hardware and my laptop starts to glitch. What I do  is I uninstall and replace the package every time I run 'sudo apt-get  update && apt-get dist-upgrade'. Which is kind of annoying. I  know that you can hide updates from the update manager, but what about  the terminal? I'm sure there are codes like "dist-upgrade [except  pm-utils]"

---

### Post by mörgæs on 2011-02-07
I don't know for sure, since I never do dist-upgrade, but you could try this:

[http://www.accessdataservices.com/blog/apt-get-hold-version/](http://www.accessdataservices.com/blog/apt-get-hold-version/)

---

### Post by Koffeehaus on 2011-02-07
> **mörgæs said:**
> I don't know for sure, since I never do dist-upgrade, but you could try this:

[http://www.accessdataservices.com/blog/apt-get-hold-version/](http://www.accessdataservices.com/blog/apt-get-hold-version/)

Excellent! Thanks Mörgæs, just what I was looking for!

---

