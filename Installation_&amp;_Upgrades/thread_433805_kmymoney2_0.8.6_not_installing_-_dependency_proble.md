---
title: "kmymoney2 0.8.6 not installing - dependency problems!"
date: 2007-05-05
forum: Installation &amp; Upgrades
---

### Post by daller on 2007-05-05
Hi there,

I'm trying to install KMyMoney2 version 0.8.6, but it rusn into dependency-problem...

madsen@ubuntu:~/dl$ sudo dpkg -i kmymoney2_0.8.6-1_kde3.4.2_i386.deb
(Læser database... 210151 filer og mapper aktuelt installeret.)
Gør klar til at erstatte kmymoney2 0.8.5-1build1 (med kmymoney2_0.8.6-1_kde3.4.2_i386.deb)...
Udpakker erstatning kmymoney2...
dpkg: afhængighedsproblemer forhindrer konfiguration af kmymoney2:
 kmymoney2 afhænger af kdelibs4 (>= 4:3.4.1-1), men:
  Pakken 'kdelibs4' er ikke installeret.
 kmymoney2 afhænger af libqt3c102-mt (>= 3:3.3.4.3), men:
  Pakken 'libqt3c102-mt' er ikke installeret.
dpkg: fejl under behandling af kmymoney2 (--install):
 afhængighedsproblemer - efterlader den ukonfigureret
Der opstod fejl under behandlingen:
 kmymoney2

It's in danish, but the message is: KMYMoney could not be installed due to unmet dependencies (kdelibs4, libqt3c102-mt)

kdelibs4 has no installation-candidate, but kdelibs4c2a (which is already installed!) can replace it...
libqt3c102-mt has no accesible version, but libqt3-mt (which is already installed!) can replace it...

I'm running Kubuntu 7.04 Feisty Fawn

...What can I do to fix this?

---

### Post by zvacet on 2007-05-08
```
sudo aptitude install kdelibs4 libqt3c102-mt
```

---

### Post by daller on 2007-05-08
> **zvacet said:**
> ```
sudo aptitude install kdelibs4 libqt3c102-mt
```

kdelibs4 has no installation-candidate, but kdelibs4c2a (which is already installed!) can replace it...
 libqt3c102-mt has no accesible version, but libqt3-mt (which is already installed!) can replace it...

---

### Post by daller on 2007-05-26
Any solution to this problem?

The 2 mentioned packages still "has no candidate-version available"

What do I do?

---

### Post by dasbooter on 2007-05-27
Hello everybody this is my first post to these forums ever!

I was a long time Suse user(maybe 5 or 6 years now) and would really like to get the updated version of kmymoney2  going as I was used to all the bells and whistles that the latest cvs version which was routinely built by third party package repos(guru or packman).

I am getting the same dependency issue that is listed in this thread but I also found the new version at what appears to be an ubuntu build service here [https://answers.launchpad.net/+builds/+build/323427/kmymoney2](https://answers.launchpad.net/+builds/+build/323427/kmymoney2). the package is for gutsy which I am thinking is like Suse factory. The funny thing is when I try and install this package it gives me another dependency error. libart-2.0-2 is not satisfiable. A quick check in synaptic shows that very package(not a variant) is already installed.

Sorry not helping much maybe this little bump will help though, or maybe there is a gutsy repo that will get the package installed?

---

### Post by Hei Ku on 2007-08-20
Sorry, but I had not seen this earlier. I found it by chance while searching in kde-apps.org.

If you want to compile from source, to get the latest kmymoney version, you should install kdelibs4-dev package.
That package has all the required headers needed to compile and install. At least, from the tests I have ran in a feisty and a breezy install with 0.8.7 version.

Feel free to contact me if you have any more problem. I am not of the kmymoney devel team, but I help support it in kubuntu every now and then.

If you want a more expert support, you can contact the dev team directly in [http://kmymoney2.sourceforge.net](http://kmymoney2.sourceforge.net). Write an email to the development support list and I assure you will get all the needed help.

---

### Post by daller on 2007-09-30
Failed to get 0.8.6 working, so stuck with 0.8.5...

...now it's time to try 0.8.7

Trying to compile 0.8.7 I get this: (./configure)

```

checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check

```

What can I do to fix this?

---

### Post by dasbooter on 2007-10-03
Sorry cant help but I am following this thread still. I am actually running kmymoney cvs from a suse vmware install, which is really ridiculous, but oh well

---

### Post by Schlomy on 2007-11-19
I am having the same problem and none of these solutions seem to work. If I try to install, either from source or binary, libs4ktdc or any variant thereof, I simply get the error that a later version is installed, which is true. 

This is especially strange, because I had KMyMoney running on Gutsy before but had to reinstall and now it won't run.

I tried installing KMyMoney from the Deb file, with the libs4 error. When I tried from source I got this:

checking if C++ programs can be compiled... no
configure: error: Your Installation isn't able to compile simple C++ programs.
Check config.log for details - if you're using a Linux distribution you might miss
a package named similar to libstdc++-dev.


On a side note, I swear that I installed KMyMoney from the Adept Installer with Gutsy as an included package. Now its not there. Wierd.

Hope you guys can help! I have all my finances backed up for KMyMoney and now I can't acces them!

Peace!

---

### Post by Schlomy on 2007-11-20
Ok I fixed the problem, but I'm not sure this will be all that helpful to others, since I am the linux-enthusiast version of the hunt and peck typist. And I'm not in the habit of documenting every little step, so when I stumble across the solution, I'm not always sure what I've done. But here goes....

When I tried to install KMyMoney from source, I got a different error than from the Deb installer, basically that my glibc++ was not installed. Which wasn't true, I had the file the terminal said, but I went back to Synaptic, did a search for c++ and basically installed every c++ program that made any sense at all whether I knew what it was for or not. Somewhere in there I hit the right one, because when I tried to configure again, everything worked fine. 

Not elegant, but it worked for me.

Peace!

---

