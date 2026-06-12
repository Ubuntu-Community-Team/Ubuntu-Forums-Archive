---
title: "Can't install pixfrogger on 9.10 64 bit?"
date: 2010-04-11
forum: Installation &amp; Upgrades
---

### Post by ingramproductions on 2010-04-11
When I try to install pixfrogger:
```
sudo apt-get install pixfrogger
```
It does not install, and I get this returned to me:
```
The following packages have unmet dependencies:
  pixfrogger: Depends: fenix but it is not installable
E: Broken packages

```
I don't find 'fenix' in the synaptic package manager.

Any ideas on how to get this running?

---

### Post by ingramproductions on 2010-04-14
It must not be anything specific to my laptop with ubuntu 9.10 64 bit, because I just tried to install it the same way on my system at work (which has the exact same os), and I got the same results.

---

### Post by PGScooter on 2010-06-13
I have the exact same problem, except on 10.04 64-bit.

---

### Post by PGScooter on 2010-06-13
I downloaded the fenix 64 deb from here:
[http://mirror.ne.gov/ubuntu/pool/universe/f/fenix/fenix_0.92a.dfsg1-3ubuntu2_amd64.deb](http://mirror.ne.gov/ubuntu/pool/universe/f/fenix/fenix_0.92a.dfsg1-3ubuntu2_amd64.deb)
and installed it
```
sudo dpkg -i *.deb
```

the game is not very fun though :(

---

### Post by ingramproductions on 2010-12-19
Thanks PGScooter, I got it installed by downloading the fenix package from that link. It's not fun if you play by yourself, but if you play with 3 friends, it gets very fun and competitive!

---

### Post by PGScooter on 2010-12-20
> **ingramproductions said:**
> Thanks PGScooter, I got it installed by downloading the fenix package from that link. It's not fun if you play by yourself, but if you play with 3 friends, it gets very fun and competitive!

ok, I'll keep that in mind and give it another shot someday. Thanks for the tip.

---

### Post by cesera on 2011-08-03
Still the same problem in 11.04 amd64. Downloading the external library now, but why is that not in the repository?

---

### Post by PGScooter on 2011-08-04
> **cesera said:**
> Still the same problem in 11.04 amd64. Downloading the external library now, but why is that not in the repository?

I agree; it should be. If you have time, could you file a bug report? I don't have time now and I'm sure I'll forget when I do have time.

---

### Post by MAFoElffen on 2011-08-04
> **PGScooter said:**
> I agree; it should be. If you have time, could you file a bug report? I don't have time now and I'm sure I'll forget when I do have time.
I had the same problem on this game wirh 9.04 thru 11.10.  But I have 6 other boxes here that it installed yo with no problems.   

I figure that it wasn't somethng missing... but rather something that was already installed that conflicts with fenix of the the pixfrogger package.  After I got it installed for my fiance and others... (IMO) I saw it wasn't worth getting it going on mine.

Installs fine on a fresh install though, with no problems.

---

### Post by PGScooter on 2011-08-04
There is a bug posted:
[https://bugs.launchpad.net/ubuntu/+source/pixfrogger/+bug/484089](https://bugs.launchpad.net/ubuntu/+source/pixfrogger/+bug/484089)

If you have 10 seconds, go there and click "this bug also affects me". You have to have a launchpad account and sign in. It's very easy to create one if you don't already have one.

---

### Post by ingramproductions on 2011-08-17
sure

---

### Post by uRock on 2011-08-17
ubuntu 9.10 is no longer supported.

---

