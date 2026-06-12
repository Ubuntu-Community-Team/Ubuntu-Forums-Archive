---
title: "Necessity of Upgrading from 16.04 to 17.10?"
date: 2018-01-11
forum: Installation &amp; Upgrades
---

### Post by galacticstone on 2018-01-11
I was afraid of bricking my Lenovo, so I installed 16.04 LTS. It runs great and I am very happy with it.

Now that the bricking issue is being fixed, is it worth it to upgrade to 17.10?  Is 17.10 a LTS or no?

I am already using GNOME, so losing Unity is not a big deal to me. 

As a newbie, it took me a little while to get my current setup configured the way I like it. I am worried if I upgrade to 17.10, I will have to start tweaking everything again.

Is there someplace that has an easy to read list of the new features and fixes that are present in 17.10 over 16.04?

Thanks in advance!

MikeG

---

### Post by cruzer001 on 2018-01-11
In April you can upgrade 16.04 direct to 18.04, skipping the other versions.  This is only possible with a LTS release.

---

### Post by yancek on 2018-01-11
You're better off staying with LTS releases and 18.04 will be available soon as pointed out above.  The only logical reasons I can think of to upgrade to a non-LTS would be if the newer non-LTS has some software you want/need which is not available with your currrent system or if you are having some problem with your current system and have verifiable information indicating a newer system will resolve it.  Wait until April/May for 18.04.

---

### Post by deadflowr on 2018-01-11
> **cruzer001 said:**
> In April you can upgrade 16.04 direct to 18.04, skipping the other versions.  This is only possible with a LTS release.

Direct upgrades from LTS to LTS aren't available until the first point release sometime in mid summer usually late July or early August.
That's when the option to run a release upgrade is available for LTS users.
You can get it it earlier by invoking the development flag for update-manager (or the do-release-upgrade command), but note that development mode is for testing and can bring about unexpected results.

---

### Post by galacticstone on 2018-01-11
Thanks for the feedback folks. I will likely wait for 18.04 - that will be another LTS, correct?

I guess there is no reason for me to upgrade to 17.10 - all of this is pretty new to me anyway, so I am still far from fully exploring and understanding 16.04. I think this could keep me occupied until 18.04 comes out.

Thanks again for tolerating all of my redundant noob questions.  :)

---

### Post by cruzer001 on 2018-01-11
> **deadflowr said:**
> You can get it it earlier by invoking the development flag for update-manager (or the do-release-upgrade command), but note that development mode is for testing and can bring about unexpected results.

It is no longer a developmental release after the end of April even if your using the -d switch.  Just a way to get it without waiting for that first point release.

> So for example 14.04 will only upgrade once 16.04.1 is released. If you want to update before, e.g. on a subseDirect upgrades from LTS to LTS aren't available until the first point  release sometime in mid summer usually late July or early August.
That's when the option to run a release upgrade is available for LTS users.t of machines to evaluate the LTS upgrade for your setup the same argument as an upgrade to a dev release has to be used via the -d switch. 

[https://help.ubuntu.com/lts/serverguide/installing-upgrading.html](https://help.ubuntu.com/lts/serverguide/installing-upgrading.html)

---

### Post by deadflowr on 2018-01-12
> **cruzer001 said:**
> It is no longer a developmental release after the end of April even if your using the -d switch.  Just a way to get it without waiting for that first point release.

Is sure is still under development, 

But I mean and meant the release upgrade tool, and not the actual release.
Since so much changes between LTS and LTS releases, to ensure a smooth upgrade they need to do some additional testing of the upgrade tool.

While more recent LTS to LTS upgrade have been relatively safe, this has not always been the case, and so the extra 3 months (or so) of testing the tool can still save a lot of downtime.

---

### Post by cruzer001 on 2018-01-12
The April release will be 18.04.0 whether you use the iso or the -d switch.  One of the same.  For those who want can pretest the point releases (1,2,3,4), but that will not happen by using the -d switch when the final release comes out.

Yes, safer to wait for a production machine (server) but not necessary for the desktop user or why would they even bother to release it in April at all?  

Sorry, but I do not see a difference between the April release iso or an upgrade using the -d switch.

---

