---
title: "Which to install on a mini lap top with atom processor"
date: 2016-02-14
forum: Installation &amp; Upgrades
---

### Post by john_OBrien on 2016-02-14
I have a HP Mini 110-3135DX laptop computer.  I think I have 1.5 GB memory and an Atom processor.  Which version of Lubuntu should I use?
Also does the verison you suggest need a separate wireless driver or does it come with it.  If I need a separate wireless from where do I get it?
Thanks

---

### Post by papibe on 2016-02-14
Hi john_OBrien.

I don't have a accurate assessment of how powerful that processor is. My guess is that is closest to a fast P4 (being not dual core)

If that's the case, vanilla Ubuntu would be a bit slow. I'd think any of the these options would work well:
[LIST]
[*][Lubuntu]("http://lubuntu.net/")
[*][Xubuntu]("http://xubuntu.org/")
[*][Ubuntu Mate]("https://ubuntu-mate.org/")
[/LIST]
As far as version, the safest option would be to go with an LTS version: 14.04. Another alternative is going with the latest version 15.10, but it has a shorter support time.

Just some thoughts. Hope that helps.
Regards.

---

### Post by kurt18947 on 2016-02-14
I agree with papibe's recommendations. Another distro to consider would be LXLE which is based on Lubuntu.

---

### Post by justen_m on 2016-02-19
My 2008 netbook has a 1.6GHz Intel Atom N270, 1.5GB RAM. Single physical core, but it is hyper-threaded for two logical cores. On some benchmarks I've done, it is comparable to a 1.8GHz P4 I've got. I run 32-bit 14.04.3LTS on my netbook. It is fairly slow, but usable. I have to carefully manage how many browser tabs I have open, etc, but that is more a memory constraint. You don't want to use swap space with its slow 5400rpm HDD. I too would recommend a lighter distro. I've been thinking about putting LXLE, which is based on Lubuntu, based on 14.04.3, on mine. I'be got it on a USB stick ready to go, just haven't gotten around to it yet...

In any case, I'd go with an LTS version. Definitely 32-bit. 14.04.3LTS has a wireless driver that works fine with my netbook's adapter (Qualcomm Atheros AR242x/AR542x).

---

### Post by kalehrl on 2016-02-20
I'd suggest you start with minimal Debian stable system and then install lxde-core.
You can even add --no-install-recommends to the command line for absolute minimal lxde-core.
This will give you a much lighter system than Lubuntu.

---

### Post by Topsiho on 2016-02-21
I fully agree with papibe's recommendation.
I have a similar netbook (Acer Aspire One), that now runs Ubuntu Mate. It is rather slow, though.

Topsiho

---

