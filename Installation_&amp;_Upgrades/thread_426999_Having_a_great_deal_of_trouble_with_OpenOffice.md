---
title: "Having a great deal of trouble with OpenOffice"
date: 2007-04-29
forum: Installation &amp; Upgrades
---

### Post by midgewa on 2007-04-29
Hey guys, im a new convert to linux and Ubuntu.

so far everything has gone very well except that I cant get any of the openoffice things to work. When i go the the main menu and click on any of them, nothing happens.. nothing loads and the screen just goes back to whatever else is running.

Ive asked alot on the OCAU forums about this and they sent me here coz nothing we tried there worked.

here is a quick list of things that havent worked ( i dont really understand alot of what is happening coz im very new to this, but i was just following instructions)

First try:
raz@midgewa:~$ sudo apt-get remove openoffice
Password:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package openoffice
raz@midgewa:~$ sudo apt-get install openoffice
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package openoffice
raz@midgewa:~$

and then this:
raz@midgewa:~$ sudo apt-get remove ooffice
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package ooffice
raz@midgewa:~$ sudo apt-get install ooffice
Reading package lists... Done
Building dependency tree 
Reading state information... Done
E: Couldn't find package ooffice


then i posted this pic to show them the command or whatever:
[http://img167.imageshack.us/img167/7218/screenshottj4.png](http://img167.imageshack.us/img167/7218/screenshottj4.png)

then this:
raz@midgewa:~$ sudo apt-get install openoffice.org
Password:
Reading package lists... Done
Building dependency tree 
Reading state information... Done
openoffice.org is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 6 not upgraded.
raz@midgewa:~$

then this:
raz@midgewa:~$ sudo apt-get remove openoffice.org
Reading package lists... Done
Building dependency tree 
Reading state information... Done
The following packages will be REMOVED:
openoffice.org
0 upgraded, 0 newly installed, 1 to remove and 6 not upgraded.
Need to get 0B of archives.
After unpacking 28.7kB disk space will be freed.
Do you want to continue [Y/n]? y 
(Reading database ... 89092 files and directories currently installed.)
Removing openoffice.org ...
raz@midgewa:~$ sudo apt-get install openoffice.org
Reading package lists... Done
Building dependency tree 
Reading state information... Done
Suggested packages:
hunspell-dictionary menu unixodbc msttcorefonts openoffice.org-officebean
openclipart-openoffice.org pstoedit imagemagick gstreamer0.10-plugins-ugly
gstreamer0.10-plugins-bad gstreamer0.10-ffmpeg
Recommended packages:
openoffice.org-filter-binfilter
The following NEW packages will be installed:
openoffice.org
0 upgraded, 1 newly installed, 0 to remove and 6 not upgraded.
Need to get 3092B of archives.
After unpacking 28.7kB of additional disk space will be used.
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main openoffice.org 2.2.0-1ubuntu3 [3092B]
Fetched 3092B in 0s (30.2kB/s) 
Selecting previously deselected package openoffice.org.
(Reading database ... 89092 files and directories currently installed.)
Unpacking openoffice.org (from .../openoffice.org_2.2.0-1ubuntu3_i386.deb) ...
Setting up openoffice.org (2.2.0-1ubuntu3) ...

raz@midgewa:~$




THEN i tried to download it and install it myself but it came from the site with RPM files in it which im am told arent for debian in which i need DEB files, and this is when i got directed here because they ran out of ideas...

I hope some of what ive done so far made sense... and can anyone help me?

Completely reinstalling Ubuntu would be a last option for me though.

---

### Post by aidanr on 2007-04-29
> /usr/lib/openoffice/program/ooqstart: not found

that file is in openoffice.org-core, try:
```
sudo apt-get --reinstall openoffice.org-core
```

or use synaptic package manager to search for it and reinstall it

---

### Post by midgewa on 2007-04-29
root@midgewa:~# sudo apt-get --reinstall openoffice.org-core
E: Invalid operation openoffice.org-core
root@midgewa:~#



something else u might find helpful from OCAU:

root@midgewa:~# ls -l /usr/lib/openoffice/program
total 0
root@midgewa:~#


apparently this means the folder is empty?

---

### Post by trents on 2007-04-29
By any chance have you also installed the firegl 3D accerator drivers? After installing them, I found that some of my aps wouldn't open, Open Office being one of them.

Steve

---

### Post by aidanr on 2007-04-29
ok shoulda tried that out first, not sure why that didn't work, do this instead:

sudo aptitude reinstall openoffice.org-core

---

### Post by midgewa on 2007-04-29
I may have, not sure... i installed some graphics driver though.. it was an nvidia one, suggested by ubuntu... from memory it was for beryl

---

### Post by midgewa on 2007-04-29
did what u said:

> root@midgewa:~# sudo aptitude reinstall openoffice.org-core
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
The following packages have been kept back:
  gnome-panel gnome-panel-data libpanel-applet2-0 tzdata update-manager 
  update-manager-core 
The following packages will be REINSTALLED:
  openoffice.org-core 
0 packages upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 6 not upgraded.
Need to get 35.5MB of archives. After unpacking 0B will be used.
Writing extended state information... Done
Get:1 [http://au.archive.ubuntu.com](http://au.archive.ubuntu.com) feisty/main openoffice.org-core 2.2.0-1ubuntu3 [35.5MB]
Fetched 35.5MB in 30s (1175kB/s)                                                
(Reading database ... 89291 files and directories currently installed.)
Preparing to replace openoffice.org-core 2.2.0-1ubuntu3 (using .../openoffice.org-core_2.2.0-1ubuntu3_i386.deb) ...
Unpacking replacement openoffice.org-core ...
Setting up openoffice.org-core (2.2.0-1ubuntu3) ...
root@midgewa:~# 



but if that was meant to fix it, it didnt... they still wont run.



(im about to reinstall everything using synaptic (advice from OCAU))

---

### Post by aidanr on 2007-04-29
is it the same output when you try to run it in the terminal or something different?

---

### Post by midgewa on 2007-04-29
FINALLY... thanks for your help people but it seemed that reinstalling it all in synaptic was the way to go.

thankyou all.

---

