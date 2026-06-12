---
title: "ATI Catalyst 8.8 Driver Released, still no Xorg 7.4 support"
date: 2008-08-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by bpl07 on 2008-08-20
[Phoronix Article]("http://www.phoronix.com/scan.php?page=article&item=amd_catalyst_evolution&num=1")

[Driver]("https://a248.e.akamai.net/f/674/9206/0/www2.ati.com/drivers/linux/ati-driver-installer-8-8-x86.x86_64.run")

Maybe next month we'll get something that works in Intrepid without downgrading Xorg/Xserver.

---

### Post by olskar on 2008-08-20
I certainly hope so...

---

### Post by fictivetoast on 2008-08-20
arrrrrrrrrrrrrrr, I was hoping ATI'd come through this month...

---

### Post by melat0nin on 2008-08-21
Is it okay to follow the cchtml instructions for installing 8.7 to install this driver?

And is it okay to install over 8.7 or does that have to be removed first?

---

### Post by grigio on 2008-08-21
Is this driver really better?
Because with catalyst 8.7 + 4850 I get a freeze every random(60)seconds on Linux.

---

### Post by soxs on 2008-08-22
> **grigio said:**
> Is this driver really better?
Because with catalyst 8.7 + 4850 I get a freeze every random(60)seconds on Linux.

Read the links, pusted in in post #1.

Btw. how can I downgrade xorg? I never did and I don't really know where to start or what is required to, and hwo I keep apt(itude) from beging me to upgrade?

---

### Post by grigio on 2008-08-22
> **soxs said:**
> Read the links, pusted in in post #1.

Btw. how can I downgrade xorg? I never did and I don't really know where to start or what is required to, and hwo I keep apt(itude) from beging me to upgrade?

What in particular?

To downgrade xorg you have to replace intrepid repos with hardy's repos... and then you need a lot of patience.

---

### Post by olskar on 2008-08-22
Check here for instructions on downgrading
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

---

### Post by rockin_goliath on 2008-08-22
Typical ATI

I will definitely be choosing Intel graphics from now on. This is just outrageous.

---

### Post by BwackNinja on 2008-08-22
@rockin_goliath

That's not quite fair to ATi. They're giving crossfire support now (its in the driver and works, not quite stable yet). They're giving support for new cards in linux the day they arrive. They're even helping open source drivers.

The way intel drivers are going though, just wow...I wants my dri2...

---

### Post by soxs on 2008-08-23
> **olskar said:**
> Check here for instructions on downgrading
[http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide](http://wiki.cchtml.com/index.php/Ubuntu_Intrepid_Installation_Guide)

Well, this one lacks _which_ packages to remove. I won't be able to remeber 100 pkgs i removed and I have to reinstall...

google doesn't spit out anything usefull :-S

EDIT: got it:
```
sudo apt-get remove --purge libgl-mesa-*
```
This will kill any xorg and x11 stuff by this single command...

EDIT: retired using hardy again, because of hundreds of dependencie errors :-S I will give it a shot again if 8.9 is out (so in about weeks)

---

### Post by InfinityCircuit on 2008-08-23
You should be able to just pin libgl1-mesa-* to 1001 and then aptitude full-upgrade will take care of the rest.

---

### Post by Mazza558 on 2008-08-23
I'm happy enough that window tearing has been reduced. DVDs will be watchable soon!

---

### Post by olskar on 2008-08-23
Hm, what would happen if 8.9 does not have Xorg 7.4 support? Then all Intrepid-users will have to downgrade their xorg? :confused:

---

### Post by Phristen on 2008-08-23
Wouldn't catalyst 8.10 be out by the time of intrepid release?

---

### Post by olskar on 2008-08-23
Yeah, it should be, but you get my point :)

---

