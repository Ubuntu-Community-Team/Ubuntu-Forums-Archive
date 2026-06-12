---
title: "Doubt about update and upgrade commands."
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by arroy_0209 on 2012-02-05
I am using ubuntu 10.04 LTS. I am confused about effect of the commands:
"sudo apt-get update and sudo apt-get upgrade". Occasionally I receive automatic messages on the monitor suggesting "important security updates" and "recommended updates". I always install the security packages but selectively install the recommended updates since I think I will not need all of these. Now, customarily before installing a new package we are advised to use both the above commands. My doubt is, if I use these commands, will the recommended but not installed packages will also be installed (which I don't want)?

Another issues is, based on the output of command iname -a:
```

Linux xyz-desktop 2.6.32-38-generic #83-Ubuntu SMP... ...2012 i686 GNU/Linux

``` Should I choose the i386 architecture of some package (rather than amd64) for installation?

---

### Post by shakabra on 2012-02-05
The "update" command is updating the cache of software sources. When it does this it looks to see if the software you already have installed has a newer version in the repositories. If there is a newer version then you can use the "upgrade" command will install it. This is normally desired. The "upgrade" command doesn't install new software per se. It merely upgrades what is already there, usually with bug fixes and new features. Of course, if you don't want to upgrade your packages you don't have to.

As for installing new software, when you add a software source to your sources.list then you need to run the "update" command to install the new package. This makes your package manager aware of the new sources. You do not have to run the "upgrade command.

[QUOTE]Another issues is, based on the output of command iname -a:
 	Code:
 	Linux xyz-desktop 2.6.32-38-generic #83-Ubuntu SMP... ...2012 i686 GNU/Linux 
 Should I choose the i386 architecture of some package (rather than amd64) for installation?[QUOTE]

I think you mean "uname -a". I believe that generally your package manager is going to determine the correct architecture for your machine unless you force it to do otherwise.


I hope this clarifies things for you.

---

