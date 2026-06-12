---
title: "upgrading to new LTS version Benefit vs Risk?"
date: 2016-09-17
forum: Installation &amp; Upgrades
---

### Post by Jorhel on 2016-09-17
Hi,
I installed Xubuntu Trusty Tarh 14.04 LTS in February and I'm still working my way through a few wrinkle to iron and a steep(ish) learning curve, problem being I don't have as much time as I would wish to learn about code and need a functional computer.
Now the software upgrade offer me to upgrade to 16.04LTS which I have so far delayed. 
14.04 will be supported until 2019 I think so no hurry right?

Cheers

---

### Post by QIII on 2016-09-17
Hi!

If'n it ain't broke ...

Take your time and don't sweat.  However, mind the end of support dates on the Hardware Enablement Stack updates if you are applying them.

What are hardware specs of your machine and what "point release" of 14.04 are you running?

(Both my home server and web server run 14.04 and I'm in no hurry to upgrade!)

---

### Post by Bucky Ball on 2016-09-17
As above. No rush. Post the output of this, please, from a terminal:

```
lsb_release -a
```

---

### Post by DuckHook on 2016-09-18
It's interesting how the staff tend to agree on the same advice so often. :lolflag:

I second (or third?) all of the above with only one additional suggestion…

I never "upgrade". Instead, on my main production box, I always dual boot: with the old LTS on one partition and the new LTS on the second. When another LTS comes out, I will replace my oldest LTS with it. In real-world terms, this means that, until April of this year, I could boot either 12.04 and 14.04. But when 16.04 came out, I replaced 12.04 with it. Now, I can boot 14.04 or 16.04, leaving 12.04 to history. When 18.04 comes out, I will replace 14.04 with it, and so on.

The benefits are so obvious that I won't insult your intelligence by going into them. The next time that nag screen comes up, I suggest that you permanently tell it to stop nattering at you and that you will go to 16.04 on your own terms and at your own good time. If and when you do, instead of upgrading your current installation, you may wish to implement a rotating redundant scheme like the one I've outlined.

---

### Post by Jorhel on 2016-09-18
```
lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty


```

That sound like a good idea!
 And would leave me the time to work out how to partition my disk, when I switched from Windows XP to the current set up I put it in the too hard basket since it seemed that XP was taking all the space I just wiped up the disk and installed xubuntu. In hindsight would have been wise to keep XP in dual boot for a bit longer, but hey! live and learn...

Thanks
It's a desktop HP compaq presario about 14 years old I just realised that thought it was under 10.
If you give me the line of code to get the proper spec, I have done it once but can't find it again, I'll post them.
for the release:
> lsb_release -a
No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 14.04.5 LTS
Release:    14.04
Codename:    trusty


---

### Post by _duncan_ on 2016-09-18
There is always a risk of something going wrong with an upgrade, no matter how cautious the ubuntu devs and the user are with the upgrade.

I have a separate home partition and a spare root partition. This allows me to install the newer LTS (16.04) version to the spare partition without losing my previous LTS version (14.04). It also allows me to continue using the older version while I took my time customizing the newer version to my liking. Even after switching to the newer version, I still keep the old version around as a contingency.

edit: oops, I only read the first 2 responses and didn't see duckhook's reply. sorry about the redundant response.

---

### Post by Impavidus on 2016-09-18
Ubuntu 14.04 will be supported until April 2019, but Xubuntu 14.04 only until April 2017. So you have 7 months of support left. Xubuntu (and Lubuntu) LTS releases are supported for 3 years.

I don't really have a fixed system of upgrading, but usually I have one partition with the latest release of Xubuntu (LTS or interim) and one with the LTS release before that. When 14.10 was released I used that to overwrite 12.04, keeping 14.04. Then I upgraded 14.10 in steps to 16.04, so now I have 14.04 and 16.04. A month from now I may overwrite 14.04 with 16.10.

The main benefit of moving to 16.04 is getting more recent versions of many programs. The risk is getting more bugs and hardware incompatibilities. If you have AMD graphics and rely on proprietary drivers, you may have to wait a few more months.

---

