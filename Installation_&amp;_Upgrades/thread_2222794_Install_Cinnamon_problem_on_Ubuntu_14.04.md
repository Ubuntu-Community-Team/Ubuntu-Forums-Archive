---
title: "Install Cinnamon problem on Ubuntu 14.04"
date: 2014-05-08
forum: Installation &amp; Upgrades
---

### Post by iftikhar-tutul on 2014-05-08
I tried to install cinnamon on Ubuntu 14.04 LTS. Below this command I used :

$ sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-stable
 
$ sudo apt-get update
 
$ sudo apt-get install cinnamon

But when I login , it shows nothing

---

### Post by John_Philpott on 2014-05-15
Cinnamon isn't yet available on that repo for Trusty. Don't know how you managed to install it ;)
You can install a nightly build of 2.2+ using this:
[COLOR=#000000]sudo add-apt-repository ppa:gwendal-lebihan-dev/cinnamon-nightly
But I wouldn't advise it. Better to wait for it to hit the stable repo.[/COLOR]

---

### Post by kleeman on 2014-05-17
Unfortunately the stable repo says that updates have been discontinued since cinnamon is now in the universe section of Ubuntu. This was true for 13.10 but is not true for 14.04 and there appears no indication when this will be rectified. Very unfortunate and the reason why I am not upgrading to 14.04 until this is fixed.

---

### Post by picpak on 2014-05-17
There's a new stable Cinnamon PPA for 14.04 I found here: [https://launchpad.net/~kranich/+archive/cubuntu](https://launchpad.net/~kranich/+archive/cubuntu)

To install it, just run:

$ sudo add-apt-repository ppa:kranich/cubuntu

$ sudo apt-get update

$ sudo apt-get install cinnamon

---

