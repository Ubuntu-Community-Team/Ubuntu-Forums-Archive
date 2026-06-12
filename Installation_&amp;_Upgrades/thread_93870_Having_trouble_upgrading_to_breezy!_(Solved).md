---
title: "Having trouble upgrading to breezy! (Solved)"
date: 2005-11-22
forum: Installation &amp; Upgrades
---

### Post by eric.stone on 2005-11-22
I'm trying to upgrade to Breezy via synaptic.  How do I set repositories to look for breezy vice hoary?  Thanks,
Eric:???:

---

### Post by Xian on 2005-11-22
From the Wiki: [How-To Upgrade To Breezy](https://wiki.ubuntu.com/BreezyUpgrade?)

---

### Post by eric.stone on 2005-11-22
Xian,
I started there.  When I open synaptic I can't find where to change from hoary to breezy.   I can't find anywhere in synaptic to execute step two (below)

#

Change your repositories to look for Breezy

    *

      From

         URI: [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
         Distribution: hoary
         Sections: main restricted

      To

         [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/)
         Distribution: breezy
         Sections:  main restricted

Thanks,
Eric

---

### Post by lorenco on 2005-11-22
Hi,  I have not tried the instructions above.  I tried upgrading from Hoary to Breezy twice...

The first time my X was gone, and had some niggles the second time around.

But try the steps above.

I also made some comments about having 2 Partitions [here]("http://ubuntuforums.org/showthread.php?t=87122")

---

### Post by eric.stone on 2005-11-22
Xian, Lorenco,
When you open synaptic, the instructions don't make sense.  Can you help?
E

---

### Post by fannymites on 2005-11-22
Open a terminal and type ```
sudo gedit /etc/apt/sources.list
```
Then look through all the text and anywhere you see the word hoary, change it to breezy and save.
Then open Synaptic, click on the reload button and go from there.

---

### Post by eric.stone on 2005-11-23
fannymites,
Great advice!   I'm downloading breezy now after swapping out "breezy" for "hoary" in the sources.list.   Thanks much,
Eric

---

