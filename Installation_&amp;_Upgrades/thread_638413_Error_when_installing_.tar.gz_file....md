---
title: "Error when installing .tar.gz file..."
date: 2007-12-12
forum: Installation &amp; Upgrades
---

### Post by XtremeBlaze on 2007-12-12
I have only recently learned how to actually install .tar.gz files, so I may be doing something wrong, although I doupt it....

I wish to install "Frets on Fire", a freeware game from SourceForge;
[http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)

When I do attempt to install the game (using the checkinstaller method) this is the result of the terminal;

```
USER@USER-linux:~$ cd FretsOnFire
USER@USER-linux:~/FretsOnFire$ sudo checkinstall
[sudo] password for USER:

checkinstall 1.6.1, Copyright 2002 Felipe Eduardo Sanchez Diaz Duran
           This software is released under the GNU GPL.

The checkinstallrc file was not found at:
/usr/local/lib/checkinstall/checkinstallrc

Assuming default values.

The package documentation directory ./doc-pak does not exist. 
Should I create a default set of package docs?  [y]: y

Preparing package documentation...OK

*** No known documentation files were found. The new package 
*** won't include a documentation directory.

Please choose the packaging method you want to use.
Slackware [S], RPM [R] or Debian [D]? d


Please write a description for the package.
End your description with an empty line or EOF.
>> FretsOnFire is a guitar Game for Computer
>> 

*****************************************
**** Debian package creation selected ***
*****************************************

*** Warning: The package name "FretsOnFire" contains upper case
*** Warning: letters. dpkg might not like that so I changed
*** Warning: them to lower case.

This package will be built according to these values: 

0 -  Maintainer: [ root@davids-linux ]
1 -  Summary: [ FretsOnFire is a guitar Game for Computer EOF ]
2 -  Name:    [ fretsonfire ]
3 -  Version: [ 20071212 ]
4 -  Release: [ 1 ]
5 -  License: [ GPL ]
6 -  Group:   [ checkinstall ]
7 -  Architecture: [ i386 ]
8 -  Source location: [ FretsOnFire ]
9 -  Alternate source location: [  ]
10 - Requires: [  ]

Enter a number to change any of them or press ENTER to continue: 

Installing with make install...

========================= Installation results ===========================
make: *** No rule to make target `install'.  Stop.

****  Installation failed. Aborting package creation.

Cleaning up...OK

Bye.

