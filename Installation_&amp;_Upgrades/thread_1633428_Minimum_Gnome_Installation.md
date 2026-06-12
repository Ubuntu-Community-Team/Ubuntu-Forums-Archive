---
title: "Minimum Gnome Installation"
date: 2010-11-29
forum: Installation &amp; Upgrades
---

### Post by peter1608 on 2010-11-29
I am trying to achieve a bespoke installation of Ubuntu 10.04.  This is so I can add the specific packages I want and then create a live CD of the resulting system.  So far I can report a partial success, and hope that with a bit of guidance I can get the rest of the way.

My first attempts started with a full install, then deleting all the packages I did not want.  These all failed, either because I was too enthusiastic and deleted critical components, or because I ended up with an iso image that was too big to fit on a CD.  Therere seemed to be a high level of interdependence, with the Software Centre insisting that to delete certain packages I did not want I also had to delete the ubuntu desktop! 

Next I tried a minimal install ([https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)), and set about adding what I wanted.  As the minimum does not include a GUI, I tried adding gnome, and discovered that I was back with the full installation!  Tried again, this time with extensive googling to fathom out what was required. I used the following commands (I know that you can do multiple installs on one line, but I wanted to keep each step as simple as possible):-

sudo aptitude update
sudo aptitude install x-window-system-core
sudo aptitude install gnome-core
sudo aptitude install gdm
sudo aptitude install firefox
sudo aptitude install synaptic
sudo aptitude install xubuntu-system-tools - this failed, presumably it's not available under 10.04. but is there an equivalent?
sudo aptitude install gnome-app-install

I have a working system, to which I have added some packages that I want, such as python imaging and gnumeric.  But it looks decidedly odd.  The iso is about 450Mb, so I can afford to add some more decoration and yet keep it on one CD.

So my question is: How do I achieve a minimal installation, with a standard gnome 'look and feel', but only the bare minimum of packages included, along with the ability to install others from a repository?

It does seem a remarkable omission that there is no option to select packages at install time - or have I missed something?
Thanks for any help.

Peter

---

### Post by mikewhatever on 2010-11-29
I think the remarkable omission is intentional, to streamline and simplify the installation process. To just improve the appearance, install gnome-themes, gnome-themes-extras and gnome-backgrounds.
In case you want an Ubuntu-like look, go for ubuntu-artwork instead.

---

### Post by peter1608 on 2010-11-30
Thanks for this. I tried your suggestions last night.  To see the effect of each one I installed them separately and rebooted each time.  The first two (gnome-themes, gnome-themes-extras)had no apparent effect, but the third (gnome-backgrounds) did present me with the familiar desktop.  I did not try ubuntu-artwork, as I was satisfied with it as it was

Not sure of its effect on the iso size, as I want to make some further changes to the installed packages, so haven't remastered it yet. But the initial problem is solved.

Peter

---

