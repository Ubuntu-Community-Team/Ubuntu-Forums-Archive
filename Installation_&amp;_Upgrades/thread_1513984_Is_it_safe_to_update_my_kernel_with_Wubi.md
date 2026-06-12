---
title: "Is it safe to update my kernel with Wubi?"
date: 2010-06-20
forum: Installation &amp; Upgrades
---

### Post by elijahthehun on 2010-06-20
I've seen quite a few posts saying that after updating the kernel in Wubi installs, GRUB gets messed up. This has caused me to hold off on the HUGE list of updates in my update manager (I have never updated since I first installed 10.04, and this was just over a week ago). Are these updates important enough to potentially risk something bad happening? What is the risk of updating? Is this an issue with all Wubi installs?

Sorry if I'm in the wrong forum.

---

### Post by warfacegod on 2010-06-20
The only real way to figure out the risks is to do it.

Security updates, in Linux, aren't as important as they are in Windows but they're still a good idea. You'll occasionally see folks here saying that they don't do updates because they can cause problem. They sometimes have and can but I still don't subscribe to that philosophy. It's like having a safe full of cash and leaving part of the combination taped to the door.

Wubi was never intended for anything more than temporary use. It's a way to try Ubuntu not use it permanently. I would imagine that is partly due to wubi's tendancy to break with updates. Consider making a separate partition for Ubuntu.

---

### Post by darkod on 2010-06-20
Most issues happening with grub2 are when actually doing UPGRADE from wubi 9.10 to wubi 10.04.

Since you have wubi 10.04 these are just UPDATES and I think you should be safe.

However, I would like to point out that wubi was always meant as only a short term install, a quick try. It is best to move to full ubuntu installation as soon as you decide you like it enough. Wubi is working inside windows and when trying to make an OS to work inside another OS issues will happen, sooner or later.

It's best to move to full ubuntu, if you like it, before you have too many things you would like to keep from wubi. Because I'm not sure you can keep anything except of course copying your personal files.

---

### Post by elijahthehun on 2010-06-20
I would make a separate partition, but my laptop is a Dell so it has all of the pointless partitions like MediaDirect, recovery, and some other one. Apparently there's some 4 partition limit that computer dummies such as myself do not know about. I'd delete the MediaDirect partition, but I'm not sure how safe it is.

---

### Post by warfacegod on 2010-06-20
[http://www.goodells.net/dellrestore/mediadirect.htm]("http://www.goodells.net/dellrestore/mediadirect.htm")

---

### Post by elijahthehun on 2010-06-20
That doesn't really help me in that I want to know if it will mess anything up if I delete the MediaDirect partition.

---

### Post by warfacegod on 2010-06-20
Do you use Mediadirect's functions? If not, then you can do away with the partition.

---

