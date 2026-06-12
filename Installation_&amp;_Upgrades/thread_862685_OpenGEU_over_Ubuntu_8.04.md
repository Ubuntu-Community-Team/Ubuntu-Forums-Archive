---
title: "OpenGEU over Ubuntu 8.04"
date: 2008-07-17
forum: Installation &amp; Upgrades
---

### Post by LabRat99 on 2008-07-17
Hi,

I'd like to know if I can install the latest version of OpenGEU over my Kubuntu 8.04 install.

---

### Post by zoe-scutterbug on 2008-07-18
If you install the OpenGEU meta package you will be given the choice of either
enlightenment or Kubuntu sessions at start up...your kubuntu applications will appear in 
your E menus and the vast majority will work well

see this answer here 
by
meindian523 which quickly sums it up
    
Re: Question on Enlightenment

"Linux desktops are composed of two different things:
1]A window manager and
2]A desktop environment
A desktop environment runs on top of the window manager.E is a window manager,GNOME and KDE are desktop environments,which include their file managers(Nautilus and Konqueror,respectively),other applications like the games,accessories,means of accessing the terminal within the desktop(gnome-terminal and konsole,respectively)
So you CAN use E as your Window manager and run GNOME and/or KDE on top of it."
 [http://ubuntuforums.org/showthread.php?t=863023&highlight=enlightenment](http://ubuntuforums.org/showthread.php?t=863023&highlight=enlightenment)
 [http://snipurl.com/30la2](http://snipurl.com/30la2)




hope that helps
zoe

---

### Post by LabRat99 on 2008-07-18
Thanks for the reply but the info I am looking for is:

I have the latest OpenGEU live cd and I have the 8.04 version of Kubuntu already installed as a dual boot with WinXP. I've tried OpenGEU out and really like it a lot.

My question is, what happens if I run the install option from the OpenGEU live cd? Will it install over the Kubuntu that I already have or what?

My goal is to end up with OpenGEU replacing the Kubuntu install and having  a dual boot system with OpenGEU and WinXP.

---

### Post by zoe-scutterbug on 2008-07-18
ahhh...;)

i am pretty clueless at the best of times...i am no expert

if you would like to overwrite your existing kubuntu installation by doing a fresh install
from the live opengeu cd then the answer is yes...

see [http://opengeuwiki-en.intilinux.com/index.php?title=Install_geubuntu_7.10_from_LiveCD](http://opengeuwiki-en.intilinux.com/index.php?title=Install_geubuntu_7.10_from_LiveCD)

or

OpenGEU - A step-by-step install from OpenGEU creator Luca De Marini.

[http://fullcirclemagazine.org/issue-9/](http://fullcirclemagazine.org/issue-9/)

opengeu uses the same kind installation process/setup as your original and it should give you the option to overwrite your kubuntu partition durring installation.

my own personal choice was to have my system so i can choose to enter ubuntu, kubuntu, mythubuntu, crystal, openbox, flux if i want...though i do stay in opengeu 99.5% of the time.

zoe

---

### Post by Skripka on 2008-07-18
Zoe-
Is there any word yet on when OpenGEU will be working for amd64?  I threw in an i386 LiveCD to play with, and am a bit addicted.

When I go through terminal to install opengeu-desktop I get:
The following packages have unmet dependencies:
  opengeu-desktop: Depends: opengeu-luna-nuova-themes but it is not going to be installed
                   Depends: emodule-extramenu-opengeu-data but it is not going to be installed
                   Depends: emodule-bling but it is not installable
                   Depends: geutheme but it is not going to be installed
                   Depends: emodule-calendar but it is not installable
E: Broken packages


Both emodule-bling and emodule-calendar are not in the repos it seems :(

---

### Post by zoe-scutterbug on 2008-07-18
no word to my knowledge..sorry..i think best ask on its forum

zoe

---

### Post by darkmaster on 2008-09-04
> **Skripka said:**
> Zoe-
Is there any word yet on when OpenGEU will be working for amd64?  I threw in an i386 LiveCD to play with, and am a bit addicted.

When I go through terminal to install opengeu-desktop I get:
The following packages have unmet dependencies:
  opengeu-desktop: Depends: opengeu-luna-nuova-themes but it is not going to be installed
                   Depends: emodule-extramenu-opengeu-data but it is not going to be installed
                   Depends: emodule-bling but it is not installable
                   Depends: geutheme but it is not going to be installed
                   Depends: emodule-calendar but it is not installable
E: Broken packages


Both emodule-bling and emodule-calendar are not in the repos it seems :(

Sorry people, I know this is very old, but you know it works on 64 bit system since some time now, do you?

---

