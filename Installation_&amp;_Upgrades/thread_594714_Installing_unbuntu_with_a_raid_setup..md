---
title: "Installing unbuntu with a raid setup."
date: 2007-10-28
forum: Installation &amp; Upgrades
---

### Post by Xanthius on 2007-10-28
Well, i downloaded the iso and burned it to disc, and everything went smoothly.
So right now, ubuntu is loaded from the disc.

But i have an issue with installing concerning that i already have Windows XP and Fedora on my hard disc.
This is my hard disc setup:

2 discs 120 gb Raid 0. -> 1 Discs 240 gb.
 20 gb : Windows Partition
 20 gb : Fedora partition
 20 gb : Fedora swap partition
 180gb : Ntfs Data ( for windows ).

Since i have loads of issues with fedora, errors etc.. i want to remove fedora from my computer and install ubuntu on its place.
But when i'm in the installer of unbuntu ( guided ), it does not detect any operation system on the hard disc.
Better yet, it does not see the raid setup, because both discs are detected as 120gb.

So i guess here is the issue, since it does not read the raid setup.
So if i'm right on this one ( pretty sure about it ), there is no use in removing the 2 operation systems and install ubuntu first since it doesn't detect the raid.

So i anyone here who knows how to let ubuntu see my raid setup?
I don't know if it matters much, but i have an asus k8v deluxe SE motherboard.

Note: i know the swap partition is a bit over the normal use, but iat the time i installed Fedora, i didn't know what to do there.
That partion, if it can be changed.. can goto 2gb, and the remaining to the Linux partition.

---

### Post by Pumalite on 2007-10-28
[https://help.ubuntu.com/community/FakeRaidHowto](https://help.ubuntu.com/community/FakeRaidHowto)

---

