---
title: "Where can I get Intrepid Ibex?"
date: 2008-04-24
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Archmage on 2008-04-24
Does someone have a link for the Intrepid Ibex-CDs? They should be released in October 2008. Is there already a version to download?

---

### Post by Humph on 2008-04-24
:lolflag:

---

### Post by Antman on 2008-04-24
> **Archmage said:**
> Does someone have a link for the Intrepid Ibex-CDs? They should be released in October 2008. Is there already a version to download?
I'm running it now. It's pretty fast, voice activated and supports time travel.:popcorn:

---

### Post by billgoldberg on 2008-04-24
> **Archmage said:**
> Does someone have a link for the Intrepid Ibex-CDs? They should be released in October 2008. Is there already a version to download?

The new ubuntu release came out today.

It will be months before you can download a beta for Ibex.

---

### Post by Dennis on 2008-04-24
> **Antman said:**
> I'm running it now. It's pretty fast, voice activated and **supports time travel**.:popcorn:

Is that time travel V1.0 or the much better V2.1 :lolflag:

---

### Post by justin whitaker on 2008-04-24
> **Dennis said:**
> Is that time travel V1.0 or the much better V2.1 :lolflag:

Actually, V. 5.0. They went into the future, and backported it. :)

---

### Post by old_dog on 2008-04-24
I'm frightened to contemplate what is in Jumping Jackass or whatever!

---

### Post by fluteflute on 2008-04-24
> **billgoldberg said:**
> The new ubuntu release came out today.

It will be months before you can download a beta for Ibex.
Actually the first alpha CD will be released in about a months time. However daily images will be available in the next week or so. And the repositories will probably open in the next few days. 

The likelyhood is there will be no major changes for a little while though.

---

### Post by Twintop on 2008-04-24
> **fluteflute said:**
> Actually the first alpha CD will be released in about a months time. However daily images will be available in the next week or so. And the repositories will probably open in the next few days. 

The likelyhood is there will be no major changes for a little while though.

Mmmm. I can almost taste the breakage already!

---

### Post by justin whitaker on 2008-04-24
> **Twintop said:**
> Mmmm. I can almost taste the breakage already!

That's what is fun. 



Supposedly. 


:)

---

### Post by waspbr on 2008-04-24
regardless of breakage in the horizon, I hope that Intrepid supports my broadcom 4328, I can make it work with ndiswrapper but it is not really ideal it messes up some other usb devices. 

Hardy was pretty stable during alpha, and It was my first time following a distro development from alpha to stable, each update was little exciting (geeky giggle). so yeah, I am looking foward to the next time.

---

### Post by shuttleworthwannabe on 2008-04-24
If you want Ibex now, I guess they will be roaming the mountains of Israel.. LOL

---

### Post by Twintop on 2008-04-26
> **waspbr said:**
> Hardy was pretty stable during alpha, and It was my first time following a distro development from alpha to stable, each update was little exciting (geeky giggle). so yeah, I am looking foward to the next time.

I'm hoping that Ibex is stable during alphas as well, but I'm not counting on it. Gutsy as breaking weekly for me, and Hardy was a LTS release. I have a feeling Ibex is going to break a lot because they aren't specifically targeting super-stability their #1 goal.

...breakage is fun though, at least on a system when you can afford some downtime. :-D It's the best way to learn.

---

### Post by Archmage on 2008-07-07
Great. The Alpha 1 is there.

---

