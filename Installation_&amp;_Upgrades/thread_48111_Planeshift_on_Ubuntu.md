---
title: "Planeshift on Ubuntu"
date: 2005-07-11
forum: Installation &amp; Upgrades
---

### Post by umfana on 2005-07-11
[size=2][font=Century Gothic]Hi

I am an "umuntu" (=person as expressed in Zulu) and fairly new to Linux. I have played around with various SuSE Linux versions, but admit never having gotten the hang of it due to not being used to command lines ](*,).
When I heard from Ubuntu, I knew straight away I'd like it, as I knew the meaning of the word before reading the explanation on the ubuntu homepage.

My expectations have been far exceeded =D> and I think I'll stay with Ubuntu. I am quite sure that with this Linux I'll be able to do give good ole Billy the kick from anyone of my PCs for good:arrow:.

Jdobson has made a list of games to be played on Linux. So I picked one: Planeshift

I downloaded the thing with wget. All that went fine (or at least it looked to me so), after download I have now a PLaneshift_CBVO.3.010.run in umfana@ubuntu.

How can I get this to install and run please?

Can anyone help





[/font][/size]

---

### Post by twowheeler on 2005-07-11
EDIT: this post contained some not-quite-right information.  I am cleaning it up so others are not as confused as I --

1.  This intstaller wants the dialog package.  So open up Synaptic and search for 'dialog'.  Install the package.

2.  In nautilus, select the .run file and change the Properties -- Permissions tab so that the file is executable.

3.  Then double click on the file.  You may get a box asking if you want to run the file or edit it.  If so, select 'Run'.  It should run and install some temporary files.  Then the installer should pop up a dialog box in a terminal asking where you want to install the game.  Answer with '~', meaning your home directory.

Note, I have tried to install this game under /usr/games, but it will not run from there.  This is true even after running a 'chgrp -R games' on the planeshift directory.  It opens the game window but then immediately closes and quits.  There must be a permissions problem, but I have not figured out what it is.  Because of the size of the package, you probably don't want to install this thing in multiple user directories.

4.  You have to make a desktop launcher for it, otherwise you will have to start it from the commandline every time.  The game program is '~/planeshift/psclient'.  

5.  You will have to register a user name at their web site before playing.

Note, planeshift is a demanding game resource-wise.  It wants plenty of memory, a speedy processor, and a good graphics card.  The web site [www.planeshift.it](www.planeshift.it) has details.

---

