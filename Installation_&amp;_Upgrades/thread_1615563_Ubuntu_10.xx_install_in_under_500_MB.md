---
title: "Ubuntu 10.xx install in under 500 MB?"
date: 2010-11-07
forum: Installation &amp; Upgrades
---

### Post by mpoon on 2010-11-07
I have a hard drive that is 512 mb.  Is it possible to fit a command-line installation of Ubuntu onto it?  I've tried installing with the alternate image, but Ubuntu turns out to take about 600mb.  Is there some way to get it lower?

Thanks!

---

### Post by sidzen on 2010-11-07
Minimal Install [here]("https://help.ubuntu.com/community/Installation/MinimalCD")

---

### Post by mörgæs on 2010-11-07
And here:
[http://ubuntuforums.org/showthread.php?t=1155961](http://ubuntuforums.org/showthread.php?t=1155961)

Maybe a minimal Lubuntu is the best choice. The applications here are lighter and smaller.

---

### Post by mpoon on 2010-11-07
I've already tried MinimalCD.  The CD itself is quite small, but it requires a massive download of a bunch of packages, which pushes me to about 600mb.  And in that thread you pointed me to, that person is removing stuff _after_ installing, which wouldn't work for me because I need the install to be < 500mb or else the install fails due to lack of disk space.  :(

---

### Post by BbUiDgZ on 2010-11-07
try the [debian](http://www.debian.org) net install or if u have plenty of time try [LFS](http://www.linuxfromscratch.org/)

---

### Post by mörgæs on 2010-11-07
> **mpoon said:**
> And in that thread you pointed me to, that person is removing stuff _after_ installing, which wouldn't work for me because I need the install to be < 500mb or else the install fails due to lack of disk space.  :(

No, he is not. Carry on reading...

Your main problem might be the room for a swap partition. How much memory does the machine have?

---

### Post by mpoon on 2010-11-07
> **mörgæs said:**
> No, he is not. Carry on reading...

Your main problem might be the room for a swap partition. How much memory does the machine have?

I did read through a lot of that thread.  What most people in there are advocating is installing with the minimal CD, and then adding in necessary packages.  My problem is that installing with the minimal CD is already too big!  My total hard drive space is 512 MB, and I'm just not even bothering with a swap partition.  Like I said, a minimal CD installation takes up about 600 MB already, so I need a way of installing Ubuntu where the installation is < 500 MB.

---

### Post by mörgæs on 2010-11-07
It just came to my mind: The computer I bought in 1994 had a hard drive of 340 MB. You should be able to buy a used drive of say, 40 GB for next to nothing.

---

### Post by sidzen on 2010-11-07
[http://ubuntuforums.org/archive/index.php/t-1037271.html]("http://ubuntuforums.org/archive/index.php/t-1037271.html")

The answer appears to be, "No," given your limitations.

---

