---
title: "How to upgrade with out messing up repositories"
date: 2015-03-31
forum: Installation &amp; Upgrades
---

### Post by pnbalaji1974 on 2015-03-31
Hi,

I am not using Ubuntu right now, but planning to install on my desktop today.

I was an ubuntu user couple of years ago, but had to ditch because of repository issues. The repository names in ubuntu and Linux Mint changes almost with every new release. Today, the repo name will be having quantal, tomorrow it will change to precise and then it will change to tahr or something like that (examples). The problem is if I don't change my repository names, updates will fail.

Is there any way to avoid this? I don't want to change the repository names in /etc/apt/sources.list with every new version/release. Infact, this is one of the reason why I prefer a rolling release distribution. Install it once and then forget about the repositories once configured.

Can some one help?

Thanks,
Balaji.

---

### Post by dino99 on 2015-03-31
yes there is a way: let ubuntu do its installation without tweaking it yourself ;)

if you want to have 'rolling' sources.list, then change the 'release name' by 'devel', save/update and you will not need to change it again.

---

### Post by pnbalaji1974 on 2015-03-31
Thanks for the reply.

By replacing the 'release name' to 'devel', will it be stable? I assume so, but want to confirm.

I might be adding some PPAs on myself (from webupd8, noobslab etc), but I don't think those will cause issues, correct?

Thanks,
Balaji.

---

### Post by kerry_s on 2015-03-31
you don't have to touch sources.list at all. if you want long term you install ubuntu 14.0.4.2 lts

if you prefer rolling release, you should go for a distro like arch or debian testing.

---

### Post by Bucky Ball on 2015-03-31
It's the PPAs (repos) you install manually that *_will_* screw up an in-box upgrade to a newer release. Disable them before upgrading to a newer release. Best bet? Use an LTS release. They are now supported for five years (Ubuntu, that is: other flavours differ).

As mentioned, you shouldn't need to touch sources.list at all. Go to 'Software and Updates' (may be called something diff in your flavour) and disable or remove the OLD repos from the previous release after you've upgraded if you want.

---

### Post by pnbalaji1974 on 2015-03-31
Yep, I am planning to install Ubuntu 14.04.2 today. Been using Manjaro for couple of years, a great rolling release distro, but I am having couple of issues that cannot be solved. So, planning to ditch and re-install Ubuntu 14.04.2 or Xubuntu 14.04.2. BTW, XFCE is my preferred DE.

Thanks,
Balaji.

---

### Post by Bucky Ball on 2015-03-31
Minimal install with xfce4 here, and has been that way for years. There's another option. ;)

---

### Post by grahammechanical on 2015-03-31
> [COLOR=#000000]By replacing the 'release name' to 'devel', will it be stable? I assume so, but want to confirm.[/COLOR]

No it will not be.

What you will get is the repositories of the next development release. At the moment those are called "vivid" and if I want to convert my existing development release over to the next development version with a "w" code name I will have to change the repository names, as you state. But if I have the repositories set to "devel" my existing Vivid Vervet development release will "roll over" to the "Wcodename" development release within the first few days of the new development cycle starting.

Do you want to run the development release? I have run it for a few years and I have found it to be very stable but I do expect breakage and I do have a 14.04 install of Ubuntu that I can fall back on if the need should arise. The development release is the nearest thing we have on Ubuntu to a "rolling release" but do not expect stability on a development release and do expect megabytes of updates almost daily.

Regards.

This is what life is like on the Ubuntu development release

[http://ubuntuforums.org/forumdisplay.php?f=427](http://ubuntuforums.org/forumdisplay.php?f=427)

---

### Post by ian-weisser on 2015-03-31
> **pnbalaji1974 said:**
> The repository names in ubuntu and Linux Mint changes almost with every new release.
Yes they do.
That's deliberate - so you can tell releases apart.

> **pnbalaji1974 said:**
> I don't want to change the repository names in /etc/apt/sources.list with every new version/release.
Who would want to? Ubuntu has used an automatic release-upgrade tool for many, many years. You edit nothing.
You should, of course, uninstall all non-Ubuntu software before starting the release-upgrade. Some non-Ubuntu packages cause file or version conflicts.
Only those who have *really* haywired their systems need to edit sources.list manually.

---