USER@USER-linux:~/FretsOnFire$ 
```

Can anyone please help me fix this problem...?

Thanks in advance :)

**EDIT - I put this in the wrong section, can someone move it please, sorry :( **

---

### Post by ardchoille42 on 2007-12-12
> **XtremeBlaze said:**
> I have only recently learned how to actually install .tar.gz files, so I may be doing something wrong, although I doupt it....

I wish to install "Frets on Fire", a freeware game from SourceForge;
[http://fretsonfire.sourceforge.net/](http://fretsonfire.sourceforge.net/)

...

If you're running Gutsy:

```
sudo apt-get install fretsonfire
```

No need to install from source, it's in the universe repo. Always check the repos before installing from source:

```
apt-cache search appname
```

---

### Post by rsambuca on 2007-12-12
As an alternative you can also use the Synaptic Package Manager to install it.  System -> Administration -> Synaptic Package Manager.  Search for your package and click "Apply".

---

### Post by XtremeBlaze on 2007-12-12
Ok, I have tried both options and 2 problems;

1. The computer that has Ubuntu on it has no internet connection
2. The main error I get says " **No rule to make target 'install' " when I try multiple methods of installing the file....

The .tar.gz file is sitting there, and i did extract it :( but i can't understand why it's not working....

Any help is again much appreciated :)

---

### Post by Partyboi2 on 2007-12-12
I suggest installing it as shown in this post
[http://ubuntuforums.org/showthread.php?p=3924451](http://ubuntuforums.org/showthread.php?p=3924451)

The extra packages you can find here (libsdl-mixer1.2 and libsdl-ttf2.0-0)
[http://packages.ubuntu.com/](http://packages.ubuntu.com/)

---

### Post by XtremeBlaze on 2007-12-12
OK, I've treid that method of installing and it still doesn't work, but I know what the problem is now. The tarball is missing the "Make" file. Is there a way for me to make one, or is there a repository of them somewhere for Applications?

---

### Post by Pumalite on 2007-12-12
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)
[http://www.psychocats.net/ubuntu/installingsoftware](http://www.psychocats.net/ubuntu/installingsoftware)

---

### Post by XtremeBlaze on 2007-12-12
I have tried this and when I type into the terminal "./configure" it says theres no such command. And when I input "make" or "make install" it says " **No rule to make target 'install' " :(

Is there an application or tool that I need to be able to create this "Make" file?

---

### Post by logos34 on 2007-12-12
look inside the folder for a README or INSTALL file for info

---

### Post by XtremeBlaze on 2007-12-12
There is no INSTALL file, and there is a README file, but it just tells you information about ingame play etc, not how to install the game...

---

### Post by logos34 on 2007-12-12
so you tried the guide in the thread partyboi2 posted above:

(post #15:
>  Before Installation

Make sure that the driver to your 3D graphic card is proper installed and working.
Check if your sourcelist is fully enabled (universe, multiverse and mediabuntu).

Next step is to download the right libs to make Frets On Fire work. To the terminal;

Code:

sudo aptitude update && sudo aptitude upgrade
sudo aptitude install libsdl-mixer1.2 libsdl-ttf2.0-0

Done.
Installation

Download Frets On Fire Full linux version to your Desktop;

Download

To the terminal;

Code:

cd ~/Desktop
mkdir ~/.Games
tar zxfv FretsOnFire-1.2.451-linux.tar.gz -C ~/.Games

Done.
Launcher

Next thing is to make a launcher for Frets On Fire;

Code:

cd ~/Desktop
nano ~/.Games/FretsOnFire/Launch-FretsOnFire.sh

Add the following;

#!/bin/bash

cd ~/.Games/FretsOnFire
sh FretsOnFire

Save (ctrl)+(o) and Save (ctrl)+(x)

Code:

chmod +x ~/.Games/FretsOnFire/Launch-FretsOnFire.sh
alacarte

Go to Games and make a new entry;

Name: Frets On Fire
Command: sh /home/USERNAME/.Games/FretsOnFire/Launch-FretsOnFire.sh
Comment: Frets on Fire is a game of musical skill and fast fingers. The aim of the game is to play guitar with the keyboard as accurately as possible.

Icon: ~/.Games/FretsOnFire/data/icon.png

Enjoy! ^_^

You just untar it and run the executable with 'sh... (unless I've missed something--I'm downloading it now to have a look inside)

---

### Post by logos34 on 2007-12-12
ok, all I did to run the game is 

cd downloads/FretsOnFire

sh FretsOnFire

---

### Post by XtremeBlaze on 2007-12-13
I did the exact same thing and the game works now :) thanks

only thing now is that when i tried to install the secong package **libsdl-mixer1.2** it said that it wasn't compatible with my version of Linux. And now when I play the game it's really jumpy, and when I save any settings I change the game crashes and goes back to the desktop, but the screen doesn't go back to the normal resolution and i have to turn off the computer :( my computer has better than the minimum specs, so would the fact that I don't have the second package installed effect this? and is there a way for me to get this package that is compatible?

---

### Post by Partyboi2 on 2007-12-13
libsdl-mixer1.2 is compatible with dapper, edgy, feisty, gusty. I don't know why you would be getting a message saying it isn't
For the crashing and the screen resolution you could have a look at this:
[http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=3;t=10359;hl=crashes+linux](http://www.fretsonfire.net/cgi-bin/ikonboard.cgi?act=ST;f=3;t=10359;hl=crashes+linux)

---

### Post by XtremeBlaze on 2007-12-13
thanks, i'll try that and see how I go. I have a feeling I may need to reinstall my graphics drivers (which is gonna be a pain) because I've had a lot of trouble with other games....

Also, i'll try and fix this problem with libsdl-mixer1.2..

Thanks for all your help :)

---

