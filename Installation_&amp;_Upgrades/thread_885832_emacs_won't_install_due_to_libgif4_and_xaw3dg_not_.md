---
title: "emacs won't install due to libgif4 and xaw3dg not installable"
date: 2008-08-10
forum: Installation &amp; Upgrades
---

### Post by KaiserSuSE on 2008-08-10
Hello gang. Just downloaded Ubuntu 8.04.1 Desktop and installed today on an old HP Pavilion 780n. Dual boot with Windows. Very nice!

My immediate problem is that I can't get my beloved emacs editor to install.

Synaptic Package Manager won't cooperate, and when I try

sudo apt-get install emacs22

I get:

The following packages have unmet dependencies:
  emacs22: Depends: emacs22-bin-common (= 22.1-0ubuntu10.1) but it is not going to be installed
           Depends: libgif4 (>= 4.1.6) but it is not installable
           Depends: xaw3dg (>= 1.5+E-1) but it is not installable
E: Broken packages

I've read posts on the forums suggesting that what's wanted with ubuntu is emacs22-gtk, but that's not even offered by Synaptic Package Manager.

There is a [download page]("http://packages.ubuntu.com/hardy/i386/emacs22-gtk/download") for emacs22-gtk on the ubuntu site, but I didn't want to fool with that, given that it warns I should be using the package mgr.

I'm hoping a fellow emacs aficionado, or ubuntu guru, can help me out here.

Thanks in advance.

[COLOR="Sienna"]KaiserSuSE[/COLOR]

---

### Post by KaiserSuSE on 2008-08-20
I had to go to the Ubuntu download site and install all of the required packages by hand. These are the packages I downloaded and installed:

liblockfile1_1.06.2_i386.deb
libgif4_4.1.6-4_i386.deb
emacsen-common_1.4.17_all.deb
emacs22-gtk_22.1-0ubuntu10.1_i386.deb
emacs22-bin-common_22.1-0ubuntu10.1_i386.deb

Once I did that, I was able to run emacs 22.1 GTK+ version.

[COLOR="Sienna"]KaiserSuSE[/COLOR]

---

### Post by Torben Putkonen on 2008-09-29
> **KaiserSuSE said:**
> I had to go to the Ubuntu download site and install all of the required packages by hand. These are the packages I downloaded and installed:


This resolution is unacceptable. What is the correct way to install Emacs on Hardy?


Edit: Correct resolution is to not use the quick and powerful "Synaptic Package Manager." Instead, use the dumbed down and slow "gnome-app-install" program through the "Add/Remove..." menu item. Gnome-app-install detects that the package list on local computer is outdated and updates it. After the package list is updated, emacs can be installed quite easily.

---

