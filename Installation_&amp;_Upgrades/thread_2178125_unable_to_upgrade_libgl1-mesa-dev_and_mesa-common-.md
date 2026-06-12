---
title: "unable to upgrade libgl1-mesa-dev and mesa-common-dev"
date: 2013-10-02
forum: Installation &amp; Upgrades
---

### Post by vivek3 on 2013-10-02
[COLOR=#ff0000]&#8203;[/COLOR]when I try to update ubuntu 12.04 via update manger I offered to install partial-upgrade so i tried to install via synaptic package manger but that doesn't help either so I trie it with aptitude and update ubuntu but when this two packages are still not updating.

---

### Post by Bucky Ball on 2013-10-02
Welcome. In a terminal, one after the other with return after each:

```
sudo apt-get update
sudo apt-get upgrade
```

That should do it. Let us know.

You omit two important pieces of information. What packages aren't upgrading? What error, if any, are you getting?

---

### Post by vivek3 on 2013-10-02
I tried both but still no effect.
I have attached some scr-shots that is showing my problem..
 [IMG]https://files.one.ubuntu.com/qcMaoJ-IR3urc_udyvwwtA[/IMG][IMG]https://files.one.ubuntu.com/A--yyOYyTMyGl6iuaQ8zow[/IMG]

---

### Post by Bucky Ball on 2013-10-02
Don't see any attached screenshots ...

Edit>Go Advanced>Paperclip icon>Attach pic. ;)

---

### Post by vivek3 on 2013-10-03
oops !! sorry here they are :) ....
[ATTACH=CONFIG]246693[/ATTACH]

[ATTACH=CONFIG]246694[/ATTACH]

[ATTACH=CONFIG]246695[/ATTACH]

---

### Post by Bucky Ball on 2013-10-03
Extremely peculiar these:

```
sudo apt-get update
sudo apt-get upgrade
```

... didn't fix that issue. Could you run them again, one at a time and report ANY error message or a message of any kind. Both these commands should take you back to a prompt. Look for a message above the prompt if/when it does. 

Could you also give the output of this command, please:

```
uname -r
```

---

### Post by vivek3 on 2013-10-03
here is the output for above commands ...
I dont know how to post terminal output so I posted text files..
[ATTACH]246696[/ATTACH]
[ATTACH]246697[/ATTACH]
[ATTACH]246698[/ATTACH]

---

### Post by Bucky Ball on 2013-10-03
Try this:

```
sudo apt-get autoremove
```

Then the two commands again. Any difference? Have you manually installed any PPAs (third-party repos that didn't come default with the install)?

---

### Post by vivek3 on 2013-10-05
yeah I tried that but still those two packages arn't upgrading...
and yeah I installed bumblebee PPA because I was having GPU problem so is this causing problem or what ?

---

### Post by Bucky Ball on 2013-10-05
Do you have ubuntu-restricted-extras installed?

---

### Post by vivek3 on 2013-10-05
ya i installed them ...

---

### Post by deadflowr on 2013-10-05
You can type
```
sudo apt-get dist-upgrade
```
in a terminal, but don't select y(yes).

Instead look for the line saying something about the following packages will be removed.

Post what they are.

Chances are the new packages will be replacing older packages, which normally simply overrides(writes) them.
But sometimes the newer package needs the older packages to be removed.

The dist-upgrade command is essentially the same output you would get if you ran a partial upgrade.

In fact you can select the partial upgrade option in the update manager, let it start and when it get to the screen with the entries for
Remove, Newly Install, Upgrade(they will each have dropdown arrows next to them, so you can expand the lists).
at the bottom of that window will have the install(OK) button and a cancel.
Selecting cancel will quit the upgrade process from actually ever starting.

---

### Post by vivek3 on 2013-10-05
anarchy@Anarchy:~$ sudo apt-get dist-upgrade
[sudo] password for anarchy: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be REMOVED:
  libgl1-mesa-dri-lts-quantal libgl1-mesa-glx-lts-quantal
  libglapi-mesa-lts-quantal libxatracker1-lts-quantal ubuntu-desktop
  x11-xserver-utils-lts-quantal xorg xserver-common-lts-quantal
  xserver-xorg-core-lts-quantal xserver-xorg-input-all-lts-quantal
  xserver-xorg-input-evdev-lts-quantal xserver-xorg-input-mouse-lts-quantal
  xserver-xorg-input-synaptics-lts-quantal
  xserver-xorg-input-vmmouse-lts-quantal xserver-xorg-input-wacom-lts-quantal
  xserver-xorg-lts-quantal xserver-xorg-video-all-lts-quantal
  xserver-xorg-video-ati-lts-quantal xserver-xorg-video-cirrus-lts-quantal
  xserver-xorg-video-fbdev-lts-quantal xserver-xorg-video-intel-lts-quantal
  xserver-xorg-video-mach64-lts-quantal xserver-xorg-video-mga-lts-quantal
  xserver-xorg-video-modesetting-lts-quantal
  xserver-xorg-video-neomagic-lts-quantal
  xserver-xorg-video-nouveau-lts-quantal
  xserver-xorg-video-openchrome-lts-quantal
  xserver-xorg-video-r128-lts-quantal xserver-xorg-video-radeon-lts-quantal
  xserver-xorg-video-s3-lts-quantal xserver-xorg-video-savage-lts-quantal
  xserver-xorg-video-siliconmotion-lts-quantal
  xserver-xorg-video-sis-lts-quantal xserver-xorg-video-sisusb-lts-quantal
  xserver-xorg-video-tdfx-lts-quantal xserver-xorg-video-trident-lts-quantal
  xserver-xorg-video-vesa-lts-quantal xserver-xorg-video-vmware-lts-quantal
The following NEW packages will be installed:
  libgl1-mesa-glx libglapi-mesa libtxc-dxtn-s2tc0 libx11-xcb-dev
  libxcb-glx0-dev libxdamage-dev libxfixes-dev libxxf86vm-dev
  x11proto-damage-dev x11proto-dri2-dev x11proto-fixes-dev x11proto-gl-dev
  x11proto-xf86vidmode-dev xserver-xorg xserver-xorg-core
  xserver-xorg-input-evdev
The following packages will be upgraded:
  apport apport-gtk gnome-settings-daemon ifupdown libgl1-mesa-dev
  libldap-2.4-2 libpulse-mainloop-glib0 libpulse0 libpulsedsp mesa-common-dev
  pulseaudio pulseaudio-module-bluetooth pulseaudio-module-gconf
  pulseaudio-module-x11 pulseaudio-utils python-apport python-problem-report
17 upgraded, 16 newly installed, 38 to remove and 0 not upgraded.
Need to get 4,836 kB of archives.
After this operation, 18.5 MB disk space will be freed.
Do you want to continue [Y/n]?

---

### Post by vivek3 on 2013-10-06
I got output like this now what should I do ???? upgrade or not ?????

---

### Post by vivek3 on 2013-10-07
Hey Thanx !!!!
I did the dist-upgrade...
 Now I am not able to update those packages and partial upgrade message is also gone !!!!!!

---

