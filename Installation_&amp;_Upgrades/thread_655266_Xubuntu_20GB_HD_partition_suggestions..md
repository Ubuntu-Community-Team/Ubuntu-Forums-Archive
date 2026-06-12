---
title: "Xubuntu 20GB HD partition suggestions."
date: 2008-01-01
forum: Installation &amp; Upgrades
---

### Post by c0reyf on 2008-01-01
Subject says it all, I'm setting up an old laptop for my son that is basically just for web/email, a few games/education from the synaptic and a gig or two of music for him to listen to.

System:
P3-700mhz
20GB
128MB

I was thinking 5% for root and double RAM for swap?

1GB root
512MB swap

Thoughts?

---

### Post by Pumalite on 2008-01-01
You need at least 7 GB for '/' (root), and have to install this:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
Or this:
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
7.10 uses more memory. Remember you are sharing your RAM with graphics.

---

### Post by c0reyf on 2008-01-01
I'm getting ready to use the Xubuntu Gusty Alt install because the live CD wouldn't work.

Ouch!! really 7GB for /root? What about swap?

---

### Post by Pumalite on 2008-01-01
The rule is 2x RAM up to 1 GB for /swap.

---

### Post by c0reyf on 2008-01-01
Just out of curiosity how did you come to 7GB for the /root?

---

### Post by Pumalite on 2008-01-01
It's a matter of proportionality. Also 'root' gets filled up pretty quickly. If you intend to keep the programs installation to a minimum, you could make it 5 GB.

---

