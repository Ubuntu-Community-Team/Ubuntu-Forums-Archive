---
title: "Triple booting gutsy, vista premium and win2k pro?"
date: 2008-02-28
forum: Installation &amp; Upgrades
---

### Post by DarkerStar on 2008-02-28
i am considering setting up a triple boot configuration on a 500G SATA drive, using Gutsy, Vista Premium and Win2K Pro. i just wanted to ask for advice on some things.

Just for some background as to why - i don't really have any connection to either of the Windows version, but i need them to run programs for school. One program will not run on Vista, so i need 2K. One will not run (properly) on 2K (needs XP minimum), so i need Vista. What a wonderful life i lead. Other than just running those programs, i don't really intend to use Vista or 2K for anything much - maybe some (older) games i still have, but that's it.

----------------------------

First, how to partition the drive? i am not sure which partitions have to be primary and which can be extended. i am *thinking*:
[LIST]
[*]Primary: 50GB 2K
[*]Primary: 150GB Vista
[*]Extended
[LIST]
[*]Logical: 75GB Ubuntu /
[*]Logical: *GB Ubuntu /home
[/LIST]
[*]Primary: 2GB Swap
[/LIST]

Second, is this a good plan for how to do it:
[LIST=1]
[*]Install Win 2K.
[*]Update to SP4 (and as necessary). -_-
[*]Install Vista.
[*]Update Vista (if necessary), and get it up to snuff (ie, get Aero running).
[*]Install Gutsy.
[*]Tweak GRUB options.
[/LIST]

Third, will the Win 2K large LBA thing be a problem? If i install W2K first, and on a partition <120GB, do i even need to worry at all? Or, if i just update to SP4, then enable large LBA support, is everything fine from then on out?

And finally... should i wait a couple of weeks for Hardy? Is there a point? Would there be any foreseeable problem installing Hardy over Gutsy? Shouldn't Vista and 2K be unaffected? Shouldn't the only thing i have to do in that case be fixing GRUB's problems? (Honestly, i don't think there is anything in Hardy that would make me *have* to have it, as was the case going from Feisty to Gutsy.)

---

### Post by jken146 on 2008-02-28
I think your plan is good.  I would try it in that order.

I would make / only 10 GB, 15 at most.  I really don't see why you'll need 75.

You probably won't even have to tweak the GRUB options -- usually it does a very good job of detecting what's already on there.

As for Hardy, it will be no big deal to just install Gutsy now and then wipe it and install Hardy in its place in April.  With a separate /home partition, all your settings will be kept.

Also, I'd limit the swap to 1 GB, and even that is being generous tbh.

---

### Post by mi_were on 2008-02-28
If the number of problems u need r that limited I would go the virtualisation way I have. I am running XP on vmware in ubuntu 7.10. I will (when laziness passes) be removing the dual boot I have now Ubuntu and Vista. Nothing against vista i is good for what it is but I have most of what I need in linux and the rest runs of XP in vmware for now.

cheers

---

### Post by Bucky Ball on 2008-02-28
Swap should be twice the size of your physical memory (RAM). 1Gb RAM = 2Gb swap, if you have the resources.

---

### Post by DarkerStar on 2008-03-01
> **jken146 said:**
> I would make / only 10 GB, 15 at most.  I really don't see why you'll need 75.
So little? Wow.

> **jken146 said:**
> You probably won't even have to tweak the GRUB options -- usually it does a very good job of detecting what's already on there.
My understanding is that when Vista gets installed, it will overwrite the MBR with its own boot manager that allows you to select between its boot loader and ntloader for Win2K. Then when Ubuntu is installed, GRUB detects only the Vista boot loader. The punch line is that GRUB gives you two basic options - Ubuntu and Vista - and when you select Vista, you get the Vista boot manager that lets you select between Vista and 2K.

i'd like to see if i can tweak GRUB's settings to give me three options - 2K, Vista and Ubuntu - and have each option correctly boot to each OS without any intermediate steps in Vista's boot manager. It's an experiment, but i have some ideas for things to try.

> **jken146 said:**
> Also, I'd limit the swap to 1 GB, and even that is being generous tbh.> **Bucky Ball said:**
> Swap should be twice the size of your physical memory (RAM). 1Gb RAM = 2Gb swap, if you have the resources.
Well, i have 2GB of RAM, but i figured 2GB swap is enough. It's not like i'm short on disk space - the primary drive is 500 GB, with two 300 GB, one 240 GB and one 120 GB drive - but 2 GB swap + 2 GB RAM seems like plenty, and i do have more RAM slots available.

---

### Post by Bucky Ball on 2008-03-02
This might be of interest:

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=218](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=218)

---

### Post by DarkerStar on 2008-05-08
> **Bucky Ball said:**
> This might be of interest:

[http://www.linux-tutorial.info/modules.php?name=MContent&pageid=218](http://www.linux-tutorial.info/modules.php?name=MContent&pageid=218)
Wow, that's an entirely different way of thinking about things. If i do reinstall at any future time, i might make the swap partition only 1 GiB, and, then use a swap file, if necessary (of course, the first thing i would probably do is get more RAM :wink:). Aside from the benefits that the guy in that article mentioned, when you're dual booting other operating systems having a swap partition is just a waste of space.

---

