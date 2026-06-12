---
title: "Ubuntu Installation Package Newbies"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by superstalker on 2009-12-21
Hi everyone,

Seeing that I've reinstalled Ubuntu a lot, because I fiddled with it so much that eventually the whole system crashes :P. I made a list for Eyecandy and usefull stuff.
[U]
It's advised to install the programs you want with: [/U]
System -> Administration -> Synaptic Package Manager

[U]Videocard:
[/U]System -> Administration -> Hardware Drivers

For the ones who have no sound. It's probably caused by Software Modem in the Hardware Drivers, disable and you have sound again.

**Eye Candy:**

_______________________________________________________________________________

_Compiz Settings Manager_
*Known for the Cube and Wobbly Windows, it let's you edit the way you interact with Ubuntu.*
_______________________________________________________________________________

_Cairo-Dock (GLX)_
*The best eyecandy (mac)dock-bar Ubuntu has to offer. Other choises are AVN, and Gnome DO.*
_______________________________________________________________________________

_drapes_
*Background changer.*
_______________________________________________________________________________

_Screenlets_
*Inserting a clock on your desktop, or a weather notifier, or CPU usage etc.*
_______________________________________________________________________________

**Usefull Stuff:**

_______________________________________________________________________________

_pysdm_
[I]Automount your hard drives / partitions.

When installed, press "Alt + F2"
```
 sudo pysdm 
```Follow instructions and the hard drives will be mounted everytime you log in.
[/I]_______________________________________________________________________________

_Virtualbox_
*OS-Emulator for those programs that only runs on Windows.*
_______________________________________________________________________________

_Ubuntu Tweak_
*Tweak Ubuntu, compact Installation Manager for eycandy and such.*

**[FONT=Verdana][SIZE=4]How to Install[/SIZE][/FONT]**
The package is suitable under Hardy, Intrepid, Jaunty and Karmic.
Visit to this link to download the latest package and source code
 [https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.2](https://launchpad.net/ubuntu-tweak/0.4.x/0.4.9.2)
 Old version of Ubuntu Tweak is available here:
 [http://code.google.com/p/ubuntu-tweak/downloads/list](http://code.google.com/p/ubuntu-tweak/downloads/list)
 [B][B]
How to add the source of Ubuntu Tweak [/B][/B]

 open your terminal ( Applications -> Accesoires -> Terminal ), first import the key:
 ```
sudo apt-key adv --recv-keys --keyserver keyserver.ubuntu.com FE85409EEAB40ECCB65740816AF0E1940624A220
``` type the command to run gedit(or other editor in your opinion) to modify the sources.list:
 ```
sudo gedit /etc/apt/sources.list
``` And put the two line into it(If you are using Ubuntu 8.04 Hardy or early) :
 ```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu hardy main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu hardy main
``` Or Ubuntu 8.10 Intrepid:
 ```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu intrepid main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu intrepid main
``` Or Ubuntu 9.04 Jaunty:
 ```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu jaunty main
``` Or Ubuntu 9.10 Karmic:
 ```
deb http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
deb-src http://ppa.launchpad.net/tualatrix/ppa/ubuntu karmic main
``` Then update the source and install or upgrade Ubuntu Tweak:
 ```
sudo apt-get update
sudo apt-get install ubuntu-tweak
``` if you have installed, just type:```

 sudo apt-get dist-upgrade

```_______________________________________________________________________________

_Ultamatix_
[I]Installation Manager:
- Codecs[/I]
[I]- Google Earth

[/I] **[FONT=Verdana][SIZE=4]How to Install[/SIZE][/FONT]**

Select **System** >> **Administration** >> **Software sources**

 Select Third-party software tab and click the add&#8230; button at the bottom.
 
    Release name - Version - DISTRONAME 
  Ultimate Edition - 2.5 - karmic   
Ultimate Edition - 2.4 - karmic   
Ultimate Edition - 2.3 - jaunty   
Ultimate Edition - 2.2 - jaunty   
Ultimate Edition - 2.1 - intrepid   
Ultimate Edition - 2.0 - intrepid   
Ubuntu - 9.10 - karmic   
Ubuntu - 9.04 - jaunty   
Ubuntu - 8.10 - intrepid   
Ubuntu - 8.04 - hardy   
Ubuntu - 7.10 - gutsy   
Ubuntu - 7.04 - edgy    [B]
INSERT DISTRO TABLE HERE[/B]
 Enter:[INDENT] ```
deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") DISTRONAME all#Ultimate Edition Repository
``` [/INDENT]Replacing **DISTRONAME** with your distro based on the table above.
 For example using Ultimate Edition 2.2 or 2.3 would be:[INDENT] ```
deb [http://repoubuntusoftware.info]("http://repoubuntusoftware.info/") jaunty all#Ultimate Edition Repository
```[/INDENT]_______________________________________________________________________________

_Skype_
*VoIP and Chat*
_______________________________________________________________________________

_xSane_
*Printer scanning utilty.*
_______________________________________________________________________________

_kOrganizer_
*Agenda.*
_______________________________________________________________________________

_aMSN_ - _emesene_ - _Pidgin_
*MSN based chatting programs.*
_______________________________________________________________________________

_Wine 1.2_
*Play Windows Games on Ubuntu*. And install Windows or Mac based programs like iTunes, Microsoft Office etc.


**Tips:**

1. Try to install as much as possible with Synaptic Package Manager. Especially for games, it's the safest way to avoid errors or crashes.

2. Ubuntu Tweak is a great program for the beginning users!

3. Ask YouTube if you don't know how to use a program. There are a huge amounts of video-based tutorials.

4. Feel free to post more usefull programs!

5. Compiz Settings Manager has way more to offer then you think, explore it.

6. Try to limit your Screenlets, as they can slow your pc/mac/laptop/notebook down.

7. OpenOffice is a good replacement for Mircosoft Office, you can expand it using Synaptic Package Manager, also you can download it on the OpenOffice site.


Greetz,
SuperStalker

---

### Post by superstalker on 2009-12-22
Well did some final editing, and used this thread when I reïnstalled Ubuntu. If there any comments, I'd be glad to hear them.

---

