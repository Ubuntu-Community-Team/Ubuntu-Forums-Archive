---
title: "Kubuntu-Win7 Dual Boot - change to Ubuntu"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by mahaganapati on 2011-03-20
I am currently running a dual-boot setup with Kubuntu 10.10 and Win7 and I have set up /, /boot, and /home on 3 separate partitions. I am thinking of switching from Kubuntu to Ubuntu, and I wonder if this can be done without messing up the dual boot setup (and my home partition).

Do I just load a Live cd and run a plain install on my /-partition or do I need to do more than that?

Thanks.

---

### Post by Hedgehog1 on 2011-03-20
At this point in the install, select:

[IMG]http://img705.imageshack.us/img705/2588/hp4partitions09.png[/IMG]

And then ONLY format the '/' and '/boot' partitions (this image below only had the '/', but you get the idea:

[IMG]http://img857.imageshack.us/img857/6342/hp4partitions13.png[/IMG]

On the '/home'; but sure **TO NOT FORMAT** that partition, and you are good to go.

***The Hedge***

:KS

---

### Post by oldos2er on 2011-03-20
Why not just install ubuntu-desktop?

---

### Post by mahaganapati on 2011-03-20
Would that be essentially the same as doing a full install? What would I miss? What would be the advantages of doing this? (I mainly want to switch because of the look & feel of Ubuntu, so if all it takes is a simple apt-get operation I'd be very happy).

---

### Post by oldos2er on 2011-03-20
Apart from the desktop environments, (K)Ubuntu are essentially the same. As to whether installing ubuntu-desktop is the same as a full clean install, I think it's close.

If you decide you want pure Gnome, see [http://psychocats.net/ubuntu/puregnome](http://psychocats.net/ubuntu/puregnome)

---

### Post by mahaganapati on 2011-03-21
Sweet. Thanks oldos2er! I had a feeling that something like this would be possible - I think all the info I need is at the psychocats site.

---

