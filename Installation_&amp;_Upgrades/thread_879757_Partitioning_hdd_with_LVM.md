---
title: "Partitioning hdd with LVM"
date: 2008-08-04
forum: Installation &amp; Upgrades
---

### Post by Lovok on 2008-08-04
I have LVM installed with Ubuntu 64 8.04.1. What I would like to do is install Ubuntu again, but without loosing my current install. I understand LVM can be used to resize partitions, so I want to shrink the one partition I have, add a second in it's place, and then install Ubuntu to it.

I don't seem to be able to find a guide that explains it to my level of (non)expertise ; in my mind, this should only take a few steps.

Thanks.

---

### Post by magnulu on 2008-08-08
I have more or less the same question in mind, so I will post it in this thread. Please excuse and feel free to correct any n00b typos/misinterpretations of the universe.

My setup & situation:
I have 7.10 installed, with LVM using my whole disk (500gb) as /. Me myself thinks this is a lot, but my plan was to do some research and use this to resize and make a setup that would make a clean install possible, without touching my data too much. I use the computer as a single user desktop, and personal files are in home folder, while music, movies, games etc are in respective directories under /usr

My problem:
I recently moved to an apartment with only wireless internet (my old one had the good ol' cable!), and I have trouble getting my wireless card working in 7.10 (yes, I have tried and tried, and ended up lonely and insane, with a cable). I figure the best solution is to do a fresh install of Hardy Heron, mainly because I have wanted to do that, and secondly because it is supposed to have better wireless support. 

I have bought another 500gb hd on sale, so keeping my data is no problem. However, I would like a set up like mentioned above: separate / and /home (and probably also /usr?). Any good ideas to how this could be solved with two 500gb disks? Should I use LVM, even though I feel that some of the documentation I found was just a little bit over my head? How much space should I allocate to the different partitions? Any other things to ponder? What would be the best alternative if I want an option to install m$ windows as well (you know, adobe premiere..)?

Sorry for long post, but needed to make my needs explicit! Thanks in advantage for all suggestions.

Cheers,
Magnus

PS! I'm not able to test any suggestions right now, as I'm on vacation. Just planning ahead, as I have no internet at home :-)

---

