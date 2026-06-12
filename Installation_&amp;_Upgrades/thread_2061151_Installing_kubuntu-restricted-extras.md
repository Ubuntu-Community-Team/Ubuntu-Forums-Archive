---
title: "Installing kubuntu-restricted-extras"
date: 2012-09-21
forum: Installation &amp; Upgrades
---

### Post by pwabrahams on 2012-09-21
On one of my machines I'm running Kubuntu 12.04 (32 bit).  I needed to install kubuntu-restricted-extras.  I wanted to do it with Synaptic, but I couldn't figure out what **deb** line needed to be added to the repository list. (It of course had to start with **deb** and include **kubuntu-restricted-extras**, but I didn't know what else was needed.)

So I tried doing it directly with **sudo apt-get install kubuntu-restricted-extras**.  That seemed to go all right at first, but then I had a truetype licensing page come up on the screen -- with no indication of how to accept it.  At the bottom it said <OK>, but pressing Enter didn't make it go away.

So I have two questions:

1. What would be the correct **deb** line?

2. How can I get past that pageful of licensing text?

---

### Post by jerrrys on 2012-09-21
Thought that got fixed, guess not

[http://ubuntuforums.org/showthread.php?t=1709419](http://ubuntuforums.org/showthread.php?t=1709419)

---

### Post by whatthefunk on 2012-09-21
Im pretty sure that to accept the licencing agreement, you need to press one of the arrow keys to highlight the OK field and then enter.

---

### Post by pwabrahams on 2012-09-22
I tried reinstalling kubuntu-restricted-extras, but since it was already installed, nothing happened.  So I never had the opportunity to test your suggestion.  But thanks anyway!!

---

### Post by oldos2er on 2012-09-22
Try ```
sudo dpkg --configure -a
```

kubuntu-restricted-extras is in the multiverse repository, which should be enabled by default in /etc/apt/sources.list

---

