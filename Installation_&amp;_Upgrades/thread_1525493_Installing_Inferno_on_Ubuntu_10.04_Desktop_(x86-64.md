---
title: "Installing Inferno on Ubuntu 10.04 Desktop (x86-64)"
date: 2010-07-06
forum: Installation &amp; Upgrades
---

### Post by fetuspuppet on 2010-07-06
From the guide on Inferno's site:

> On Linux systems with a Debian base, such as Ubuntu, to compile the  graphical version of the system     you will need the Debian packages *libxext-dev, libxpm-dev, and  x11proto-xext-dev* installed
```
sudo apt-get install libxext-dev libxpm-dev x11proto-xext-dev
```Grab the inferno source, make sure you have all the build utils installed as well.

edit the file after untaring inferno called mkconfig and change the flags to match your Ubuntu system - 386 or Power etc... More details are on the Inferno site for this.

[http://www.xs4all.nl/~mechiel/inferno/getting-started.html#compiling]("http://www.xs4all.nl/%7Emechiel/inferno/getting-started.html#compiling")

More to come...

---

