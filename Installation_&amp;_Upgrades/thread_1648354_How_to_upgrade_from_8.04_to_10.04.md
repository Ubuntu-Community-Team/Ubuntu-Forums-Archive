---
title: "How to upgrade from 8.04 to 10.04?"
date: 2010-12-18
forum: Installation &amp; Upgrades
---

### Post by kline on 2010-12-18
I am lost on pulling anything new from the repositories that my (*old*), but solid 8.04 releast.  The synaptic front-end fails because apt-get fails.  So, is there any magic incantation to upgrade me from 2+ year ago?

[[** Note that ideally I would like something for my latest notebook, an ASUS 900A that has 16GB of SSD.  But first things first... .** ]]

---

### Post by gmargo on 2010-12-18
[https://help.ubuntu.com/community/LucidUpgrades](https://help.ubuntu.com/community/LucidUpgrades)

Personally I think you should reinstall fresh, and skip the LTS and go straight to 10.10. (I'm a long time 8.04 user and short time 10.04 hater, but 10.10 is tolerable.)

---

### Post by Quackers on 2010-12-18
I think that if you are likely to stay with the installation for a couple of years you should go for the Long Term Support release (10.04). However, it seems that upgrading through 4 releases tends to not go well! It may be advisable to install 10.04 as a fresh install via the cd.

---

### Post by davidmohammed on 2010-12-18
> **kline said:**
> I am lost on pulling anything new from the repositories that my (*old*), but solid 8.04 releast.  The synaptic front-end fails because apt-get fails.  So, is there any magic incantation to upgrade me from 2+ year ago?

[[** Note that ideally I would like something for my latest notebook, an ASUS 900A that has 16GB of SSD.  But first things first... .** ]]

I'm curious - you say the synaptic front end fails - why?

in a terminal type

sudo apt-get upgrade && sudo apt-get update

any errors?

you can upgrade [straight to 10.04]("https://help.ubuntu.com/community/LucidUpgrades") - you dont have to go through 4 releases.

However - I would recommend you just backup what you need and just do a fresh install.

---

### Post by Quackers on 2010-12-18
I would imagine synaptic fails because 8.04 isn't supported any more.
Even if you upgrade directly from 8.04 to 10.04 you are still upgrading across 4 versions. You may not be doing each stage separately, but it's still being done :-)

---

### Post by kline on 2010-12-18
> **davidmohammed said:**
> I'm curious - you say the synaptic front end fails - why?

in a terminal type

sudo apt-get upgrade && sudo apt-get update

any errors?

you can upgrade [straight to 10.04]("https://help.ubuntu.com/community/LucidUpgrades") - you dont have to go through 4 releases.

However - I would recommend you just backup what you need and just do a fresh install.



I have three [3] discs with various releases of Ubuntu.  Both the 10.10 and the 10.04 CD discs failed to load; there was some bizarre death during the load.  Only the 8.04 DVD loaded without error, and even then, my burner stalled/failed twice, but the install did not exit.

apt-get always gives me warning and errors .... yes, probably because 8.04 is no longer supported.

I'll try the LucidUgrades, thanks.  --(The more I can upgrade over the wire, the better!)

---

### Post by kansasnoob on 2010-12-18
> **kline said:**
> I have three [3] discs with various releases of Ubuntu.  Both the 10.10 and the 10.04 CD discs failed to load; there was some bizarre death during the load.  Only the 8.04 DVD loaded without error, and even then, my burner stalled/failed twice, but the install did not exit.

apt-get always gives me warning and errors .... yes, probably because 8.04 is no longer supported.

I'll try the LucidUgrades, thanks.  --(The more I can upgrade over the wire, the better!)

That may mean that newer versions of Ubuntu won't play well with your hardware. Or you may be looking at a hardware failure since you say this, "even then, my burner stalled/failed twice, but the install did not exit"!

We need to know exactly when the new 10.04 disc fails. What errors does it show?

---

### Post by kansasnoob on 2010-12-18
> probably because 8.04 is no longer supported.

Ubuntu 8.04 is supported until April 2011, and until April 2013 on the server edition.

LTS releases have 3 years support for Desktop and 5 years for servers, and 8.04 was LTS :D

So, let's be patient and figure out what's wrong.

---

### Post by viking lander on 2010-12-18
OK, I'm having similar issues, I tried running the automatic system upgrade and it says there is nothing new to install???  Please help!  I really would like to do this step by step to learn a little about linux/ubuntu, so I can help myself a little better in the future.  I'm running a Dell mini netbook, no CD drive so I'm a little behind the power curve already.  Any help  Please!?

---

### Post by Quackers on 2010-12-18
> **kansasnoob said:**
> Ubuntu 8.04 is supported until April 2011, and until April 2013 on the server edition.

LTS releases have 3 years support for Desktop and 5 years for servers, and 8.04 was LTS :D

So, let's be patient and figure out what's wrong.

Correct kansasnoob, my bad! Something definitely wrong then :o

---

### Post by kline on 2010-12-19
For untraceable reasons I had lost my network connection.  Restoring the original version of Linux got that back; then I was able to install 10.04 easily.  Be nice to install 10.10 over this .04.  Is it doable over the wire?

---

### Post by ottosykora on 2010-12-19
thee is no upgrading through 4 versions from 8.04 to 10.04.
This is one single and direct update since it is an update from one LTS to other LTS and this is well supported and ment to be done so.

Two weeks ago, I did the same.
Had 08.04 lts on an old dell laptop, tried 10.10 from CD, will not work on that hardware, so run the normal version update while selcting in the sources that I want only lts supported vesions. 
On such very old laptop and rather slow internet connection it took some less then 2.5 hrs alltogether.

So there is no jumping from 8.04 to 8.10 to 9.04 etc needed.

---

