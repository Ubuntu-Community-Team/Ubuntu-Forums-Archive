---
title: "Fresh install without losing $HOME"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by wiggie on 2007-05-03
Is there a way to install Feisty from scratch, but without losing data in the home directory?

This question may sound silly, and I suppose the answer would be to just upgrade. The problem is, I have a tendency to clutter/gather up a lot of stuff, and I am not sure if it is like in Windows, where one needs to reformat every couple of months to have a healthy system. 

Please clarify me on this.

The other problem is, I have a lot of data, and backing it up is going to be a major pain.

Thank you, and because I like the "rock on" emoticon, I will use it

:guitar:

---

### Post by Churnd on 2007-05-03
Is Home on a different or the same partition as Root?  Don't know?  Do fdisk -l in the terminal and post it here.

---

### Post by wiggie on 2007-05-03
The same partition.

I didn't quite figure it out how to make multiple partitions, and i lost my patience; I just wanted a linux install as fast as possible. Now I regret not being patient.

---

### Post by Churnd on 2007-05-03
Yeah, patience is virtue especially in linux.

You'll lose your /home directory if you reinstall since it's on the same partition.  An alternative is you could try partitioning now with a live CD (such as Knoppix or Gparted) depending on how much free space you have left, and copy your data to that partition, then set it as your home directory when you reinstall.  However, repartitioning is always risky and you shouldn't do so without having a copy of your data first.

Or you could just upgrade.  Linux is nothing like Windows.  There is no registry to get cluttered up.

---

### Post by wiggie on 2007-05-03
gotcha, will do an upgrade. If that still won`t be as I want it to be, I will do a backup of my files, repartition and install

Thanks for the help

---

