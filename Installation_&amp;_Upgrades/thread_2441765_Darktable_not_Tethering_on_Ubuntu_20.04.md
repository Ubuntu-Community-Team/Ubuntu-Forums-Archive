---
title: "Darktable not Tethering on Ubuntu 20.04"
date: 2020-04-26
forum: Installation &amp; Upgrades
---

### Post by twayneyoung on 2020-04-26
I just installed Ubuntu 20.04.  After installing Darktable from the Ubuntu Software Store, my Canon 5D Mark II would no longer allow tethering.  I was not given the option, nor was there a Scan for Devices button.  It worked fine, no problems, on Ubuntu 19.10.

SO, I uninstalled Darktable, and then re-installed using the command line in a terminal window:  sudo apt-get install darktable

Following that, it worked fine, and automatically detected my camera.  

I believe there is a discrepancy between the command line installed software and that being offered on the Ubuntu Store.  This should be checked out.

---

### Post by CelticWarrior on 2020-04-26
welcome.

Here are a few need to know things:

Tethering is sharing an internet connection from a mobile device. Accessing files from a camera, wired or wireless is NOT tethering.
The default installation for many apps now is as snaps and snaps require permissions (there's a button for that in the store right after the installation is finished) for accessing storage devices.

The version you ended up with is older than the one available as snap.

In a nutshell, it's not a matter of discrepancy.

---

