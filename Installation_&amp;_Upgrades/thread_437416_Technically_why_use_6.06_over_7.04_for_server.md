---
title: "Technically why use 6.06 over 7.04 for server?"
date: 2007-05-08
forum: Installation &amp; Upgrades
---

### Post by Quixis on 2007-05-08
Hi all, newbie to the forums here.

I'm thinking of installing an email relay / proxy server for a business using Ubuntu server. Now I understand that 6.06 has a 5 year support period and 7.04 doesn't, but why?

I'm assuming 7.04 has the latest packages available in a stable form so I'm still looking for the reason to why 6.06 would be the supported choice?

Anyway if that makes sense could someone please explain what the situation is.

Thanks

---

### Post by dmizer on 2007-05-08
one major thing to consider here is upgrades.  dapper is an LTS release.  you will be able to upgrade directly from dapper to the next LTS release without having to go through all the intermediate releases.

generally servers don't need to be cutting edge ... just secure and reliable.  with LTS you get long term security and stability without having to worry about taking your email and proxy server offline every 6 months while you hunt down upgrade snafu or hardware/software compatibility disaster.

---

### Post by Quixis on 2007-05-09
> **dmizer said:**
> one major thing to consider here is upgrades.  dapper is an LTS release.  you will be able to upgrade directly from dapper to the next LTS release without having to go through all the intermediate releases.

generally servers don't need to be cutting edge ... just secure and reliable.  with LTS you get long term security and stability without having to worry about taking your email and proxy server offline every 6 months while you hunt down upgrade snafu or hardware/software compatibility disaster.

dmizer, thank you for educating me. Now it makes a heap of sense. So yes, it's better to jump from a reliable LTS release to another LTS.

Thanks again sir. :)

---

### Post by Jahf on 2007-05-10
I'm curious about something similar.

Will there be a 7.x LTS release, or will there not be another LTS release until the current LTS is close to retirement?

I'm just now building out a major project, one which I'll be developing for a few months or more, so it would be no big deal for me to put it on a 7.x non-LTS release now, and then when I finalize and move to production move it to a clean install of a 7.x LTS release.

But, if there is no solid plan for a new LTS yet, and it really won't be out until 2009, it probably makes more sense for me to build on 6.06 and then upgrade via the LTS supported migration later.

---

### Post by dmizer on 2007-05-11
it has not yet been officially announced, [but i have read](http://derstandard.at/?url=/?id=2845484) [derStandard] that feisty +2 (post gutsy) will possibly be LTS.  but again ... there has not been an official announcement as of yet.  however, given the release schedule, it is unlikely that there will be a 7.x LTS.  further, there's no real reason for there to be a 7.x LTS as covering 2 LTS releases has to be a nightmare.

either way ... it still makes sense to build on 6.06 because you'll be wise to wait on your upgrade from 6.06 until you've done trials, as well as perused the forums to have a look at what kind of problems people have run into with their server updates.  dapper will be securely supported until 2009, there''s no reason to rush things when considering server deployment.

---

