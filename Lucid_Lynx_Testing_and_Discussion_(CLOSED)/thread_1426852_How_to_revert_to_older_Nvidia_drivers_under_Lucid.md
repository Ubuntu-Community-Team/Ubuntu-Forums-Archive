---
title: "How to revert to older Nvidia drivers under Lucid?"
date: 2010-03-10
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by recluce on 2010-03-10
As we are all aware now, 195.36.08 drivers may kill your graphics card. The big question now is: how do I revert to older drivers?

Jockey offers 173 series drivers, but fails to install. Synaptic fails to install older drivers, you get a half-installed driver and lots of fun with X.org. The NVidia drivers (original from NVidia site) abort with an error. "How to" guides for older Ubuntu versions don't seem to work either.

So if anybody could point me in the right direction on how to install one of the older NVidia drivers under Lucid, I would be really thankful.

---

### Post by mc4man on 2010-03-10
Well if you don't wish to use nvidia-current then one way would be to change to nouveau as here
[http://ubuntuforums.org/showthread.php?t=1423210](http://ubuntuforums.org/showthread.php?t=1423210)

( I have 3 different nvidia cards running the 195.36.08 with absolutely no issues.
Also have one box dual booting, one w/ nouveau, one w/ 195.36.08, nouveau isn't not too bad though on a hd panel it's a loser atm

---

### Post by recluce on 2010-03-11
> **mc4man said:**
> Well if you don't wish to use nvidia-current then one way would be to change to nouveau as here
[http://ubuntuforums.org/showthread.php?t=1423210](http://ubuntuforums.org/showthread.php?t=1423210)

( I have 3 different nvidia cards running the 195.36.08 with absolutely no issues.
Also have one box dual booting, one w/ nouveau, one w/ 195.36.08, nouveau isn't not too bad though on a hd panel it's a loser atm

I am currently using 195.36.08 as well, but with an uneasy feeling. Nouveau I have used for testing, but I have performance issues with HD video and I like desktop effects... ;)

That is why I asked for ways to successfully install older NVidia (proprietary) driver versions.

---

### Post by cariboo on 2010-03-11
If you use the drivers from xorg-edgers ppa, you get desktop affects.

BTW howdy from another BC resident.

---

### Post by recluce on 2010-03-12
> **cariboo907 said:**
> If you use the drivers from xorg-edgers ppa, you get desktop affects.

BTW howdy from another BC resident.

I checked out the xorg-edgers project - and I am not sure I am that brave... :rolleyes: It starts with something like "x-org edgers is for people who think that 'unstable' versions are for old ladies....

And greetings back from Victoria. Looking at an inch of snow right now! :shock:

---

