---
title: "Synaptic Package Upgrade Problems"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by bamend on 2006-10-15
I'm trying to upgrade my synaptic packages to load edgy eft.  I run this command "sudo apt-get dist-upgrade" and get this message:

Reading package lists... Done
Building dependency tree... Done
Calculating upgrade... Done
The following packages have been kept back:
  build-essential dpkg-dev fakeroot g++ libc6-dev
0 upgraded, 0 newly installed, 0 to remove and 5 not upgraded.

So I open my synaptic program manager and try to tag one of these packages for upgrade.  When I try to upgrade build-essential for example I get this message:

build-essential:
  Depends: gcc (>=4:4.1.1) but 4:4.0.3-1 is to be installed
  Depends: g++ (>=4:4.1.1) but 4:4.0.3-1 is to be installed

The same sort of thing happens for each of the packages listed above.  What am I doing wrong?

---

### Post by hanzomon4 on 2006-10-15
I had a similar issue upgrading, my solution is one I would not suggest.
I uninstalled whatever app was not allowing me to upgrade(in your case gcc and g++)
Now this would cause me to remove other stuff, I basically uninstalled every package playing this little game.

Eventually I stopped getting dependence problems. I had copied the name of each package I removed to a text file. After I stopped getting the dependence problems I start reinstalling the packages I uninstalled by using the text file.

My advice find another way, my way is a headache.

---

