---
title: "Forced upgrade from 7.10 on sparc"
date: 2010-08-14
forum: Installation &amp; Upgrades
---

### Post by merald on 2010-08-14
Got kernel panic when upgradeing from 9.04 to 9.10...

Have a tough time with this sparc server. On newer disto it doesnt regognize the cdrom in installation what will result in no install. I tried all trix I found on internet about this issue but none of them did it for me.

So I went back in versions. When I come to 7.10 gutsy everything seems to work, so now everything is up and running.

But now I want it back on version 9.04. Last time (a year ago) I did the same thing, and just do-release-update to current version. Now that doesnt work. Maybe becourse I need some updates to gutsy, and the gutsy repositorys is not available anywere.

Any suggestions how I can pass this upgrade to 8.04? I set the
APT::Get::AllowUnauthenticated true;
to pass this far...


Logs; [http://85.195.2.106/dist-upgrade.tar.gz](http://85.195.2.106/dist-upgrade.tar.gz)

---

### Post by lemming465 on 2010-08-15
I think they dropped SPARC support at 8.10.  I'm not sure what effect that had on the 8.04 repositories, if any.

---

### Post by merald on 2010-08-16
I manage to upgrade to 8.04 after installing package tzdata. For some reason that is not installed in 7.10.

I thinking about what level I should have it. The SPARC version of 8.04 is not LTS then?

If you have an LTS version and the other versions around expire, how will you upgrade to next LTS then?  :confused:

---

### Post by mörgæs on 2010-08-16
It sounds like this machine has been through a lot of upgrades. Isn't it time to consider a clean install?

---

### Post by merald on 2010-08-16
If it was possible I wouldn't hesitate a second! See my first post in thread...

Are pretty disappointed of ubuntu sparc port. Thought it should be better be course its no such problem in Debian. Guess almost nobody run ubuntu at sparc platform? A prefix at forum thread would maybe be a start :D

---

### Post by lemming465 on 2010-08-17
I would assume if they dropped SPARC support, that no upgrade from 8.04 LTS to 10.04 LTS would be available.  You'd be stuck n 8.04, at which point dropping Ubuntu and running something else such as Debian might be appealing.

---

### Post by merald on 2010-08-17
Thanks for your response

Heh all this trade-offs, allways something whatever you choose. I been very committed to ubuntu project, and want it to develop. 

Let us start from the beginning; What is the reason there is a SPARC port of Ubuntu in the first place? Becourse Debian has it? I think it get more bad-will to offer something that then is not maintained rather than not offer it at all.

---

### Post by lemming465 on 2010-08-17
It looks like the Ubuntu SPARC port went from unofficial, to official, to unofficial, to defunct as levels of interest waxed and waned, e.g.:
[sparc official at 6.06]("https://lists.ubuntu.com/archives/ubuntu-devel-discuss/2007-February/000322.html")
[SPARC decommissioned for 10.10]("http://lwn.net/Articles/391238/")

---

### Post by merald on 2010-08-17
That link was a pretty clear answer. So a warning to those people finding this thread trying to install Ubuntu on sparc - don't ;)

---

### Post by linux18 on 2010-08-17
debian 6 is a few months away(finally!) that is pretty much the only way your going to get a quality sparc OS, just backup your installation do a fresh 7.10 install ans coast for the next few months until debian 6 SPARC

---

### Post by lemming465 on 2010-08-17
NetBSD probably has a good SPARC port too, but that won't look much like Debian or Ubuntu.

---

### Post by merald on 2010-08-18
I am on SPARC 8.04 LTS level now, as it says it has support until April 2013 accoding to [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

Is that true or could it just suddenly dissapear?

---

### Post by mörgæs on 2010-08-18
> **merald said:**
> I am on SPARC 8.04 LTS level now, as it says it has support until April 2013 accoding to [http://en.wikipedia.org/wiki/List_of_Ubuntu_releases](http://en.wikipedia.org/wiki/List_of_Ubuntu_releases)

Is that true or could it just suddenly dissapear?

You can trust that. I have never heard of changes to the support scheme.

---

