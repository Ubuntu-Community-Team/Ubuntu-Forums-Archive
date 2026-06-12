---
title: "Tidying up after yourself packaging"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by mikeym on 2007-05-26
Hi,

I have recently been doing a bit of packaging from source and I'm a bit unclear as to what I actually need to keep on my system afterwards. Can I remove any packages on my system with the word -dev in them? 

What step should I take to keep a tidy system?

PS I've been using checkinstall for most of my packaging.

---

### Post by merlinus on 2007-05-26
You can try this from a terminal:

```

sudo apt-get autoclean
sudo apt-get clean
sudo apt-get autoremove

```

Good luck!

-merlin

---

### Post by mikeym on 2007-05-27
cheers, 

Can someone tell me then if I can clean up my pcakages with -dev after their name?

---

### Post by pbw on 2007-05-27
Sure, in terminal just enter dpkg -l *-dev to see what devel packages are installed on your system and remove whatever you like.

-- pbw

---

