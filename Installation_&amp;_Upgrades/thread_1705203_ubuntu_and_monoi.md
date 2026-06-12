---
title: "ubuntu and monoi"
date: 2011-03-11
forum: Installation &amp; Upgrades
---

### Post by haroldh7 on 2011-03-11
I would like to see when installing ubuntu a choice for users to choose what they want installed on their system or not.
I know for a fact that there are some like myself that does not want mono runtime files or mono apps on their linux box and when we try to uninstall all the files or apps that link with mono ends up breaking the linux box.

My question is why can't ubuntu make a distro of ubuntu that offers to users the files and apps for use with mono and a choice for those users to install ubuntu with out the mono files or apps.

There are somne of us that think mono is as bad as .net and some of us want a linux box that runs linux and not window files or apps unless they can be written as pure linux code and not C# crap.
I feel that C or C++ is the real way to write linux code and anything written in C# is windows and always will be windows.

If they want to put more windows stuff on ubuntu, then they shouldn't be calling it linux..

This is my idea and my opinion.

---

### Post by directhex on 2011-03-11
> **haroldh7 said:**
> I would like to see when installing ubuntu a choice for users to choose what they want installed on their system or not.

This is intentionally not offered as the Ubuntu developers are unable to properly integrate more than one app for a given task - so they simply pick one app to target and target fully. If you want to pick your packages, install from a Server Edition CD, then install what you like.

> I know for a fact that there are some like myself that does not want mono runtime files or mono apps on their linux box and when we try to uninstall all the files or apps that link with mono ends up breaking the linux box.

This is categorically false. The only time people break things is when they uninstall the package "ubuntu-mono" which has nothing to do with the Mono framework - it's a set of monochrome icons. The Mono applications and libraries installed by default in Ubuntu can be cleanly removed without fuss - the ubuntu-mono icons can not.

> My question is why can't ubuntu make a distro of ubuntu that offers to users the files and apps for use with mono and a choice for those users to install ubuntu with out the mono files or apps.

See answer to first section. There isn't enough manpower to do everything twice for multiple target apps - e.g. rewriting the Ubuntu One synchronization support in C++ to use in Gnote rather than Tomboy.

> There are somne of us that think mono is as bad as .net and some of us want a linux box that runs linux and not window files or apps unless they can be written as pure linux code and not C# crap.

So run a Linux box without the apps you don't want, you're entirely within your rights to do that.

> I feel that C or C++ is the real way to write linux code and anything written in C# is windows and always will be windows.

Contribute superior C or C++ code, and it'll get picked over the C# alternative - see Shotwell/F-Spot.

> If they want to put more windows stuff on ubuntu, then they shouldn't be calling it linux..

No C# apps in Ubuntu were written on or for Windows. Calling them "Windows stuff" is pretty disingenuous.

---

