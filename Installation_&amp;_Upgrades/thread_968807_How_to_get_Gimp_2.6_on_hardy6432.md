---
title: "How to get Gimp 2.6 on hardy64/32"
date: 2008-11-03
forum: Installation &amp; Upgrades
---

### Post by otz070 on 2008-11-03
Since I found it so much of an nucance to get to work Now that I did I thought I'd post it here so if anyone else has trouble

1. []("http://www.getdeb.net/app/Gimp") at the bottom of page use click for hardy 64 bits (or 32 bits if using 32bits:))

2. download all 5 .deb packages to a folder on your desktop name it WITHOUT spaces (example gimpnew) 

2.5 (because I almost forgot this most critical step) remove using synaptic old version of gimp and all components (click the check box to the left of gimp and select complete removal ok all the following screens (should only have gimp components here though use common sense don't let it remove something importatnt) then apply.

3.open up terminal 
cd (Insert directory here) (easy way is to open folder containing the packages right click select propertys and select and copy location and paste it right after cd (make sure there is a space after cd though:))
(example   cd /home/username/desktop/gimpnew)
This will return ~/Desktop/gimpnew$ 


4. next type sudo dpkg -i (space after i ) then all 5 package names (easy way is to right click propertys on each one at atime and copy the name from the top text box ) make sure you put a space between each:)

5.you will probably get prompeted for your password here

6. if every thing went ok gimp 2.6 will be installed in your applications menu:)

have fun:)

---

