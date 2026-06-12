---
title: "Problem compiling head tracking plugin for compiz."
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by Durkheim on 2010-07-21
Hi,

I'm trying to compile the plugin for compiz that allows head tracking. I'm using Ubuntu 10.04 "Lucid".

I tried with the source code from [here]("http://gitweb.compiz-fusion.org/?p=users/klange/headtracking;a=snapshot;h=e79ef4df3292b5c98bc0673ea79577eb7b2cf5c7;sf=tgz") or from git using
```
git clone git://git.compiz-fusion.org/users/klange/headtracking

```

In both cases compilation works fine, but when it tries to link the following happens:

```
~/headtracking/headtracking$ sudo make
convert   : headtracking.xml.in -> build/headtracking.xml
bcop'ing  : build/headtracking.xml -> build/headtracking_options.h
bcop'ing  : build/headtracking.xml -> build/headtracking_options.c
schema    : build/headtracking.xml -> build/compiz-headtracking.schema
compiling : facedetect.c -> build/facedetect.lo
compiling : headtracking.c -> build/headtracking.lo
compiling : build/headtracking_options.c -> build/headtracking_options.lo
linking   : build/libheadtracking.la/usr/bin/ld: cannot find -lcvaux
collect2: ld returned 1 exit status
make: *** [build/libheadtracking.la] Erreur 1

```

I searched the interwebs for an answer but can't figure out  why -lcvaux option is missing from the linker...

Any help will be much appreciated.

Thanks,
David

---

### Post by Durkheim on 2010-07-22
up.

---

### Post by realzippy on 2010-07-22
No idea,but,it means it cannot find an external library.
Run

```
sudo apt-get install libcv1 libcvaux1 libcv-dev libcvaux-dev
```

and try again...

---

### Post by realzippy on 2010-07-22
Ignore my former post.
Have you compiled latest **opencv** from svn?
Otherwise headtracking will not compile...
I just installed/compiled headtracking (your version)after compiling opencv as shown in this guide:

[http://opencv.willowgarage.com/wiki/InstallGuide_Linux](http://opencv.willowgarage.com/wiki/InstallGuide_Linux)

I chose the *latest tested OpenCV snapshot*;**do not forget** the
**path configuration** after compiling !!!

To compile *headtracking* after you done this,you need  to install

compiz-fusion-bcop compiz-dev **libtool**

Let me know when running into problems...

---

### Post by Durkheim on 2010-07-22
Hi, 

Thank you very much for your help!
I followed your steps carefully and voila, the plugin is compiled and installed :)
My camera doesn't lit up and nothing moves on screen, but that is another story.

Thanks again!

---

### Post by realzippy on 2010-07-22
Fine so far.
Please set thread as solved (threadtools),and open a new one
with that camera issue,assuming your camera works generally.
Remember some thread about *headtracking* and *not reacting* camera...good luck!

---

