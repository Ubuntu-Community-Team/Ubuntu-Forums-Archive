---
title: "Install a package for LTS Ubuntu's on a non-LTS Ubuntu"
date: 2010-09-25
forum: Installation &amp; Upgrades
---

### Post by flylehe on 2010-09-25
I am still using Intrepid (Ubuntu 8.10). Now I want to install some package from PPA ([https://launchpad.net/~jd-team/+archive/jdownloader](https://launchpad.net/~jd-team/+archive/jdownloader)). The package offers several versions for several long term support versions of Ubuntu, including Hardy (8.04), Jaunty (9.04),...., but not Intrepid (8.10).

I was wondering if I can choose the version for Hardy to install on my Intrepid? Specifically, if I add to my /etc/apt/sources.list the following sources:
> 
deb [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) hardy main 
deb-src [http://ppa.launchpad.net/jd-team/jdownloader/ubuntu](http://ppa.launchpad.net/jd-team/jdownloader/ubuntu) hardy main 

Will it work on my Intrepid? What shall I do to install the package on my Intrepid?

Thanks and regards!

---

### Post by mörgæs on 2010-09-26
8.10 is unsupported and hence a security threat. Better to try a live boot of 10.04 and afterwards a clean install, if the boot works well.

---

