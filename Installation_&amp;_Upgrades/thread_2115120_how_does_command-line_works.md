---
title: "how does command-line works?"
date: 2013-02-12
forum: Installation &amp; Upgrades
---

### Post by prince0fpersia on 2013-02-12
hi

i am beginner in ubuntu 12.04 and i dont know how command-line into it works?
i am trying to install open-cv 2.4.3 in it but i have some problems .

for example when i have tried to run this code :
sudo apt-get install libpnglite-dev libpngwriter0-dev libpngwriter0c2

i received this results :
```
Reading package lists... Done
Building dependency tree
Reading state information... Done
E: Unable to locate package libpngwriter0-dev
E: Unable to locate package libpngwriter0c2
```what is the problem?
i am doing it by following this instruction : opencv.willowgarage.com/wiki/InstallGuide %3A Debian

Generally i want to know how i can use the command-line?
how should i run this codes :
```
cd ~/<my_working _directory> git clone https://github.com/Itseez/opencv.git
```or i cant understand this instruction :


[LIST=1]
[*]Create a temporary directory, which we denote as  <cmake_binary_dir>, where you want to put the generated Makefiles,  project files as well the object files and output binaries.
[*]Enter the <cmake_binary_dir> and type
 cmake [<some optional parameters>] <path to the OpenCV source directory> 
 
 For example
 cd ~/opencv mkdir release cd release cmake -D CMAKE_BUILD_TYPE=RELEASE -D CMAKE_INSTALL_PREFIX=/usr/local ..
[*]Enter the created temporary directory (<cmake_binary_dir>) and proceed with:
 make sudo make install
[/LIST]


[SIZE=3]**[COLOR=Red]may anyone explain that how i should and what i should write in command line?[/COLOR]**[/SIZE]

i am very grateful to him

---

### Post by dino99 on 2013-02-12
Following external howto can help indeed, but as it concern ubuntu, its better to follow:

[https://help.ubuntu.com/community/OpenCV](https://help.ubuntu.com/community/OpenCV)

---

### Post by ibjsb4 on 2013-02-12
E: Unable to locate package libpngwriter0-dev E: Unable to locate package libpngwriter0c2

They simply don't exist.

Is this homework?

---

### Post by dino99 on 2013-02-12
> **ibjsb4 said:**
> E: Unable to locate package libpngwriter0-dev E: Unable to locate package libpngwriter0c2

They simply don't exist.

Is this homework?

[http://packages.ubuntu.com/en/lucid/libpngwriter0-dev](http://packages.ubuntu.com/en/lucid/libpngwriter0-dev)

---

### Post by ibjsb4 on 2013-02-12
> **dino99 said:**
> you might want to open your own thread instead spamming someone else  :o

[http://packages.ubuntu.com/fr/lucid/libpngwriter0-dev](http://packages.ubuntu.com/fr/lucid/libpngwriter0-dev)

Did you read post #1?

And your link points to Hardy 8.04, thats not much help :)

---

### Post by dino99 on 2013-02-12
> **ibjsb4 said:**
> Did you read post #1?

And your link points to Hardy 8.04, thats not much help :)

sometimes i read too quickly, my bad ;)

but if yourself pay attention, that link point to LUCID
(that package does not exist on more recent ubuntu release, but should probably work)

can be downloaded from here too:
[https://launchpad.net/ubuntu/+source/pngwriter](https://launchpad.net/ubuntu/+source/pngwriter)

---

### Post by bantuvez on 2013-02-12
LOL. dino99. You should receive a *Golden Raspberry Award *for that comment. XD

---

### Post by dino99 on 2013-02-12
> **bantuvez said:**
> LOL. dino99. You should receive a *Golden Raspberry Award *for that comment. XD

yes i know   :D:D:D

note: that package is only a virtual package

[http://www.debian.org/doc/debian-policy/ch-binary.html#s-virtual_pkg](http://www.debian.org/doc/debian-policy/ch-binary.html#s-virtual_pkg)

---

### Post by ibjsb4 on 2013-02-12
I guess Lucid is a better option for Precise.  Time for me to move on :)

---

