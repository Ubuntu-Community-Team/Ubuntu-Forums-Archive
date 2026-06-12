---
title: "New Lubuntu Install: libqt4"
date: 2022-04-09
forum: Installation &amp; Upgrades
---

### Post by bugenhagen2014 on 2022-04-09
I just did a fresh install of Lubuntu 20.04 and I was trying to install software. Got this message:

he following packages have unmet dependencies:
 plume-creator:i386 : Depends: libqt4-gui:i386 (>= 4.8.3) but it is not installable
                      Depends: libqt4-core:i386 (>= 4.8.3) but it is not installable
                      Depends: libqt4-xml:i386 (>= 4.8.3) but it is not installable
                      Depends: libqt4-network:i386 (>= 4.8.3) but it is not installable
                      Depends: libhunspell-1.3-0:i386 (>= 1.3.2) but it is not installable
E: Unable to correct problems, you have held broken packages.

I hunted down a repository called 'rock core' and added it:

More info: [https://launchpad.net/~rock-core/+archive/ubuntu/qt4](https://launchpad.net/~rock-core/+archive/ubuntu/qt4)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Hit:1 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal InRelease           
Get:2 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) focal-security InRelease [114 kB]
Hit:3 [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) focal InRelease                                         
Get:4 [http://ppa.launchpad.net/rock-core/qt4/ubuntu](http://ppa.launchpad.net/rock-core/qt4/ubuntu) focal InRelease [18.0 kB]                     
Get:5 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-updates InRelease [114 kB]
Get:6 [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) focal-backports InRelease [108 kB]
Get:7 [http://ppa.launchpad.net/rock-core/qt4/ubuntu](http://ppa.launchpad.net/rock-core/qt4/ubuntu) focal/main amd64 Packages [17.7 kB]
Get:8 [http://ppa.launchpad.net/rock-core/qt4/ubuntu](http://ppa.launchpad.net/rock-core/qt4/ubuntu) focal/main i386 Packages [1,232 B]
Get:9 [http://ppa.launchpad.net/rock-core/qt4/ubuntu](http://ppa.launchpad.net/rock-core/qt4/ubuntu) focal/main Translation-en [4,244 B]
Fetched 377 kB in 5s (76.7 kB/s)            
Reading package lists... Done

Still have broken packages. Can anyone help?

Thanks

---

### Post by deadflowr on 2022-04-09
Your error relates to 32-bit packages which nether Ubuntu nor the PPA provide.
[s]I'm not really sure what your options are going forward.[/s]

You could keep digging through Launchpad to see if any PPA exist that build the required 32-bit packages.
You could try building the required packages yourself from source.
You could try running the program inside a virtual machine or container which itself would be running an older version of Ubuntu that still supports those packages required.
You could try and find a 64-bit version of the program, which would hopefully do away with the need for any 32-bit packages.

Edit: I guess I do know of some options

Double Edit:
I forgot to mention, for the record, that the :i386 means 32-bit, which how I could tell.

---

### Post by ActionParsnip on 2022-04-09
What is the output of
```

lsb_release -a; uname -a

```

---

### Post by bugenhagen2014 on 2022-04-09
Thanks for all the input! After a couple hours of data mining, I found out the Qt 32 bit libs won't work with 20.04. I went to LXDE because I needed the extra 1.5 gig of ram Unity was eating. I have an 2008 crappy intel workstation with an I5 and 8g ram. So, what I did, since this is a fresh install, I rolled back to 18.04.5 and problem solved.

---

