---
title: "Ubuntu 11.10 'clean install' versus upgrading from update manager?"
date: 2011-12-04
forum: Installation &amp; Upgrades
---

### Post by dandylion on 2011-12-04
Hey all!

I am quite confused on the differences between upgrading the OS through the update manager versus upgrading it by installing it versus a cd. You see i originally had 11.10 installed on my netook, and to my dismay it ran VERY slow. I later decided to install an earlier version(10.04) and it ran lightning quick ^.^ For one reason or another, i eventually upgraded to 11.04 and then to 11.10, and it was actually VERY fast. Weird, no?

So being a fool for love, I let my significant other borrow my tiny netbook (HP 210), and he ended up messing things up via the terminal. I decided to just re-install 11.10 AGAIN and now its back to its sluggish routine. My question is... WHY?

I already attempted a few quick fixes such as adjusting my swappiness, but nothing ive done has really done much help. Should I just tediously re-install 10.04 and then update?

---

### Post by zvacet on 2011-12-05
It sounds very strange,but if it work for you...Anyway if you decide to install 10.04 maybe you can stick with it,because in April will be released next LTS and you will have 3 years support for that version.Of course if you don´t need latest software right now.

---

### Post by critin on 2011-12-05
> the differences between upgrading the OS through the update manager versus upgrading it by installing it versus a cd.

I assume you meant 'installing via a cd'?

The difference is upgrading through the update manager add new and deletes old packages, dependencies differ from version to version.  

Installing through a cd is a fresh install with no prior packages to deal with--it's a clean page.

Installing clean is sometimes best, and some users have no problems with simply upgrading.  Users choice.

If you upgrade from 10.04 to 11.10, I believe you have to upgrade to 10.10, then 11.04, then finally to 11.10.  That's a lot of stress and packages for the updater to wade through.  

If you install 10.04, which is a very good version, you can safely upgrade directly to 12.04 when it's released.  By then most of the 11.10 bugs should be worked out.

---

