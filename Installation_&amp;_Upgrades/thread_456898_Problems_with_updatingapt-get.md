---
title: "Problems with updating/apt-get"
date: 2007-05-28
forum: Installation &amp; Upgrades
---

### Post by woopud on 2007-05-28
I just changed from "regular" Feisty to Ubuntu Studio which all went fine until I got available updates. It gave me the following message:

Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.

So I open up a terminal and do the following:

```
woopud@woopud-desktop:~$ sudo apt-get -f install
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  libmpich1.0c2 lmms galan mx44 cheesetracker gnome-bin rezound kaconnect
  libgtk-canvas1 libsdl-gfx1.2-4 fftw2 spiralsynthmodular libgnome32 gnusound
  ardour-gtk lmms-common gnome-libs-data ecamegapedal om libart2 specimen
  libgnorbagtk0 qmidiroute gdk-imlib1 kluppe libscsynth1 qmidicontrol
  gcc-3.4-base horgand libphat0 ams libsdl-sound1.2 qmidiarp qsampler solfege
  libgnomeui32 libdb3 qarecord sfftw2 libgdk-pixbuf2 freewheeling imlib-base
  ardour-session-exchange gmorgan amsynth liborbit0 gdk-imlib11 libgig3c2
  soundstretch python-ecasound2.2 libgnomesupport0 ecasound libclalsadrv1
  libg2c0 supercollider sweep libsclang1 libfox1.4 soundtracker liblscp
  libgnorba27
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  ardour
The following NEW packages will be installed:
  ardour
0 upgraded, 1 newly installed, 0 to remove and 7 not upgraded.
4 not fully installed or removed.
Need to get 0B/4968kB of archives.
After unpacking 17.2MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 131201 files and directories currently installed.)
Unpacking ardour (from .../ardour_1%3a2.0-0ubuntu2_i386.deb) ...
dpkg: error processing /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb (--unpack):
 trying to overwrite `/usr/share/locale/de_DE/LC_MESSAGES/gtk_ardour.mo', which is also in package ardour-gtk
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 /var/cache/apt/archives/ardour_1%3a2.0-0ubuntu2_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
woopud@woopud-desktop:~$
```

How can I fix this ?

Bert

---

### Post by Jussi Kukkonen on 2007-05-28
The ardour package conflicts with ardour-gtk. If you are sure your sources.list is fine (I suggest double-checking), the reason is probably a broken package... If ardour is not essential to you, you can try removing one or both packages.

---

### Post by woopud on 2007-05-28
How would i go about doing that exactly ?

Bert

---

### Post by Jussi Kukkonen on 2007-05-28
Removing the packages?

***sudo apt-get remove ardour*** should work.

---

### Post by woopud on 2007-05-28
Somehow I got it fixed now, suddenly the 'autoremove" option did work after several tries.  Seems everything is okay now, thanks everybody for the suggestions.

Bert

---

