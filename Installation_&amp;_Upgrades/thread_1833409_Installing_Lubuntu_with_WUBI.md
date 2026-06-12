---
title: "Installing Lubuntu with WUBI"
date: 2011-08-26
forum: Installation &amp; Upgrades
---

### Post by Orcris on 2011-08-26
Is it possible to install Lubuntu with WUBI? I have a low end netbook, so I want a lightweight system that still has all the eyecandy I like. I don't have a free flash drive to burn it to, so the only other solution is WUBI. Is it possible to force WUBI to install Lubuntu?

---

### Post by bcbc on 2011-08-26
No, you can't install lubuntu with wubi. 

And I haven't heard of a plan to include it in Oneiric either (lubuntu becomes an official version of Ubuntu in the upcoming release).

---

### Post by Orcris on 2011-08-26
Well, is there any way to install Lubuntu from Windows without a CD or flash drive?

---

### Post by bcbc on 2011-08-26
No, not that I know of. (apart from a virtual machine, but that's obviously not what you want).

Install Ubuntu using Wubi, then after it's booted do [this]("https://wiki.ubuntu.com/Lubuntu/DocumentationHelp#Install_Lubuntu_from_Ubuntu_or_any_Ubuntu_flavors"):

> Install Lubuntu from Ubuntu or any Ubuntu flavors

You can install on any installed version of Ubuntu by adding the lubuntu ppa and then installing lubuntu:

sudo add-apt-repository ppa:lubuntu-desktop/ppa
sudo apt-get update
sudo apt-get install --no-install-recommends lubuntu-desktop
If you wish to get rid of an existing k/x/ed/ubuntu then head over to [Pure LXDE]("http://psychocats.net/ubuntu/purelxde"). alter the very end from

&& sudo apt-get install lubuntu-desktop
To

&& sudo apt-get install --no-install-recommends lubuntu-desktop
[QUOTE][/QUOTE]

---

