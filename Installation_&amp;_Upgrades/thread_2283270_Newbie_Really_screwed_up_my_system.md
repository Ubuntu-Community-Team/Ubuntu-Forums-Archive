---
title: "Newbie: Really screwed up my system"
date: 2015-06-20
forum: Installation &amp; Upgrades
---

### Post by KLSDR on 2015-06-20
So I started with Ubuntu 14.02 everything running awesome.... Continued to learn Ubuntu.. Was asked eventually to upgrade to 14.10, not everything upgraded completely because of wine something or other.. still learning Ubuntu, still updating every day.. then asked to upgrade to 15.04 so I did and now my system is completely broke. I can only run it from a disc I made when I first checked out Ubuntu.. I know this is a very elementary description, I really need some help and am not sure what info I need to give to get the help I need... Looking for someone with an extreme amount of patience! 

Thank you in advance

---

### Post by Bashing-om on 2015-06-20
KLSDR; Hello ;

Well, I guess my reputation fits:
> 
... Looking for someone with an extreme amount of patience! 

So long as you are trying I will not give up.

So; we have a failed upgrade all the way from 14.04 and presently sitting on 15.04.

The greatest point of failure in the upgrade process is 3rd party software (Wine ! for instance) installed . Just because one can tack on software, does not make it a part of ubuntu. ( proprietary graphics drivers are also a part of that group of non-ubuntu coding).

But, The goal here is to fix the system that now has 15.04 .
Let's begin by examining what the sources for installed software are. And disable all that do not apply:
Post back the outputs - Between code tags - of terminal commands:
```

cat -n /etc/apt/sources.list
tail -v -n +1 /etc/apt/sources.list.d/*

```

We get the sources settled down, then we look at making the package manager happy -> then and only then can we can clean up the system.

[INDENT][INDENT]maybe easy
[INDENT][INDENT][INDENT]maybe not so easy
[INDENT][INDENT][INDENT]in the process to find out
[/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT][/INDENT]

---

### Post by KLSDR on 2015-06-21
Oh yay... But I really do hope you have a lot of patience... so, since I can only run my laptop from a disc... grrrrrr.. (I know so many people will be rolling their eyes over this next sentence) um... where do I find the outputs?

Ok.. so extreme newbie I guess...

---

### Post by Bucky Ball on 2015-06-21
Personally, I'd backup valuable data and reinstall 14.04 LTS. For future reference, just because you are offered a distro upgrade, you're not forced to take it. 14.04 LTS is an Long-Term Support release and is supported for five years until 2019. 14.10 is supported for about another month and a bit. 15.04 supported until next Jan/Feb. Interim releases have nine months support, LTS = five years.

In Software and Updates, you can set the updater to ONLY tell you if there is an LTS release available, NOT and interim release. Perhaps go there and set that.

As mentioned, if you are going to do a net upgrade, switch off any PPAs you have added manually and disable anything not installed from the official repositories. They are pretty much the sole cause of net upgrade breakage.

---

### Post by Bashing-om on 2015-06-21
KLSDR; Hey ;

Concur totally with Bucky Ball's advise IF you want a quick clean solution to this situation. A clean install will be much much faster than fixing a broken install.

However, If you are in for the challenge and want to learn, well .. We can try and fix this install . Be aware that 15.04 uses systemd as the initiate (booting) process rather then the former upstart. I have little familiarity with systemd to this time . and it may well be a learning situation for the both of us !

Whatcha gonna do  ?

[INDENT][INDENT]it is your system, your time and your effort
[/INDENT][/INDENT]

---

### Post by Bucky Ball on 2015-06-21
> **Bashing-om said:**
> 
Concur totally with Bucky Ball's advise IF you want a quick clean solution to this situation. A clean install will be much much faster than fixing a broken install.

However, If you are in for the challenge and want to learn, well .. We can try and fix this install .

+1. ;)

---

### Post by Ty_Scheun on 2015-06-23
What do you mean by "only booting from a disc"? I would just baackup data and reinstall ubuntu

---

