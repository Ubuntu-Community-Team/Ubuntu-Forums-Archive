---
title: "Additional Package Installing issue in ubuntu 9.10"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by tosandip on 2010-03-12
Guys,

I had installed 9.10 Ubuntu on my Dell 1564. I wanted to download & Install additional packages say like tcsh.

When I tried downloading the packages using apt-get.. I got an error massage saying package not found. Any Idea how to get rid of this issue.

I have also checked my etc/apt/sources.list File & it looks all right.

Is there any switch need to turn ON for enabling apt-get?

Regards
San

---

### Post by Enigmapond on 2010-03-12
Make sure you have the proper name of the package.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by slakkie on 2010-03-12
You can use aptitude to search for packages

aptitude search <packagename>
aptitude search ~d<packagedescription>

eg.

aptitude search xserver-xorg-video* will search for packages with that name

aptitude search ~dwebcam will search for packages where the description mentions webcam. 

Hope this helps.

---

### Post by tosandip on 2010-03-12
> **Enigmapond said:**
> Make sure you have the proper name of the package.

[http://packages.ubuntu.com/](http://packages.ubuntu.com/)


Say to Install vim,

I tried
sudo apt-get install vim
vim-full
vim-gnome
tcsh
csh

etc, But every time it came out with saying no package found. So I started believing that something is missing to turn ON apt-get

---

### Post by kathy4scuba on 2010-04-23
It's been a couple of years since I had to install Ubuntu and I was running into similar issues.  What I had forgotten to do was to update the package list on my computer:

sudo apt-get update

Once I did that, then the following worked:

sudo apt-get install tcsh

Hope this helps.  

I'm now also able to get tcsh with the Synaptic Package Manager.

---

