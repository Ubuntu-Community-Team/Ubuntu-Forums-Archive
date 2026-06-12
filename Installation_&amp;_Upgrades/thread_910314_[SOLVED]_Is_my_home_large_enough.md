---
title: "[SOLVED] Is my /home large enough?"
date: 2008-09-04
forum: Installation &amp; Upgrades
---

### Post by anxiousdog on 2008-09-04
I keep getting errors regarding the size of my /home directory. I was wondering if someone would take a look at my gparted screenshot (attached) and see if I set things up incorrectly.

---

### Post by snowpine on 2008-09-04
Your / doesn't need to be so big--5gb should be enough unless you plan to install lots and lots of applications. Shrink your / and grow your /home.

---

### Post by anxiousdog on 2008-09-04
What's the easiest way to do that? When I'm in gparted, I can't resize/move anything. The options are greyed out.

---

### Post by ElSlunko on 2008-09-04
You can't make changes while you're booted from your HD since your HD is in use. You'll have to boot from the Live CD and use the partition editor there.

---

### Post by niyonk on 2008-09-04
Looks like an easier way would be reinstalling. :)

In the installation create 5BG(/), 1GB(swap), the remaining will be your (/home) which i believe will then be 14GB

---

### Post by snowpine on 2008-09-04
> **anxiousdog said:**
> What's the easiest way to do that? When I'm in gparted, I can't resize/move anything. The options are greyed out.

You need to boot from the Live CD and then run GParted. Can't resize partitions while they are in use. :)

---

### Post by snowpine on 2008-09-04
> **niyonk said:**
> Looks like an easier way would be reinstalling. :)

In the installation create 5BG(/), 1GB(swap), the remaining will be your (/home) which i believe will then be 14GB

No offense :) but why on earth would it be easier to reinstall than to resize the partition?

---

### Post by niyonk on 2008-09-04
I do not really trust resizing knowing i already got stuff in the partition.

---

### Post by anxiousdog on 2008-09-04
> **ElSlunko said:**
> You can't make changes while you're booted from your HD since your HD is in use. You'll have to boot from the Live CD and use the partition editor there.

This looks like the easiest option. Hopefully I can do so with no data loss. :)

---

### Post by snowpine on 2008-09-04
> **anxiousdog said:**
> This looks like the easiest option. Hopefully I can do so with no data loss. :)

Always a good idea to back up your important files first!
But resizing partitions using GParted is very safe. I don't want to say it is 100% foolproof because then if something goes wrong, you'll blame me :) but it is a good piece of software and what you're doing is pretty typical, imo.

---

### Post by anxiousdog on 2008-09-04
> **snowpine said:**
> Always a good idea to back up your important files first!
But resizing partitions using GParted is very safe. I don't want to say it is 100% foolproof because then if something goes wrong, you'll blame me :) but it is a good piece of software and what you're doing is pretty typical, imo.

I've had good luck with it so far, but I'm curious what I can use to back up my system. Mainly I'd like to save all the data and reinstall XP through virtual box instead of the dual boot that I have now. I just don't have enough space on my HD to back up!

---

### Post by zvacet on 2008-09-04
You can shrink your Windows partition (defragmat it few times before do that) and you will have space to back up.

---

### Post by lswb on 2008-09-04
Having a separate /home partition is overrated IMHO. On a system with only a single linux distribution, I see no advantage to it at all, compared to having home as a subdirectory of root on the same partition.

---

### Post by Sef on 2008-09-04
> Your / doesn't need to be so big--5gb should be enough unless you plan to install lots and lots of applications. Shrink your / and grow your /home.

Root (/) should be 8 - 10 GB.

> Having a separate /home partition is overrated IMHO. On a system with only a single linux distribution, I see no advantage to it at all, compared to having home as a subdirectory of root on the same partition.

It is good to have it separate in case there is a problem with root, or you desire to do a clean install.

---

### Post by anxiousdog on 2008-09-05
Interesting bits all around. I have completely switched from Windows into Hardy, but mostly because after the install I can no longer boot to XP at all. I'm fine with that so far, but I'd still like to back up my data and try to clean things up a bit.

---

### Post by Elfy on 2008-09-05
You have windows installed but can't access it through gruband want to?

Or you can and don't want to and just need to get data of the partition before you get rid of it?

---

### Post by anxiousdog on 2008-09-05
> **forestpixie said:**
> You have windows installed but can't access it through gruband want to?

Or you can and don't want to and just need to get data of the partition before you get rid of it?

Right now I think I want to see if I can use Virtualbox to do everything that I need XP for. If so, I will not need the windows partition at all and I will just move the data over and blow it away.

---

