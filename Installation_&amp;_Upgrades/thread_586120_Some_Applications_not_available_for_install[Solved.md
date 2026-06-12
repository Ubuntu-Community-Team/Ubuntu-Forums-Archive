---
title: "Some Applications not available for install[Solved]"
date: 2007-10-22
forum: Installation &amp; Upgrades
---

### Post by notamonopoly on 2007-10-22
I made a fresh install of Gutsy which installed perfectly. Now I am going about installing all of the applications that I normally use from the add/remove menu. I noticed that some of the applications were not there. I went into preferences and made sure that all of the multiverse, restricted, partner options were checked but I still do not see them.

I am looking for Thunderbird specifically. There was another thread with the exact same problem and it was resolved when the person discovered that the partner line in the /etc/apt/sources.list file was commented out. I've checked my list and nothing is commented out.

I also tried Automatix as they usually have newer versions available but they don't have it either.

I would much rather use these channels than download and install directly from Mozilla.

I'm at a loss. Can someone suggest something, please.

Thanks

---

### Post by notamonopoly on 2007-10-22
I decided to try using apt-get and it installed successfully.

sudo apt-get install thunderbird

Now it shows up in the add/remove programs list, go figure.

---

