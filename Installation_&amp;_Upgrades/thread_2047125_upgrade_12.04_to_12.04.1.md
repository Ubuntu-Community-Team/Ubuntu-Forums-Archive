---
title: "upgrade 12.04 to 12.04.1"
date: 2012-08-24
forum: Installation &amp; Upgrades
---

### Post by geovino on 2012-08-24
If you are running 12.04, do you automatically upgrade to 12.04.1 by running the regular updates?

Or do you run apt-get upgrade or dist-upgrade?

---

### Post by darkod on 2012-08-24
The regular updates are apt-get upgrade. Yes, that should do it.

You don't run dist-upgrade since you are already on 12.04. The point releases don't count as version upgrade as far as I know.

---

### Post by geovino on 2012-08-24
That's what I thought, Thanks.

[solved]

---

### Post by jianglai on 2012-08-24
I am on 12.04 and ran apt-get upgrade, but my system version still is 12.04. Did I miss something?

---

### Post by Sp3ctre18 on 2012-08-24
I'm on 12.04 and I'm in no rush to get the upgrade but I see the full image and i see people like geovino here talking about getting it....why dont I see it? I'm seeing extremely few results of help as I search around.

I don't see anything update manager (settings are on LTS releases). If I do apt-get upgrade I get 0 everything. What's going on&#65311;

---

### Post by rlshosting on 2012-08-24
I don't see anything either.

---

### Post by PaulW2U on 2012-08-24
Type **lsb_release -a** in a terminal window.

You probably already have 12.04.1 if you've applied all the updates that have been offered to you so far.

---

### Post by rlshosting on 2012-08-24
Ok. Great. It says I am on 12.04.1

No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu 12.04.1 LTS
Release:    12.04
Codename:    precise

---

### Post by PaulW2U on 2012-08-24
> **rlshosting said:**
> Ok. Great. It says I am on 12.04.1

Super, no need to worry about upgrading. :)

The same will happen when 12.04.2, 12.04.3 and 12.04.4 are released.

Just carry on applying the updates and your version information will automatically reflect the latest minor release.

---

### Post by Slim Odds on 2012-08-24
It does take some time for the updates to get propagated to all of the servers, so not everyone will always see the update at the exact same time.

Be patience, it's on its way.

---

### Post by Sp3ctre18 on 2012-08-24
Ah, thanks! I also see 12.04.1 in "description." :lolflag:

Is it normal that it doesn't show in system details? There it only says 12.04 LTS.

Thanks. :)

---

### Post by rchar66 on 2012-08-24
> **Sp3ctre18 said:**
> Ah, thanks! I also see 12.04.1 in "description." :lolflag:

Is it normal that it doesn't show in system details? There it only says 12.04 LTS.

Thanks. :)

Must be, I have the same thing as you.

That was an easy update. I'm sticking with the "LTS" updates from now on. Upgrading the distro every six months is getting a little crazy.

---

### Post by Sp3ctre18 on 2012-08-25
ah, alright. Thanks.

Yeah, now that I'm using Ubuntu more regularly, I'm also going to stay on LTS; besides, I don't expect I'll be having much time for constant upgrades.

---

### Post by Slim Odds on 2012-08-27
> **rchar66 said:**
> Must be, I have the same thing as you.

That was an easy update. I'm sticking with the "LTS" updates from now on. Upgrading the distro every six months is getting a little crazy.
You don't have to upgrade every six months. Even the non-LTS releases are supported for 18 months.

But I do think that the LTS is good for most folks.

---

