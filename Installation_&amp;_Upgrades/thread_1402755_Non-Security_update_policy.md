---
title: "Non-Security update policy"
date: 2010-02-09
forum: Installation &amp; Upgrades
---

### Post by jethro1138 on 2010-02-09
Hi all,

This is something I'd thought I'd be able to find a simple answer to, but I haven't been able to, so...

One of the main reasons I switched over from debian to Ubuntu was that Ubuntu was supposedly much faster to get updated versions of programs. For example, at the time Firefox 3.0 was out an debian had been stuck on 2.x for ages with no signs of ever catching up. 

Now I find Ubuntu does more or less the same thing. Firefox 3.6 has been out for a decent amount of time, but I haven't seen an update from 3.5.7 yet. Even worse, MythTV has been on 0.22-rc1 ever since I installed Ubuntu 9.10. 0.22 had been released shortly after, but no updates yet. I realise an rc-to-official isn't a big deal, but still.

Is there any central place where Ubuntu developers list projects and plans on getting updated versions? I know I can compile and install programs, and I will if no updates are forthcoming, but I'd rather not do that if there WILL be an update in the near future.

---

### Post by julianb on 2010-02-09
> **jethro1138 said:**
> Is there any central place where Ubuntu developers list projects and plans on getting updated versions? I know I can compile and install programs, and I will if no updates are forthcoming, but I'd rather not do that if there WILL be an update in the near future.

I take it you don't want to switch to Debian Unstable (Sid) in order to get cutting-edge software...

Some software developers put out .deb versions of their programs so you don't have to install. 

I also don't really recommend jumping to newest software versions when there ISN'T a new feature that you want (except security updates which are easy and which you probably already do).

---

### Post by jethro1138 on 2010-02-09
That's the sad thing, I /was/ on debian unstable! 

I'm also trying to keep my system tidy for once... not the mishmash of distribution-provided software and stuff I hacked together and .deb/tar.gz from developers/random people... so I'd like to stick with as much actual Ubuntu stuff as I can. 

Firefox and MythTV might not have been the best examples (Firefox 3.6 is still pretty new, and mythtv probably didn't gain features). But there are other programs. ufraw, for instance, has a new version with new features I'd like to have, and if I build it myself it won't play nice with F-Spot (at least that has been my experience in the past!) 

What I'm saying is I'd just like to know if something's being worked on. Yes, I can add a ppa for the latest-and-greatest Firefox, and if there'll be no official Ubuntu package for 3.6 till whatever the next version of Ubuntu comes out, then I will. But it'd be nice if there was some place I could check! (:


> **julianb said:**
> I take it you don't want to switch to Debian Unstable (Sid) in order to get cutting-edge software...

Some software developers put out .deb versions of their programs so you don't have to install. 

I also don't really recommend jumping to newest software versions when there ISN'T a new feature that you want (except security updates which are easy and which you probably already do).

---

### Post by snowpine on 2010-02-09
You misunderstand how updates work in Ubuntu. :) 9.10 = October 2009. If a new version of an application comes out in November 2009 (or later), it will never be included in the official 9.10 repositories. Ubuntu is not what's called "rolling release" (like Debian Sid); each release is "stable" once it's released.

The exception would be necessary security updates. So for example if Mozilla stops supporting FF 3.5 and it's not safe to surf the web with it any more, then you might see 3.6.

---

### Post by jethro1138 on 2010-02-09
THANK YOU. That's the answer I was looking for, albeit not the one I really wanted! (:

> **snowpine said:**
> You misunderstand how updates work in Ubuntu. :) 9.10 = October 2009. If a new version of an application comes out in November 2009 (or later), it will never be included in the official 9.10 repositories. Ubuntu is not what's called "rolling release" (like Debian Sid); each release is "stable" once it's released.

The exception would be necessary security updates. So for example if Mozilla stops supporting FF 3.5 and it's not safe to surf the web with it any more, then you might see 3.6.

---

### Post by snowpine on 2010-02-09
You're welcome. And of course, nothing stops you from using FF3.6 if you want to install it yourself. :)

---

### Post by jethro1138 on 2010-02-09
and I did, right after I saw your reply. Like I mentioned above, though, my goal here was to minimize system messiness where there's distriution-provided stuff, and then stuff I compiled myself, and then PPA repositories, and the TGZ distributions, etc, etc... 

> **snowpine said:**
> You're welcome. And of course, nothing stops you from using FF3.6 if you want to install it yourself. :)

---

