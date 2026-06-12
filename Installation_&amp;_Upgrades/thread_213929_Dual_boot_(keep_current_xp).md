---
title: "Dual boot (keep current xp)"
date: 2006-07-12
forum: Installation &amp; Upgrades
---

### Post by Sequel on 2006-07-12
I have seen tons of threads of dual booting and I have yet to see a straight answer that doesn't give some half-assed shortcut to "rig" the installation. </rant>

I have a Toshiba Satellite Notebook with Windows XP. 
80gb (256mb scrap partition)

I want to install Ubuntu 4.10 on a seperate partition (naturally) while KEEPING my current Windows XP install (main partition).

I load up the CD and I can get to the "manually configure partition" screen. Where do I go from there. 

My goal: 60gb Windows (256mb scrap partition)
         15gb Ubuntu 4.10 (5gb ext for Ubuntu)

Is this possible with the 4.10 partitioner? I have tried to "resize" the current main partition to 60gb, but it totally ignores me and nothing happens. I have tried QT-Parted from my knoppix live disc but when I try to resize my partition I get an error popup that is blank. (no words, just an empty box with the question mark bubble icon). 

Any straight-forward help with this would be appreciated.

---

### Post by radiazo on 2006-07-12
the easy way is use the gparted version included in brezzy or in dapper live cds. It is in the system/administration menu named gnome partition editor or gnome partition manager (i don't remember exactly). if you have problems with   the repartition, is better if you post your actual partition table (number or partitions, size, type, primary or extended, etc.) for more help.

---

### Post by bikeboy on 2006-07-12
1) Get the latest version if you can.

2) Here are some good links, some with illustrated guides.
[http://users.bigpond.net.au/hermanzone/](http://users.bigpond.net.au/hermanzone/)
[http://psychocats.net/ubuntu/partitioning.html](http://psychocats.net/ubuntu/partitioning.html)
[http://psychocats.net/ubuntu/installing.html](http://psychocats.net/ubuntu/installing.html)

---

### Post by Sequel on 2006-07-12
Alright, remember how I said that I get an error when using QTParted on Knoppix live? Well that was when I had the notebook plugged in... Today in class I tried QTParted (I didn't actually partition yet) and there was no error. I was using battery power too.

Now I know that you can not partition an active drive (atleast not the one containing the OS right?) Why is it that I can run QTParted from a live CD only while running battery power?

---

### Post by bikeboy on 2006-07-12
When you say active you mean mounted right? Because when you run a LiveCD it doesn't actually mount the drives unless you specifically make it. Therefore you can partition using a LiveCD, battery power doesn't come into it. Although you wouldn't want to run out of power in the middle of a re-partition.

---

