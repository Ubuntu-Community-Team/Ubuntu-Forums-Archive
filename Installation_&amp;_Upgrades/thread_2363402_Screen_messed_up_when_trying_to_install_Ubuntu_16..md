---
title: "Screen messed up when trying to install Ubuntu 16.04.2 LTS"
date: 2017-06-09
forum: Installation &amp; Upgrades
---

### Post by felipeaamacedo on 2017-06-09
Hello everyone!
I'm trying to get into Ubuntu, never used it before. My PC is really old, and I'm trying yo resurrect it! :D before buy another one. It is an HP, with AMD Turion(tm) 64 X2 TL-58 Processor, and a NVIDIA GeForce 7150M/nForce 630M. During the installation or while trying to test the system I'm facing up a problem, my screen gets all messed up, and I can't even read what's on it. I tried to find out how to fix it but I haven't gotten any solution yet. I'm attaching some figures that hopefully will show the problem.


Here when I press any key before gets to the installing page is everything alright,
[ATTACH=CONFIG]275552[/ATTACH]

However when I press to either test the system or install it starts to run alright,
[ATTACH=CONFIG]275553[/ATTACH]

But it gets weird after a second,
[ATTACH=CONFIG]275555[/ATTACH]

and the screen stays all messed up, not centered, like in those two last images.
[ATTACH=CONFIG]275554[/ATTACH]
[ATTACH=CONFIG]275556[/ATTACH]

I really appreciate the time and the effort for helping me!
Hopefully I'll starts to use Ubuntu soon!

---

### Post by LastDino on 2017-06-09
How much RAM do you have (From what I know of that model, it is around 1 GB)?

We may have a problem with that graphic card as well, but these should be cleared first.

You ought to start with Lubuntu on that system, not Ubuntu.

---

### Post by felipeaamacedo on 2017-06-09
Hello LastDino,
First, thanks for your fast reply!

It has 2GB of RAM, I was actually thinking about Lubuntu at first, but because I need to work with Lazarus, and I've never seen a video with Lazarus on Lubuntu, I changed my plans to Ubuntu.

---

### Post by LastDino on 2017-06-09
Core is same, so if it works on Ubuntu, it will on other Ubuntu based ones. Might be some dependency installing here and there but that is it.

With 2GB one can consider Xubuntu, so first, download Xubuntu from 

[https://xubuntu.org/release/16-04/](https://xubuntu.org/release/16-04/)

Use torrent link, doesn't matter if 32 bit, as your RAM is only 2GB it wont matter.

Check MD5 checksum after downloading

---

### Post by felipeaamacedo on 2017-06-09
I followed your advice about Xubuntu, downloaded it, however I ended up with the same issue :(


[ATTACH=CONFIG]275558[/ATTACH]

I wonder if it could be a Graphic Driver issue. Though, how can I install the driver without seeing nothing hahahahaha!

Thanks again

---

### Post by LastDino on 2017-06-10
Yes, that is why I said what I did in first post. 

Here is easy guide for setting "nomodeset" 

[https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076](https://askubuntu.com/questions/162075/my-computer-boots-to-a-black-screen-what-options-do-i-have-to-fix-it/162076)

Then do the installation, judging by this, this seems to be your first Linux installation, it will be good if you read up on gparted and Linux partition schemes before you try to dual boot.

---

### Post by felipeaamacedo on 2017-06-20
Hi LastDino, I'm returning to thank you for all support, I got my Xubuntu up and running last week with your last post! I took a while to get use to this new operate system, but I'm really enjoying it! Thanks you again!

---

