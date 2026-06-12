---
title: "creating multiple users on separate partitions during install."
date: 2008-01-03
forum: Installation &amp; Upgrades
---

### Post by miravar on 2008-01-03
I have just installed Gutsy,

I wanted to create several user accounts, each on a separate partition, so that I would have control over where they actually were on the disk. I particularly wanted to do it during the install process, rather than afterwards. I am sure this used to be possible, but the Gutsy install process no longer seems to have a means of doing this. I was never even asked whether I wanted to have more than one user.

I had managed to create the multiple partitions all right, at the disk partitioning stage, but this turned out to be a mistake. Running the 'adduser' command after the installation was complete could not make use of the /home directories I had set up during disk partitioning. Instead, 'adduser' informed me that, although it had noticed the existence of the directories, it was not going to use them! 

How could I have done it?

---

