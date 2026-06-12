---
title: "Package is not configured yet"
date: 2015-03-09
forum: Installation &amp; Upgrades
---

### Post by brian52 on 2015-03-09
I have this problem... Lot of problems, how to solve? (First time I ever touch linux, not as friendly as windows.. took me some hours to figure it what is a terminal lol)

```
root@pbx:~# dpkg --configure -aSetting up cups-daemon (1.7.2-0ubuntu1.5) ...
^Cdpkg: error processing package cups-daemon (--configure):
 subprocess installed post-installation script was interrupted
Setting up udev (204-5ubuntu20.10) ...


start: Job is already running: udev
invoke-rc.d: initscript udev, action "restart" failed.
dpkg: error processing package udev (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of pulseaudio:
 pulseaudio depends on udev (>= 143); however:
  Package udev is not configured yet.


dpkg: error processing package pulseaudio (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups:
 cups depends on cups-daemon (>= 1.7.2-0ubuntu1.5); however:
  Package cups-daemon is not configured yet.


dpkg: error processing package cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-bluetooth:
 pulseaudio-module-bluetooth depends on pulseaudio; however:
  Package pulseaudio is not configured yet.


dpkg: error processing package pulseaudio-module-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of pulseaudio-module-x11:
 pulseaudio-module-x11 depends on pulseaudio; however:
  Package pulseaudio is not configured yet.


dpkg: error processing package pulseaudio-module-x11 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez:
 bluez depends on udev (>= 170-1); however:
  Package udev is not configured yet.


dpkg: error processing package bluez (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-core:
 xserver-xorg-core depends on udev (>= 149); however:
  Package udev is not configured yet.


dpkg: error processing package xserver-xorg-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of systemd-services:
 systemd-services depends on udev (>= 175-0ubuntu23); however:
  Package udev is not configured yet.


dpkg: error processing package systemd-services (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of cups-core-drivers:
 cups-core-drivers depends on cups-daemon (>= 1.7.2-0ubuntu1.5); however:
  Package cups-daemon is not configured yet.


dpkg: error processing package cups-core-drivers (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of indicator-session:
 indicator-session depends on systemd-services; however:
  Package systemd-services is not configured yet.


dpkg: error processing package indicator-session (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg:
 xserver-xorg depends on xserver-xorg-core (>= 2:1.11); however:
  Package xserver-xorg-core is not configured yet.


dpkg: error processing package xserver-xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of libpam-systemd:amd64:
 libpam-systemd:amd64 depends on systemd-services (= 204-5ubuntu20.10); however:
  Package systemd-services is not configured yet.


dpkg: error processing package libpam-systemd:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-alsa:amd64:
 bluez-alsa:amd64 depends on bluez; however:
  Package bluez is not configured yet.


dpkg: error processing package bluez-alsa:amd64 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of gnome-bluetooth:
 gnome-bluetooth depends on bluez (>= 4.36); however:
  Package bluez is not configured yet.
 gnome-bluetooth depends on udev (>= 154); however:
  Package udev is not configured yet.


dpkg: error processing package gnome-bluetooth (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of bluez-cups:
 bluez-cups depends on cups; however:
  Package cups is not configured yet.


dpkg: error processing package bluez-cups (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-intel:
 xserver-xorg-video-intel depends on xorg-video-abi-15; however:
  Package xorg-video-abi-15 is not installed.
  Package xserver-xorg-core which provides xorg-video-abi-15 is not configured yet.
 xserver-xorg-video-intel depends on xserver-xorg-core (>= 2:1.14.99.902); however:
  Package xserver-xorg-core is not configured yet.


dpkg: error processing package xserver-xorg-video-intel (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xorg:
 xorg depends on xserver-xorg (>= 1:7.7+1ubuntu8.1) | xserver-xorg-renamed; however:
  Package xserver-xorg is not configured yet.
  Package xserver-xorg-renamed is not installed.
  Package xserver-xorg which provides xserver-xorg-renamed is not configured yet.


dpkg: error processing package xorg (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xserver-xorg-video-all:
 xserver-xorg-video-all depends on xserver-xorg-video-intel; however:
  Package xserver-xorg-video-intel is not configured yet.


dpkg: error processing package xserver-xorg-video-all (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 cups-daemon
 udev
 pulseaudio
 cups
 pulseaudio-module-bluetooth
 pulseaudio-module-x11
 bluez
 xserver-xorg-core
 systemd-services
 cups-core-drivers
 indicator-session
 xserver-xorg
 libpam-systemd:amd64
 bluez-alsa:amd64
 gnome-bluetooth
 bluez-cups
 xserver-xorg-video-intel
 xorg
 xserver-xorg-video-all

```

---

