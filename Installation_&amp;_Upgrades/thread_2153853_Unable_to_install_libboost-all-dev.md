---
title: "Unable to install libboost-all-dev"
date: 2013-06-12
forum: Installation &amp; Upgrades
---

### Post by warlock1990 on 2013-06-12
Hi, 
I need to install this package for setting up gnu-radio on my system. However when I'm trying to install this dependency I'm getting an error as:

The following packages have unmet dependencies:
 libboost-all-dev : Depends: libboost-dev but it is not going to be installed
                    Depends: libboost-date-time-dev but it is not going to be installed
                    Depends: libboost-filesystem-dev but it is not going to be installed
                    Depends: libboost-graph-dev but it is not going to be installed
                    Depends: libboost-graph-parallel-dev but it is not going to be installed
                    Depends: libboost-iostreams-dev but it is not going to be installed
                    Depends: libboost-math-dev but it is not going to be installed
                    Depends: libboost-mpi-dev but it is not going to be installed
                    Depends: libboost-mpi-python-dev but it is not going to be installed
                    Depends: libboost-program-options-dev but it is not going to be installed
                    Depends: libboost-python-dev but it is not going to be installed
                    Depends: libboost-regex-dev but it is not going to be installed
                    Depends: libboost-serialization-dev but it is not going to be installed
                    Depends: libboost-signals-dev but it is not going to be installed
                    Depends: libboost-system-dev but it is not going to be installed
                    Depends: libboost-test-dev but it is not going to be installed
                    Depends: libboost-thread-dev but it is not going to be installed
                    Depends: libboost-wave-dev but it is not going to be installed
E: Unable to correct problems, you have held broken packages.

---

### Post by Bashing-om on 2013-06-12
[COLOR=#000000]warlock1990; Hi ! back at ya ..

What version/distro are you using ?
What method are you using to install "gnu-radio" ? That application is not listed in the 13.04 software repositories.
Are you stepping outside the norm ?
[/COLOR][INDENT=2][COLOR=#000000]
help us to help you

[/COLOR][/INDENT]

---

### Post by warlock1990 on 2013-06-12
Hi Bashing-om, thanks for replying to this thread.

I'm using Ubuntu 12.04. 
I'm trying to install gnu-radio using precompiled binaries. 
The 'libboost-all-dev' is on of the dependencies for gnu-radio and I'm unable to go ahead without installing this first.

---

### Post by steeldriver on 2013-06-12
Hmm... I don't understand why you'd need any -dev packages to install precompiled binaries - those should only be required if you are trying to build from source

I don't think that error is likely to be anything to do with libboost-*-dev specifically - you will probably need to fix your broken package situation regardless e.g.

```

sudo apt-get install -f
sudo dpkg --configure -a
sudo apt-get clean
sudo apt-get update

```

FWIW I have all (I think) of the libboost-*-dev packages on my 12.04.02 box and have built gnuradio-3.2.2 from source on it at one time (although iirc I never went as far as 'make install' so I can't be 100% sure the build worked)

---

