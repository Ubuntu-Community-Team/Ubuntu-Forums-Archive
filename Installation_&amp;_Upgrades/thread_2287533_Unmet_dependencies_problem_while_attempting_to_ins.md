---
title: "Unmet dependencies problem while attempting to install Wine"
date: 2015-07-20
forum: Installation &amp; Upgrades
---

### Post by ashwary2 on 2015-07-20
While attempting to install Wine from the software center i'm getting the following error message:
[B]
Package dependencies cannot be resolved[/B]

details- The following packages have unmet dependencies:

unity-control-center: Depends: libpulse-mainloop-glib0 (>= 1:0.99.1) but 1:4.0-0ubuntu11.1 is to be installed
                      Depends: libpulse0 (>= 1:0.99.1) but 1:4.0-0ubuntu11.1 is to be installed
                      Depends: libxi6 (>= 2:1.2.99.4) but 2:1.7.1.901-1ubuntu1.1 is to be installed
wine1.6: Depends: wine1.6-amd64 (= 1:1.6.2-0ubuntu4) but 1:1.6.2-0ubuntu4 is to be installed
         Depends: wine1.6-i386 (= 1:1.6.2-0ubuntu4) but it is a virtual package



Please see the attachments!

---

### Post by ian-weisser on 2015-07-20
You seem to be trying to install a very old version of Wine.

What version of Ubuntu are you running? 12.04? 14.04?
Are you following instructions from someplace? If so, please provide the link.
Did you add a PPA or other non-Ubuntu repository as part of this process?
Did you already download and/orinstall something as partof this process? If so, what?
In your two screenshots, the problems are different. Did you change something?

---

### Post by ashwary2 on 2015-07-20
Thanks a lot for replying. Sorry for being less descriptive. But it's been only 2 days since i started using GNU/linux. 

I'm using 14.04. I followed instructions from a youtube video ([https://www.youtube.com/watch?v=yvhahmvyxJ0](https://www.youtube.com/watch?v=yvhahmvyxJ0)) and later a webpage ([http://askubuntu.com/questions/364798/unmet-dependencies-while-installing-wine](http://askubuntu.com/questions/364798/unmet-dependencies-while-installing-wine))

Yes. I did add a non-Ubuntu repository.

I tried a few solutions after googling the issue. particularly this (i didn't follow all the solutions as i was not able to understand which one applied in my case):- [http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa](http://askubuntu.com/questions/140246/how-do-i-resolve-unmet-dependencies-after-adding-a-ppa)

and this- [http://askubuntu.com/questions/563178/the-following-packages-have-unmet-dependencies](http://askubuntu.com/questions/563178/the-following-packages-have-unmet-dependencies)

and this -http://askubuntu.com/questions/499663/unity-control-center-uninstalled-itself

Past two days i've run many commands and i may have messed something up. 

I did try to install various versions, first from the software center directly, that didn't work so i went on to add a repo and tried installing 1.5 and 1.7. but failed both times.

---

### Post by ian-weisser on 2015-07-20
Ah, you have followed random instructions off the internet (that YouTube video), with unfortunate results.
A better source would be [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) . The YouTube method your followed falls under 'Newer Versions of Wine (Not Recommended)' 

First, you need to get your package manager working again. Without your package manger, you're *really* stuck (and won't get security updates).

1) Uninstall Wine    [sudo apt-get remove wine; sudo apt-get autoremove]
2) Delete the Wine package from your local package cache (so your system must download a new package)    [sudo apt-get clean wine]
3) Disable those non-Ubuntu sources (so your system will download the new package from official sources)
4) Install Wine    [sudo apt-get install wine]

After your package manager is working again, we can look into why Wine isn't working for you.

---

