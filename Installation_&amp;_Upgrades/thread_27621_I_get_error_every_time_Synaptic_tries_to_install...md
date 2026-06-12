---
title: "I get error every time Synaptic tries to install..."
date: 2005-04-16
forum: Installation &amp; Upgrades
---

### Post by Turin Turambar on 2005-04-16
....sdl-mixer package.

Here's what it says:

E: /var/cache/apt/archives/libsdl-mixer1.2_1.2.5-9_i386.deb:  trying to overwrite `/usr/lib/libSDL_mixer-1.2.so.0', which is also in package sdl-mixer

Every time I enter Synaptic, it says that there are some broken packages. And sdl-mixer is the one. How can I fix this problem?

---

### Post by Turin Turambar on 2005-04-17
I tried with apt-get -f install and here's what I got:

```
Get:1 http://archive.ubuntu.com hoary/main libsdl-mixer1.2 1.2.5-9 [121kB]
Fetched 121kB in 36s (3334B/s)

Preconfiguring packages ...
(Reading database ... 76511 files and directories currently installed.)
Unpacking libsdl-mixer1.2 (from .../libsdl-mixer1.2_1.2.5-9_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/libsdl-mixer1.2_1.2.5-9_i386.deb (--unpack):
 trying to overwrite `/usr/lib/libSDL_mixer-1.2.so.0', which is also in package sdl-mixer
Errors were encountered while processing:
 /var/cache/apt/archives/libsdl-mixer1.2_1.2.5-9_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

At first I couldn't even install sdl-mixer with apt-get, so I downloaded the .rpm file from sdl site. I installed the package with alien.
Then I have updated the apt-get source list and sdl-mixer showed up in the list. You know the rest.

Did I screw up something?

---

### Post by c_dog on 2005-04-17
Sounds like you are trying to load different deb builds of either the same source files with different names or they are from different component repositories. If you use alien this can happen a lot because whoever compiled the code is say SuSE may have given the different libraries the same name as debian or the may have just have same code named in different upper or lower cases. This also happens a lot when you mix sarge, sid, or woody debs in with ubuntu for the same reasons. Yalour best bet to fix it is to remove the broken packages and if you really want to go ahead an install what you're trying to install; delete the library or file that is apt says already has are there. Then install the new packages.

---

### Post by c_dog on 2005-04-17
Sounds like you are trying to load different deb builds of either the same source files with different names or they are from different component repositories. If you use alien this can happen a lot because whoever compiled the code in say SuSE may have given the different libraries the same name as debian or the may have just have same code named in different upper or lower cases. This also happens a lot when you mix sarge, sid, or woody debs in with ubuntu for the same reasons. The best bet to fix this is to remove the broken packages and if you really want to go ahead an install what you're trying to install; delete the library or file that is apt says already has are there. Then install the new packages.

---

### Post by Turin Turambar on 2005-04-17
I deleted the mixer files in /usr/lib, but I still receive the same error message when Synaptic tries to install?!?   :-?

---

### Post by cdhotfire on 2005-04-17
```

$ sudo apt-get remove libsdl-mixer1.2
$ sudo apt-get check

```

download, [http://packages.debian.org/stable/libs/libsdl-mixer1.2](http://packages.debian.org/stable/libs/libsdl-mixer1.2), from there then.

```

$ cd /where/ever/u/put/deb/
$ sudo dpkg -i libsdl-mixer1.2.deb

```

Does this work?

---

### Post by Turin Turambar on 2005-04-17
Thanks for a tip, but unfortunately it didn't help. :(

This package is not, in fact, installed, and that's what *apt-get remove* said too.

I have downloaded the file, tried with dpkg and got the same message!  :-? 

```
root@ubuntu:/home/ivan/My Downloads # dpkg -i libsdl-mixer1.2_1.2.1-5_i386.deb
(Reading database ... 76511 files and directories currently installed.)
Unpacking libsdl-mixer1.2 (from libsdl-mixer1.2_1.2.1-5_i386.deb) ...
dpkg: error processing libsdl-mixer1.2_1.2.1-5_i386.deb (--install):
 trying to overwrite `/usr/lib/libSDL_mixer-1.2.so.0', which is also in package sdl-mixer
Errors were encountered while processing:
 libsdl-mixer1.2_1.2.1-5_i386.deb
```

There's NO other libsdl-mixer file prior to installing this package! It seems to me (and I'm a rookie) that it tries to overwrite itself?!
I noticed that package contains libsdl-mixer file and the symlink named libSDL_mixer-1.2.so.0 (the problematic file). However, only lbsdl-mixer gets installed - not the symlink...

---

### Post by Turin Turambar on 2005-04-17
FINALLY!!

I installed it with dpkg --force-overwrite option! Huh!

---

### Post by cdhotfire on 2005-04-17
[QUOTE=Turin Turambar]FINALLY!!

I installed it with dpkg --force-overwrite option! Huh![/QUOTE]

congrats, this was what i was gonna suggest next.;-)

---

