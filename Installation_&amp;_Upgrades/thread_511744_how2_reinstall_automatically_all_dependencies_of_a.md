---
title: "how2 reinstall automatically all dependencies of a package?"
date: 2007-07-28
forum: Installation &amp; Upgrades
---

### Post by frafu on 2007-07-28
Hello,

Could anybody please tell me if there is a way to automatically reinstall all dependencies of a package (even if they seem already installed)? 

Thanks in advance. 

Francesco

---

### Post by kidders on 2007-07-29
Hi there,

There is no easy way to do this. It's not really something people normally need, since it would invariably result in the reinstallation of half a person's system, in most cases ... which could have unpredictable results. Consider, for instance, how many dependencies something simple like Kate is likely to have!

---

### Post by frafu on 2007-07-29
Hello, 

Thanks for your reply. 

In fact, I was aiming at the opposite: my intention was to fix a few things by reinstalling ubuntu-desktop. 

Maybe there is another way, to make ubuntu reinstall everything that comes with a standard installation (in fact, playing around, I lost several configuration panels), but keeping custom configurations? (Similar to what happens with a dist-upgrade.) 

Francesco

---

### Post by kidders on 2007-07-29
Ahhh... I see. Personally, I'd opt for a more "targeted" approach, and only reinstall the things that *need* to be reinstalled. ubuntu-desktop depends on an awful lot of packages. :-(

I wonder if some web searching would turn up a reasonably comprehensive list of the packages an ubuntu server release would go looking for if asked to do an "apt-get install ubuntu-desktop". Such a list might cover your needs, in that it'd leave out a lot of the deeper dependencies, and wouldn't include anything that depends on ubuntu-desktop either. Unfortunately, I can't construct the list for you myself ... the only server release I have is Dapper, at the moment.

---

### Post by frafu on 2007-07-29
@kidders

Thanks to your reply I know that there is not an automatic way to reinstall a package with all its dependencies. Thus I will go with the targeted approach trying to fix the problems when the need for it arises. 

I have looked at the Depends of the ubuntu-desktop package, and considering their number, the targeted approach seems more sensible.  ;)

Thanks again for your explanations. 

Francesco

---

