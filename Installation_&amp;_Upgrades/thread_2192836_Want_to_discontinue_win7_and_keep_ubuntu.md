---
title: "Want to discontinue win7 and keep ubuntu"
date: 2013-12-09
forum: Installation &amp; Upgrades
---

### Post by steven0brock on 2013-12-09
Hi all,

I want to discontinue win7 on my laptop but keep my ubuntu 12.04 lts install.

Problem is...
I installed ubuntu in windows???
Looking at gparted I only have a NTFS partition and no ext3 partition?

Not sure how to post a picture showing gparted, the insert image button brings a a url ?

Here is a link to the picture:
[https://drive.google.com/file/d/0B94UJoOID2SIVVBqc3JFRkk4SnM/edit?usp=sharing](https://drive.google.com/file/d/0B94UJoOID2SIVVBqc3JFRkk4SnM/edit?usp=sharing)


Not sure if it is even possible to do what I want to do.....
Don't really want to lose my ubuntu install because everything works!

Thank you in advance for any help

---

### Post by Bucky Ball on 2013-12-10
You have Wubi. Not sure if there's a way to migrate a Wubi install to its own partition but that's where you should start your research.

[https://duckduckgo.com/?q=migrate+wubi+install+to+own+partition](https://duckduckgo.com/?q=migrate+wubi+install+to+own+partition)

PS: Ubuntu uses EXT4 by default now. ;)

---

### Post by steven0brock on 2013-12-10
Thanks Bucky Ball.

I am just going to go with a fresh install of ubuntu.
I am assuming that if wubi 12.04 works flawlessly on my laptop... then a full install from the 12.04 LTS iso should work as good...?

LOL at the EXT4 comment. Last time I used *nix was in the late 90's (mandrake) on a EXT3 file system, movin up in the world :p

---

### Post by Bucky Ball on 2013-12-10
Heh. Yea, 12.04 should work fine. Try Ubuntu from the install disk to have a shot. You might have wireless or graphics issues, but disregard. They can generally be fixed once installed (as they may need third-party drivers which can't be installed on the LiveCD). Good luck. ;)

Only thing you might need to have a bit of think about is how you're going to go about partitioning. You need / and a /swap partition at the least. A separate /home partition is often used also. In the case of the latter the / partition really doesn't need to be anymore than 20Gb (if that big), and /swap at 2Gb. /home for your personal data as big as you like.

---

