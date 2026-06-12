---
title: "Avoid apt prompting on modified pkg files, and instead keep the modified files"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by piavlo on 2008-05-13
Hi,
I have several files i have modified and every time there is a new version for package (which contains the modified file)
I get prompted if i want to keep or override the modified file.

Setting up apt (0.7.6ubuntu14.1) ...

Configuration file `/etc/cron.daily/apt'
 ==> Modified (by you or by a script) since installation.
 ==> Package distributor has shipped an updated version.
   What would you like to do about it ?  Your options are:
    Y or I  : install the package maintainer's version
    N or O  : keep your currently-installed version
      D     : show the differences between the versions
      Z     : background this process to examine the situation
 The default action is to keep your current version.
*** apt (Y/I/N/O/D/Z) [default=N] ?

 Is there an option to tell apt to keep the modified files,
since i'm running updates unattended?

---

### Post by lemming465 on 2008-05-19
I think you can get the behavior you want using either *aptitude hold* from the command line or the *Package -> Lock version* menu pick in Synaptic.

---

### Post by gelowe on 2008-08-19
Have you read into the dpkg docs? They control a lot of the prompts that appear after apt has run.

---

