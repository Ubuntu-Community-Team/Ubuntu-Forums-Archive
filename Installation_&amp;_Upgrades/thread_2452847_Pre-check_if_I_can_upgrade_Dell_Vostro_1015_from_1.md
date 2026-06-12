---
title: "Pre-check if I can upgrade Dell Vostro 1015 from 16.04 to 18.04"
date: 2020-10-29
forum: Installation &amp; Upgrades
---

### Post by InfiniteStudent on 2020-10-29
This old 32 bit CPU machine is still working for me and I am keeping it updated at 16.04LTS.

I am concerned about trying to upgrade to OS to 18.04 because this machine is critical for me.

I would like to have someone with experience with this matter respond with information about their experience processing this upgrade.

Thank you.

---

### Post by crip720 on 2020-10-29
Should be able to upgrade to 18.04, but that is the last upgrade for 32bit.  You can't upgrade to or install 20.04.  If any important data on machine, should have backup just in case.  Will have to change distro if you want to upgrade in the future.

---

### Post by crip720 on 2020-10-29
I would check that your CPU is only 32bit.  Quite a few 64bit CPUs came with a 32bit OS.  Might be able to change to 64bit OS, but does require a full install, not upgrade, with lost of data if not backup.

---

### Post by CelticWarrior on 2020-10-29
Dell Vostro 1015 is definitely 64-bit ([COLOR=#000000]Intel Core 2 Duo). And yes, it was sold with Windows 7 32-bit.[/COLOR]

---

### Post by guiverc on 2020-10-29
Windows is often sold on consumer grade PCs in 32bit (esp. xp, vista & 7) as it was $5 cheaper and consumers understood $5 more than they understood *32 vs 64bit*s.  (*Microsoft also used the price difference to upsell; limited 32-bit windows to ~4GB of RAM when no such limitation actually existed outside of ms windows*).

If it's a desktop, you can upgrade via re-install, allowing you to switch from a 32-bit (i386) system to 64-bit (amd64), use *something-else*, select your existing partitions and don't format. That was how I switched my then 32bit system on a dell optiplex 755 to *amd64*.  This may also work with servers, but there are more complications on servers.

What complications you have will mostly depend on what applications you have installed. If you've limited 3rd party (*PPA or other non-Canonical/Ubuntu repository software*) you should not expect problems, however the more 3rd party packages you've added your potential for problems increases. It'll depend on those 3rd party packages added & who built/maintained them (*were they built in a way to allow upgrade? or they only considered then-existing packages*).

There is also some complications due to software reaching it's EOL, eg. *python2* & *Qt4* (*Qt4 actually was surpassed in 2012 with Qt5, but it was supported until 2019 in Debian & Ubuntu*). This won't impact a 16.04->18.04 upgrade, but will for example impact a 18.04->20.04 upgrade as those packages you may have that rely on Qt4, that weren't ported to Qt5 could create problems in upgrade, or not work on 20.04; I'm using that as example only.

I don't remember what the key changes were back in 2016-2018 any longer (*nor do I know your use case*), I was using Qt4 & python2 only in example (*a ~recent example** encountered by 18.04 to 20.04 upgraders*).

---

### Post by InfiniteStudent on 2020-11-03
> **guiverc said:**
> Windows is often sold on consumer grade PCs in 32bit (esp. xp, vista & 7) as it was $5 cheaper and consumers understood $5 more than they understood *32 vs 64bit*s.  (*Microsoft also used the price difference to upsell; limited 32-bit windows to ~4GB of RAM when no such limitation actually existed outside of ms windows*).

If it's a desktop, you can upgrade via re-install, allowing you to switch from a 32-bit (i386) system to 64-bit (amd64), use *something-else*, select your existing partitions and don't format. That was how I switched my then 32bit system on a dell optiplex 755 to *amd64*.  This may also work with servers, but there are more complications on servers.

What complications you have will mostly depend on what applications you have installed. If you've limited 3rd party (*PPA or other non-Canonical/Ubuntu repository software*) you should not expect problems, however the more 3rd party packages you've added your potential for problems increases. It'll depend on those 3rd party packages added & who built/maintained them (*were they built in a way to allow upgrade? or they only considered then-existing packages*).

There is also some complications due to software reaching it's EOL, eg. *python2* & *Qt4* (*Qt4 actually was surpassed in 2012 with Qt5, but it was supported until 2019 in Debian & Ubuntu*). This won't impact a 16.04->18.04 upgrade, but will for example impact a 18.04->20.04 upgrade as those packages you may have that rely on Qt4, that weren't ported to Qt5 could create problems in upgrade, or not work on 20.04; I'm using that as example only.

I don't remember what the key changes were back in 2016-2018 any longer (*nor do I know your use case*), I was using Qt4 & python2 only in example (*a ~recent example** encountered by 18.04 to 20.04 upgraders*).

Thank you for all the replys.

I consider this questions solved.

Carl

---

