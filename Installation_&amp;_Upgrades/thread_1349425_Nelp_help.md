---
title: "Nelp help"
date: 2009-12-08
forum: Installation &amp; Upgrades
---

### Post by venom90 on 2009-12-08
Heyy ppl.. i got a problem..
during installation i divided my 13.6 gb drive..
10 gb for home..
1 gb for swap..
2.6 gb for root.. as instructed by an ubuntu user

and now after one week it says "low disk space".. the root drive is out of memory 
is there any potential solutions for this problem? thanks.

---

### Post by starcraft.man on 2009-12-08
> **venom90 said:**
> Heyy ppl.. i got a problem..
during installation i divided my 13.6 gb drive..
10 gb for home..
1 gb for swap..
2.6 gb for root.. as instructed by an ubuntu user

and now after one week it says "low disk space".. the root drive is out of memory 
is there any potential solutions for this problem? thanks.

Yes, you need to resize the root partition to be larger, thats the longterm solution. In the short term following commands should clear some space:

```
sudo apt-get autoremove

sudo apt-get autoclean
```

As for the partitions, you need to make / at least 5-6 GB IMO. Sounds like ya been installing lots of packages. You need to use gparted, from a liveCD environment. Resize home to have less space and then move such space to / (I'd make at least 6GB for root). Gparted has excellent documentation here (see old documentation section). The package can be found in System > Admin > gparted on a live CD, it's not installed by default to a computer.

A few notes, ensure you backup any life or death data. You might want to upgrade to a larger disk, I know it costs, but 13GB total really isn't much at all nowadays, that's either a really dated disk or you've allocated far too little to linux. Gparted needs to be run from a live session to ensure that no partitions are mounted since they will be edited, this includes swap. On the main screen, gparted might automount swap. Right click on the swap partition and then click swapoff.

I think that's enough info, hope it works for ya.

---

### Post by DJonsson2008 on 2009-12-08
some notes.

* empty trash 
* and don't forget to empty root trash,
  you will need to logon on as root to 
  empty root trash

* backup your HD and 
* use the latest version of 
  bootable gparted CD for resizing,

---

### Post by starcraft.man on 2009-12-08
> **DJonsson2008 said:**
> some notes.

* empty trash 
* and don't forget to empty root trash,
  you will need to logon on as root to 
  empty root trash

* backup your HD and 
* use the latest version of 
  bootable gparted CD for resizing,

Good notes, strictly speaking you don't need to download a separate gparted CD for resizing. Like I said, it's installed to any recent liveCD and in the repos if not.

---

