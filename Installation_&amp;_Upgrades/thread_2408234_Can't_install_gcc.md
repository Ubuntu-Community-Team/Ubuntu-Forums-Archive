---
title: "Can't install gcc"
date: 2018-12-15
forum: Installation &amp; Upgrades
---

### Post by DrRus on 2018-12-15
I need some help. I did a clean install of 18.04 and I am trying to install VMWare player. It needs "gcc", so I'm thinking - no big deal, ran "apt install gcc" and this is what I get:

```
sudo apt install gcc
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gcc : Depends: gcc-7 (>= 7.3.0-12~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
```

Trying to get gcc-7, I get:

```
sudo apt install gcc-7
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 gcc-7 : Depends: cpp-7 (= 7.3.0-16ubuntu3) but 7.3.0-27ubuntu1~18.04 is to be installed
         Depends: gcc-7-base (= 7.3.0-16ubuntu3) but 7.3.0-27ubuntu1~18.04 is to be installed
         Depends: libgcc-7-dev (= 7.3.0-16ubuntu3) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

```

Any help as to why I can't get these packages (and how to fix it) would be greatly appreciated!!

---

### Post by ubfan1 on 2018-12-15
Those are all old versions, with 7.3.0-27 the current one.  Did you first run sudo apt-get update?   I thought gcc was installed by default, no need to do anything.  You probably need the build-essential package (and the kernel header if no in the build-essential). g++ takes an explicit install if you need it.

---

### Post by DrRus on 2018-12-16
Yes, update/upgrade has been ran. And gcc is not installed. This is what I get when I try to install "build-essential":

```
The following packages have unmet dependencies:
 build-essential : Depends: gcc (>= 4:7.2) but it is not going to be installed
                   Depends: g++ (>= 4:7.2) but it is not going to be installed
                   Depends: dpkg-dev (>= 1.17.11) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

And when I try to install g++:

```
The following packages have unmet dependencies:
 g++ : Depends: gcc (>= 4:7.3.0-3ubuntu2) but it is not going to be installed
       Depends: g++-7 (>= 7.3.0-12~) but it is not going to be installed
       Depends: gcc-7 (>= 7.3.0-12~) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.


```

I really don't understand why it says "but it is not going to be installed" on all those packages...

---

### Post by DrRus on 2018-12-16
Well, just wanted to follow up, it seems I have resolved the problem, but who knows how much harm I did in the process :)

I ended up installing aptitude and using it to install gcc and build-essential. It had to downgrade a bunch of packages in the process, so only time will tell what issues this will cause in the future...

The whole reason for this was so I could install VMware Player, and as far as that task is concerned - mission accomplished. :)

---

### Post by ubfan1 on 2018-12-16
Probably some ppa resource brought in some old versions.  If problems persist, remove the extra ppas, do the apt-get update again, install build-essential and g++ (getting the current versions), then add the other ppa, run apt-get update again, and install again.

---