### Post by dino99 on 2015-03-09
Looks like you have chosen the hard way  ;)  Everything is usually made with gui (but if you prefer the command line, its up to you indeed  :p

a good start is to let us know about which ubuntu/desktop is installed, to get a closer answer(s) of course.

Anyway, let's start with something easy and userfriendly:

-open a terminal (you now know about it) and run:
- sudo apt-get update
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove
- sudo apt-get install synaptic
- gksudo synaptic

you now have the package manager opened, glance at the top bar menu and the left panel options; all you need is there

---

### Post by ajgreeny on 2015-03-09
> **9d9 said:**
> Looks like you have chosen the hard way  ;)  Everything is usually made with gui (but if you prefer the command line, its up to you indeed  :p

a good start is to let us know about which ubuntu/desktop is installed, to get a closer answer(s) of course.

Anyway, let's start with something easy and userfriendly:

-open a terminal (you now know about it) and run:
- sudo apt-get update
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove
- sudo apt-get install synaptic
[COLOR=#ff0000]- sudo synaptic[/COLOR]

you now have the file manager opened, glance at the top bar menu and the left panel options; all you need is there
I think 9d9 meant a package manager, not file manager, but whichever it is, please **do not use "sudo synaptic"**.
Sudo is for command line applications and utilities not for any GUI applications, and although some will work with sudo successfully, its use could potentially lock you out of your user login by changing permissions of files in your /home.

For GUI applications you should always use ```
gksudo synaptic
``` (you will need to install gksu first,) or use command ```
sudo -H synaptic
``` which is much safer as, to put it in simple terms, it opens a terminal as root and then runs synaptic from that.
See [http://ubuntuforums.org/showthread.php?t=2265982](http://ubuntuforums.org/showthread.php?t=2265982) for more information about that in the lower posts of the thread.

---

### Post by grahammechanical on 2015-03-09
I recently launched Synaptic Package Manager from the Dash and I was required to authenticate. In this way Synaptic runs with administrator permissions. The only time I would want to launch Synaptic from the command line is if I did not have a user interface but could still open the terminal and if I wanted to remove or install a specific package in the hopes of fixing things.

@brian52

Please explain why you are running dpkg --configure -a? What were you trying to do that caused a need to configure packages? It might help us to advise you better. If a particular package is causing this problem, then is it one you are trying to install? And have you downloaded it from some web site?

Ubuntu is very friendly but because Ubuntu is a Linux distribution we also have the freedom of using the Linux command line and is something that we need to learn.

---

### Post by brian52 on 2015-03-09
> **9d9 said:**
> Looks like you have chosen the hard way  ;)  Everything is usually made with gui (but if you prefer the command line, its up to you indeed  :p

a good start is to let us know about which ubuntu/desktop is installed, to get a closer answer(s) of course.

Anyway, let's start with something easy and userfriendly:

-open a terminal (you now know about it) and run:
- sudo apt-get update
- sudo apt-get clean
- sudo apt-get autoclean
- sudo apt-get autoremove
- sudo apt-get install synaptic
- gksudo synaptic

you now have the package manager opened, glance at the top bar menu and the left panel options; all you need is there

> **ajgreeny said:**
> I think 9d9 meant a package manager, not file manager, but whichever it is, please **do not use "sudo synaptic"**.
Sudo is for command line applications and utilities not for any GUI applications, and although some will work with sudo successfully, its use could potentially lock you out of your user login by changing permissions of files in your /home.

For GUI applications you should always use ```
gksudo synaptic
``` (you will need to install gksu first,) or use command ```
sudo -H synaptic
``` which is much safer as, to put it in simple terms, it opens a terminal as root and then runs synaptic from that.
See [http://ubuntuforums.org/showthread.php?t=2265982](http://ubuntuforums.org/showthread.php?t=2265982) for more information about that in the lower posts of the thread.

> **grahammechanical said:**
> I recently launched Synaptic Package Manager from the Dash and I was required to authenticate. In this way Synaptic runs with administrator permissions. The only time I would want to launch Synaptic from the command line is if I did not have a user interface but could still open the terminal and if I wanted to remove or install a specific package in the hopes of fixing things.

@brian52

Please explain why you are running dpkg --configure -a? What were you trying to do that caused a need to configure packages? It might help us to advise you better. If a particular package is causing this problem, then is it one you are trying to install? And have you downloaded it from some web site?

Ubuntu is very friendly but because Ubuntu is a Linux distribution we also have the freedom of using the Linux command line and is something that we need to learn.

Thank you all for answering!

I haven't done anything so far, not sure what synaptic does.

Actually, Ubuntu is user friendly, however for me, user friendly has bugged.

I only want one thing after installing ubuntu for desktop x64, and it is to install and use incrediblepbx for a phone system. I installed it 1 month ago..

But then, ubuntu keep bugging me with automatic updates notifications. So I've decided to updates whent he pop up promted. It was supposed to be user friendly UNTIL THE UPDATES stalled and froze and there was no way to cancel it as the cancel buttun is not clickable. So the update will stall and remain like this forever. The only think I can do is to click on "detail" which shows some terminal stuffs, and I press enter so the installation can continue.. I had to press enter lot of times..

I am not sure what is wrong: so I pasted most of my problems here using the words i can find on the terminal.

It wouldn't be a problem if the updates via the pop up interface worked and didn't stall in the middle.

Also, I don't know if this is related, but I can't shut down or restart the computer using the ubuntu "start button" on the top left. It won't shut down or restart, it however brought me to a black screen with a flashing "l" (that flashing thing that tells you where you can write something on a word document for example..) I always need to shut down it by pressing the computer shut down button with my hand.

---

### Post by brian52 on 2015-03-10
anyways this is now a mess. i cant start my linux..  ca only go to some terminal screen with my usb linux distribution[h=1]["udevadm trigger is not permitted while udev is unconfigured."]("http://ubuntuforums.org/showthread.php?t=1567147")[/h]
damn everything i try has to be stalled at udev (setting up udev (204-5ubuntu20.10).. litterally everything, even install sudo pacman (which no idea what it is), or install anything such as [COLOR=#000000]*synaptic [I]fails too because it stalls at *[/I][/COLOR]udev (setting up udev (204-5ubuntu20.10)

---

### Post by brian52 on 2015-03-10
[IMG]http://i58.tinypic.com/9tijoj.jpg[/IMG]

---

