---
title: "Installing with a .tar.gz file"
date: 2012-02-05
forum: Installation &amp; Upgrades
---

### Post by timmc94 on 2012-02-05
I am trying to install a game called *Marble Arena 2* on my Ubuntu laptop. I saw it in the software center but it told me I didn't have the right download sources, so I went to the website for the game and downloaded it through the link for Linux Systems. It gave me a .tar.gz file, which I have installed from before but I cannot figure this one out. Any tips?

---

### Post by lisati on 2012-02-05
There should be installation instructions on the website.

If you open up the file in Nautilus, there may be a "readme" file with installation instructions.

---

### Post by sanderj on 2012-02-06
> **timmc94 said:**
> I am trying to install a game called *Marble Arena 2* on my Ubuntu laptop. I saw it in the software center but it told me I didn't have the right download sources, so I went to the website for the game and downloaded it through the link for Linux Systems. It gave me a .tar.gz file, which I have installed from before but I cannot figure this one out. Any tips?

Normally it is preferred to install from packages, as that will take care automatically of dependencies and updates. However, I couldn't find a package for "marble arena".

So I download the tar.gz file. I unpacked it by openening it and clicking on "Extract". I then opened a terminal, and went into the main directory of Marble Arena (containing the directories "bin", "data", and "packages"). From there I started the game by typing "bin/arena_64", which gave an error "error while loading shared libraries: libSDL_mixer-1.2.so.0: cannot open shared object file: No such file or directory"

Some googling revealed that I had to install a library:

sudo apt-get install libsdl-mixer1.2

After that I could start the game:

bin/arena_64 

HTH

---

### Post by sanderj on 2012-02-06
Oh, do you have Ubuntu 11.10 Oneiric? If so, there seems to be a package available:

[https://apps.staging.ubuntu.com/cat/applications/oneiric/marblearena2/](https://apps.staging.ubuntu.com/cat/applications/oneiric/marblearena2/)

Installing a package is much easier than using .tar.gz files.

---

