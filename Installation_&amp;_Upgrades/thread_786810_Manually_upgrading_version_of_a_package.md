---
title: "Manually upgrading version of a package"
date: 2008-05-08
forum: Installation &amp; Upgrades
---

### Post by mickey78 on 2008-05-08
Hello guys.

First, im not a Linux expert.

I run a small server, and I go "by the packages"... My questions is about the "clean" way of manually upgrading a package installed by apt-get install command. 

And NO, i am not talking about the apt-get update and upgrade command.... What I mean is, for example, the package in  my release of ubuntu is VERY inferior to the real package verison.

For instance, I have installed cacti, but the package in ubuntu (7.10) is old. Same for phpmyadmin and so on.

I know those 2 would have been fairly easy to install without the package, but lets stay focus on my main question.

Also, what when I'll need to upgrade apache or php or mysql for instance? How will ubuntu keep track of them if i upgrade or recompile them manually?

Anyways, thanks for helping me out!!

---

### Post by lemming465 on 2008-05-10
In general, once you start playing with your own versions of packages, you have to do your own follow-on support.  The large and more inter-related things get, the more work this will be.

One option, typical for folks running Debian testing, is to use the fancier features of dpkg to use specific newer versions of packages from experimental repositories, while keeping most of their system on more stable versions.  This has a learning curve to set up, but helps keep maintenance costs lower.

The other method is to remove the supplied package and install your own from upstream source.  With stuff as complicated as Apache I tend to prefer to pick Linux distributions with the versions I want. PHP or Mysql or Cacti by themselves probably aren't too bad.  I wrote up a presentation on [building tools from source]("https://mywebspace.wisc.edu/jeleinwe/web/BTS") for a class of forensics students last year, which you might find helpful.

---

