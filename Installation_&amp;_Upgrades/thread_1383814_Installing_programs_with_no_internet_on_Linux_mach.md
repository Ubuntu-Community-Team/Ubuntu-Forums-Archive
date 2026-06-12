---
title: "Installing programs with no internet on Linux machine"
date: 2010-01-17
forum: Installation &amp; Upgrades
---

### Post by B15h on 2010-01-17
Please help me. I’ve successfully set up Ubuntu on a desktop computer I got for free (because it’s RAM was half destroyed by a virus and the owner got a new one). I don’t have this computer connected to the internet but I can get the internet on my laptop’s built in wifi (from some random neighbour who has an unsecure WLAN). So, to install programs on Ubuntu I have to download the .deb or .ter.gz files from the laptop (winXP), copy them to a USB drive, transfer them to the Linux machine and install. Problem is, none have worked so far:
   
  Blender (install from .deb)
       Error: Dependency is not satisfiable
   
   
  Blender (install from .tar.gz)
       I created a new blender folder in /home and extracted there. If I double click the blender.exe file nothing happens. If I go to the terminal and type “blender” it says that the program is not installed.
   
   
  Audacity (from .deb file)
                   Error: Dependency is not satisfiable: audacity.data (=1.3.9-6)
   
   
  libdvdcss2_1.2.9-1 i386.deb (so I can watch DVDs in Totem movie player)
       .deb package installs with no problem. Still cannot watch DVDs. Movie player says: ”Totem player cannot play this type of media (DVD) because it does have the appropriate plugins to be able to read the disk.
   
   
  LMMS (from .deb file)
                   .deb package installs with no error. However, I cannot see the application in any menu, on the desktop or /home folder. If I go to the terminal and type “lmms” it says that it is not installed. If I again try to install from .deb package it says that the program is already installed. I did find a folder /usr/share/lmms but it did not contain any .exe or launcher files.
   
   
  Aldrin (Buzz clone)
                   Same deal as LMMS and libdvdscc2. .deb file installs fine but can’t see it anywhere.
   
  Please tell me there is a simple answer for all of this. I will be getting an DSL connection soon so I’ll be able to use the software centre but I’m worried I’ll still have these problems. Thanks in advance.
   
  B15h

---

### Post by oldos2er on 2010-01-17
Look into either Keryx ([http://keryxproject.org/](http://keryxproject.org/)) or AptonCD ([http://aptoncd.sourceforge.net/](http://aptoncd.sourceforge.net/)) for info on installing packages offline.

You won't find *.exe files in Linux.

---

