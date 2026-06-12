---
title: "Whats required to build new modules for new drivers?"
date: 2007-10-03
forum: Installation &amp; Upgrades
---

### Post by ubunutucyclotron on 2007-10-03
Hello all.

I have downloaded some new drivers that require me to "make" them.

When typing the command in the subdir that contains the drivers I get this:

make
make -C /lib/modules/2.6.15-29-386/build SUBDIRS=/home/cyclotron/Desktop/Drivers/ibdriver-1.3.2-linux-2.6.20 modules
make: *** /lib/modules/2.6.15-29-386/build: No such file or directory.  Stop.
make: *** [default] Error 2

Checking /lib/modules/2.6.15-29-386 I see indeed I do not have a build directory. What do I have to install to get one and be able to build these drivers?

Incidentally in my /lib/modules there are two dirs for older versions of the kernal. Can I delete them?

Thanks in advance,
Daryl

---

### Post by renzokuken on 2007-10-03
run ```
sudo apt-get install build-essential
``` and try again

build-essential contains everything you need to build from source

---

### Post by ubunutucyclotron on 2007-10-03
Ok done. 

Still doing the exact same thing though! Error message etc exactly as posted above.
Still no build directory to be found in /lib/modules/2.6.15-29-386/

?

Daryl

---