### Post by sayakb on 2008-07-07
Yepp..
[http://cdimage.ubuntu.com/releases/intrepid/alpha-1/](http://cdimage.ubuntu.com/releases/intrepid/alpha-1/)

Btw, don't use this as your primary OS. It may/may not break down several times, may even need a clean install. Install it on a separate partition.

---

### Post by hyper_ch on 2008-07-07
someone said last week ibex is pretty much unstable yet and a lot of things aren't working (yet)

---

### Post by ET! on 2008-07-07
it would have been better if they named it Imperial ibex rather than the intrepid....
btw its advisable to wait for the stable beta release

---

### Post by bobbocanfly on 2008-07-07
If you have a spare machine/partition and dont mind it when one of your OS's comes crashing down around you (X failing on you is less fun than it sounds) then please do try Intrepid. We need as many testers as we can get to make sure Intrepid is awesome.

Intrepid alpha one images are at [http://cdimage.ubuntu.com/releases/intrepid/alpha-1/](http://cdimage.ubuntu.com/releases/intrepid/alpha-1/) and current dailies (may not work and may be > 700mb) can be found here [http://cdimage.ubuntu.com/daily/current/](http://cdimage.ubuntu.com/daily/current/) (Also, this is alternate install only).

---

### Post by wilbur.harvey on 2008-07-07
I have a clean install of Hardy, and tried an "update-manager -d" to upgrade to v8.10.

It says "New distribution release '8.10' is available.

It downloads the upgrade tool, goes through the step of Setting new software channels, says that support for libnet1 has ended, then runs "Calculating the changes" and comes back with an error of

"Could not calculate the upgrade"

---

### Post by Twintop on 2008-07-07
> **wilbur.harvey said:**
> I have a clean install of Hardy, and tried an "update-manager -d" to upgrade to v8.10.

It says "New distribution release '8.10' is available.

It downloads the upgrade tool, goes through the step of Setting new software channels, says that support for libnet1 has ended, then runs "Calculating the changes" and comes back with an error of

"Could not calculate the upgrade"

What you want to do is set a clean install of 8.04, then edit your /etc/apt/sources.list file and replace any references to "hardy" with "intrepid". Then run

```
apt-get update
```and
```
apt-get upgrade
```Do NOT run apt-get dist-upgrade, as it has a tendency to push updates down that might not have all of their dependencies filled yet (and will cause major breakage most of the time).

---

### Post by monsterikan on 2008-07-07
if i upgrade my hardy heron to intrepid ibex (alpha), can i roll back the version to hardy? because i really need intrepid ibex for a glance review.

btw, what is the difference between alternate and server?
so this alpha version has no desktop installation?

---

### Post by Archmage on 2008-07-08
> **monsterikan said:**
> if i upgrade my hardy heron to intrepid ibex (alpha), can i roll back the version to hardy? because i really need intrepid ibex for a glance review.

Nope. You can't therefore you shouldn't do this on your productive system. As alread stress out you should only do this for testing with a seperate system.

So if you have no additional partition I wouldn't touch it till Ocotober.

---

### Post by Twintop on 2008-07-08
> **Archmage said:**
> 
[quote=monsterikan;5341396]if i upgrade my hardy heron to intrepid ibex (alpha), can i roll back the version to hardy? because i really need intrepid ibex for a glance review.
Nope. You can't therefore you shouldn't do this on your productive system. As alread stress out you should only do this for testing with a seperate system.

So if you have no additional partition I wouldn't touch it till Ocotober.[/quote]

This isn't entirely true. I've hosed alpha versions of Ubuntu before and recovered (mostly) unscathed by editing /etc/apt/sources.list so that it points to the previous version's repos instead of the current, then update/upgrade/dist-upgrading in apt-get.

This being said, I'd suggest running it in a virtual machine.

> **monsterikan said:**
> btw, what is the difference between alternate and server?
so this alpha version has no desktop installation?

Alternate CDs are, generally, used on systems that have funky/really old hardware and do not offer any sort of a live-cd environment. It will still install the desktop version just fine, though.

The Server CD installs a bare-bones system that you can add pieces to after installation, and is meant as a 'base' for any servers you want to setup (so that you don't get unneeded apps/services installed).


If you can, hold off ~2 days for Alpha 2 to be released. It will have a 'normal' Live-CD that you can boot from.

---

### Post by hyper_ch on 2008-07-09
> **Twintop said:**
> Alternate CDs are, generally, used on systems that have funky/really old hardware and do not offer any sort of a live-cd environment. It will still install the desktop version just fine, though.
and for encryption

---

