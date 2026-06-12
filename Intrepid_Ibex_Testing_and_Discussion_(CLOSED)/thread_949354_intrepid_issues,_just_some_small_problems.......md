---
title: "intrepid issues, just some small problems......"
date: 2008-10-16
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by techno-mole on 2008-10-16
hello all.

well like a lot of people im using the beta of intrepid (not long now before they release an rc) and like some im having some issues, mine cant be considered too important, but they are annoying all the same.

the first being i still cant use my bluetooth adapter, it worked before the updated the kernel to 2.6.27-7-generic, but then on the other hand from what i read if they hadnt have upgraded the kernel the nvidia drivers wouldnt have worked properly for some people (me included) so i guess you really cant have your cake and eat it :) 
the bluetooth isnt a big problem for me, but i would like it to work as it saves having to take the sd card out of my phone to transfer files, i have filed a launchpad report about this though.

the other really annoying thing is for some reason i cant add launchers to the desktop or the panel, well i sort of can, but for some reason instead of a firefox icon or open office icon i get a generic gear icon instead, even if i edit the launcher, the same goes for adding items to the favourites as well (using kbubuntu by the way)

although i have discovered that i can get the launchers to display correctly, ive found that if the launcher i want to create has a .desktop file in usr/share/applications once ive created the launcher i get the generic gear icon, but if i go into usr/share/applications and delete the .desktop file for that application and then create the launcher it appears as it should, i have no idea why this is so, but it worked for me, so if you are having the same issue then try this - 

go to usr/share/applications and look for the .desktop file of the application, if its there open usr/shar/applications as root and delete it
then try and create the launcher again using the menu editor, and it should work.

" Please do not delete all the .desktop files in usr/share/applications (i did this the first time, and found most of my menu items disappeared)
just do it one at a time for the launchers you want to create "

---

