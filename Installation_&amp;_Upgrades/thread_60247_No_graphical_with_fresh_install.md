---
title: "No graphical with fresh install"
date: 2005-08-27
forum: Installation &amp; Upgrades
---

### Post by 1inxs on 2005-08-27
In early 2004 I completed an install using Gentoo. This was after trying Redhat and Suse. I gave Linux an 18 month break due to the lack of hardware supported by Linux at that time. Wanted to see if things have improved. I like Gnome, which is what led me to ubuntu. I've tried the live cd, as well as the install cd. When the system reboots, I only get a console, no graphical desktop. My video card is an ATI X700 PCI express. The MOBO is Asus A8NE-FM w/AMD64 3000+. I'm hoping to use my previous posts on Gentoo.org and new posts here, to get a full system functioning. Thanks in advance for your help.

---

### Post by amohanty on 2005-08-27
Does startx at the CLI work?

if it does thhen look at what is the default runlevel, I think its in inittab, dont have access to my box right now, but look for it and make sure that the default runlevel is 5 which is multiuser, networked, gui login.

HTH
AM

---

### Post by 1inxs on 2005-08-27
This is what I get
robert@ubuntu:~$ startx
xauth: creating new authority file /home/robert/.Xauthority
xauth: creating new authority file /home/robert/.Xauthority
xinit: No such file or directory (error 2):  no server "X" in Path
Use the -- option, or make sure that /us/X11R6/bin is in your path and that "X" is a program or a link to the right type of server for your display. Possible server names include:
Xorg      X.org displays

giving up.
xinit: Connection refused (error 111): unable to connect to X server
xinit: No such process (eror 3): Server error.

When I did the fresh install, I got some of the following. Most of this flashed by quickly, so I can't spell it out exactly. Things like bad problem, agh failed and a few others. I then got an error screen warning me of pkg errors. I click ok and I think it sent me to apt. I exit without changes and come to a black and blue screen with the following

---Upgradable Packages
---New Packages
---Not Installed Packages
---Virtual Packages
---Tasks

This was all prior to startx. Please let me know where to go from here.

---

### Post by 1inxs on 2005-08-27
My last post did not show?

---

### Post by 1inxs on 2005-08-27
[QUOTE=1inxs]This is what I get
robert@ubuntu:~$ startx
xauth: creating new authority file /home/robert/.Xauthority
xauth: creating new authority file /home/robert/.Xauthority
xinit: No such file or directory (error 2):  no server "X" in Path
Use the -- option, or make sure that /us/X11R6/bin is in your path and that "X" is a program or a link to the right type of server for your display. Possible server names include:
Xorg      X.org displays

giving up.
xinit: Connection refused (error 111): unable to connect to X server
xinit: No such process (eror 3): Server error.

When I did the fresh install, I got some of the following. Most of this flashed by quickly, so I can't spell it out exactly. Things like bad problem, agh failed and a few others. I then got an error screen warning me of pkg errors. I click ok and I think it sent me to apt. I exit without changes and come to a black and blue screen with the following

---Upgradable Packages
---New Packages
---Not Installed Packages
---Virtual Packages
---Tasks

This was all prior to startx. Please let me know where to go from here.[/QUOTE]
 My last post did not show?

---

### Post by amohanty on 2005-08-27
If at the terminal you type:

type X

what does it return?

Theres a possibility that you did not install xorg packages. To install those I think you would need to do the following on the terminal at the very least:

apt-get install xorg-xserver
apt-get install xorg-common

HTH
AM

PS: by any chance did you do a server install? That does not install the UI. To install gnome at the terminal type:

apt-get install ubuntu-desktop

---

### Post by 1inxs on 2005-08-28
This is what I get when I
type x
bash: type: x: not found

Next I do

apt-get install xorg-server
Reading package lists... Done
Building dependency tree... Done
E: Couldn't find package xorg-xserver

When I do

apt-get install xorg-common
The following packages have unmet dependencies
foomatic-filters-ppds: Depends: foomatic-db-engine but it is not going to be installed
mozilla-firefox: Depends fontconfig but it is not going to be installed
ubuntu-desktop: Depends: file-roller but it is not going to be installed
                         Depends: foomatic-db-engine but it is not going to be installed
                        Depends: foomatic-db-hpijs but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

 ](*,)

---

### Post by brightanvil on 2005-08-28
Hi, checkout this post ["Stuck After Install"](http://ubuntuforums.org/showthread.php?t=59695) .

And follow the instruction to change the display driver to vesa from this post ["Error on startup"](http://www.ubuntuforums.org/showpost.php?p=238105&postcount=20).

It should solve your problems.

Cheers.

---

### Post by 1inxs on 2005-08-30
Still not up and running. I did

sudo nano -w /etc/X11/XF86Config

and it appears empty. My burner is a Plextor 716A 16x dual layer burner. When I burn a disk should I slow down the burn speed? I also tried the DVDs I received from ubuntu with no success. When using this burner was also unable to get an operable Fedora Core system. Maybe a disk check? Sorry, I,m kind of rambling. I'm just hoping to test drive a good linux with Gnome GUI. I'm not a fan of K this and K that that comes in Kde package.

---

### Post by amohanty on 2005-08-30
I would suggest that you burn a new cd from a different source machine, verify the cd write and then try to install.

AM

---

### Post by 1inxs on 2005-09-07
I did a media check and the dvd passed. It just won't load in graphical mode. I still have not seen ubuntu up and running. I may have to wait for an update.

---

### Post by 1inxs on 2005-09-29
Is that it? No one can help?

---

