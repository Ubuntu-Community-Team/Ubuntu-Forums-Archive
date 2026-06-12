---
title: "Should I wait for 7.10 ?"
date: 2007-04-24
forum: Installation &amp; Upgrades
---

### Post by bozo on 2007-04-24
Hi people,

   I'm currently running 6.06 desktop on my home server (acting as both web/mail server and media player using my TV as display).

The system is a bit customized, though not overly so. I have a couple extra APT sources and a non-free nvidia kernel module for the display, a moderately complex mail configuration that I would hate to lose (postfix/spamassassin/clamav/cyrus), and a software raid using mdadm, root filesystem included.

I've been considering upgrading to 7.04, which means I have to upgrade to 6.10 before, but it seems this is not always painless, to say the least.

So, the question is, should I wait for 7.10 to make a single, massive upgrade (which, according to the [FAQ]("http://www.ubuntu.com/aboutus/faq"), will be supported : "*Upgrades will be supported from Enterprise Release to Enterprise Release*."), or would it be better to go through all the incremental steps of 6.10 and 7.04 before?

A secondary question is, how solid will the 6.06 -> 7.10 upgrade be? More or less robust than 6.06 -> 6.10, for instance?

Any insight would be appreciated.

--
Daniel

---

### Post by flyingbrass on 2007-04-24
Unless you need something Dapper doesn't provide or just have the urge to play with your system, stick with what is working.  Security updates will be available for Dapper for 2 more years (desktop version).  If it ain't broke...

I seriously doubt upgrading would go smoothly.  If you want to try Feisty I recommend a clean install.

---

### Post by bozo on 2007-04-24
Thanks for the quick reply.

As far as possible, I'd rather avoid reinstalling : the mail service configuration is a real PITA, and I've got baaaaad memories of the software raid setup (though, come to think of it, if I keep the filesystems, it shouldn't be that bad).

The current Dapper setup satisfies me, except for one piece of software : the mythtv version I use is bugged (well, the mythvideo bit, at least), and I'd rather stick to  maintained  packages than build my own version.

The remaining question is more intended for the developers, I guess : how well will the jump from 6.06 to 7.10 be supported?

---

### Post by superm1 on 2007-04-24
> **bozo said:**
> Thanks for the quick reply.

As far as possible, I'd rather avoid reinstalling : the mail service configuration is a real PITA, and I've got baaaaad memories of the software raid setup (though, come to think of it, if I keep the filesystems, it shouldn't be that bad).

The current Dapper setup satisfies me, except for one piece of software : the mythtv version I use is bugged (well, the mythvideo bit, at least), and I'd rather stick to  maintained  packages than build my own version.

The remaining question is more intended for the developers, I guess : how well will the jump from 6.06 to 7.10 be supported?
Bozo,
You installed the backport correct?  Mythvideo should have also been backported recently to dapper....
Can you post the output of
```
dpkg -l | grep myth
```

---

### Post by bozo on 2007-04-25
> **superm1 said:**
> Bozo,
You installed the backport correct?  Mythvideo should have also been backported recently to dapper....
Can you post the output of
```
dpkg -l | grep myth
```

No, I'm not using the backport yet, still running 0.18.1 (IIRC). I tried the backport (0.20) some time ago, but mythvideo hadn't been backported yet, and I went back to the older version.

I'll try the mythtv backport. In the meantime, I'm going to stick with dapper.

Thanks for all the input.

---

### Post by superm1 on 2007-04-25
Mythvideo should be available in the 0.20 backport for dapper.  I prodded the archive admins a few weeks ago about it.

---

### Post by bozo on 2007-04-26
> **superm1 said:**
> Mythvideo should be available in the 0.20 backport for dapper.  I prodded the archive admins a few weeks ago about it.

Yup. I had a look yesterday, and there it is - though I was too lazy to upgrade right then, I'll deal with that in a couple days :popcorn:

---

### Post by bozo on 2007-05-11
> **bozo said:**
> Yup. I had a look yesterday, and there it is - though I was too lazy to upgrade right then, I'll deal with that in a couple days :popcorn:
For the record, I installed the mythtv backport a few days ago, haven't had a single problem since!

---

