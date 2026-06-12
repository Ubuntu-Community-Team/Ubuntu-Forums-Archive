---
title: "Upgrading from Ubuntu Studio OS 20.04 to 20.04.1 --- upgrades also all Creative Softw"
date: 2020-08-19
forum: Installation &amp; Upgrades
---

### Post by lsepolis123 on 2020-08-19
Upgrading from Ubuntu Studio OS 20.04 to >>> 20.04.1 --- upgrades also all Creative Software...?

Upgrading from Ubuntu Studio OS 19.10 or 19.04 or 18.04 to >>> 20.04/20.04.1 --- upgrades also all Creative Software...?

---

### Post by Impavidus on 2020-08-19
There is no release upgrade from 20.04 to 20.04.1. It's the same release of Ubuntu, the only thing that happened is that a new live disk image was released, with the regular upgrades from 23 April until 6 August already built in. If you have installed all the regular upgrades, there's no difference between 20.04 and 20.04.1.

There has never been an upgrade from 19.04 to 20.04. Support for 19.04 ended before 20.04 was released, so such an upgrade wouldn't make sense.

There is (or was) an upgrade from 19.10 to 20.04 (support for 19.10 ended about a month ago) and the upgrade from 18.04 to 20.04 is also available (or will be very soon). These upgrades will upgrade all software from the official Ubuntu repositories. Software from other sources is not automatically upgraded. Third-party repositories (PPAs) are disabled before the upgrade. You can re-enable them after the upgrade. The results from that depend on the decisions taken by the PPA's maintainers. In most PPAs you get the latest version of your software on older releases of Ubuntu too.

Snaps get automatically upgraded all the time and manually installed stuff can only be upgraded manually.

I don't see anything Creative in the official repositories, so it depends on how you installed it.

---

### Post by lsepolis123 on 2020-08-20
> **Impavidus said:**
> 

I don't see anything Creative in the official repositories, so it depends on how you installed it.



So in other words - for Ubuntu or Ubuntu Studio --- when ever you update or upgrade - Software came with the distribution, e.g. all creative software come preinstalled in Ubuntu Studio, are upgraded... correct? 

e.g. Not needed update/upgrade **Blender (came preinstalled) **when **Ubuntu Studio** went from **20.04 to 20.04.1**...? if were **existed update in Blender** Will applied... when update distribution, since was preinstalled...

Preinstalled Software --- Never needed manual upgrade in Ubuntu Studio, correct?

---

### Post by Impavidus on 2020-08-20
As you wrote "Creative Software" with capitals, I assumed you were writing about some (probably commercial) software bundle called "Creative Software". But as it appears you mean Blender and stuff like that, yes, everything preinstalled comes from the official repositories and you never have to worry about upgrading those. It all happens automatically with small, backported bugfixes. New releases of applications come whenever you upgrade to a new release of Ubuntu (Studio; or whatever flavour), like 18.04 to 20.04. 20.04 to 20.04.1 is not a release upgrade, so Blender stays at the same version (although you may have got bugfixes since the release of 20.04).

Only a few applications get upgraded to new releases within the same release of Ubuntu.

---

### Post by lsepolis123 on 2020-08-21
So, Normally never update preinstalled software alone... ?

---

### Post by CelticWarrior on 2020-08-21
Most software isn't updated unless there's a critical need. Exceptions are web browsers for obvious reason and a few others. During the release's cycle there will be be many security updates to core system packages and many software from PPAs also gets updates but most of the software included in any given release stays in the same version. That's why distros like Ubuntu tend to be stable and other distros with a different model/philosophy - rolling release - tend to have things breaking occasionally because it's always updating.

---

### Post by Impavidus on 2020-08-21
Everything that's preinstalled comes from the official repositories and everything from the repositories (both officlal and unofficial) is handled automatically by the package manager (and you shouldn't install any software that's not from the repositories. Well, sometimes you can't avoid it with printer drivers and stuff like that). Depending on how you configured your system, it's either fully automatic, or you get prompted, or you have to run the package manager yourself, but once the package manager is running, it will detect and install all upgrades automatically. So if you get a pop-up telling you that there are upgrades available and "Would you like to install them?", you say yes. That's what I call automatic. You don't have to look around yourself to see what upgrades are available, then somehow install them.

So don't worry about upgrades, just let the package manager do what it wants (which is installing upgrades).

Don't block upgrades, but don't try to do it manually either.

---

