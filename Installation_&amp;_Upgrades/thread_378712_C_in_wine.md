---
title: "C:\ in wine"
date: 2007-03-07
forum: Installation &amp; Upgrades
---

### Post by cnc95fan on 2007-03-07
Hi, i am new in ubuntu and linux  and i downloaded wine so i could run windows programs, i loaded the app luancher and i went into drives and it said there is no c:\ drive this is not so great remember to click add to create one! i tried that and i also tried auto detect,  but every time i load the app luancher program and lcick drives, it keeps coming up with the no c:\ drive message, can anyone help? 
thanks

---

### Post by dotman on 2007-03-07
Have you created a virtual C: drive folder somewhere? 

Usually wine makes one for you at ~/.wine/drive_c. Make sure there is a Program Files/ and a windows/ folder in drive_c/ too. Then from the wine configuration GUI map C: to ~/.wine/drive_c

---

### Post by zvacet on 2007-03-08
In terminal type &#733;winecfg&#733;and when opens go>drives and press autodetect

---

### Post by cnc95fan on 2007-03-08
i tried both of them but there is no folder called drive_c in the wine dir and whemn i type that command into the terminal, go to drievs, press auto detect and click ok and go back into the program, it still asks me to create a drive

---

### Post by dotman on 2007-03-08
well the i think you need to create a dir to store "windows" files in. the default is usually in ~/.wine/ so if you manually create that directory structure you can just tell wine to use it. so in ~/.wine/ make a dir called drive_c/ then in that new directory make Program Files/ and windows/ then in the wine config tell it to use /home/[yourname]/.wine/drive_c/ as the C: drive.

---

### Post by zvacet on 2007-03-09
Try use wine tools.
[http://ubuntuforums.org/showthread.php?t=149585&highlight=wine]("http://ubuntuforums.org/showthread.php?t=149585&highlight=wine")

---

### Post by cnc95fan on 2007-03-09
still doesnt work

---

### Post by dotman on 2007-03-09
so even when you specify where the "c drive" is it still says it can't find it? did you use a package manager to install it or did you download and compile it?

---

### Post by cnc95fan on 2007-03-10
yep, i specified where i manually created the c drive and i mapped the dir, but it still wont show a c drive and asks me to create a new one, i connectied my ubuntu laptop to the internet(erthnet) and i used add remove programs to install it.. otherwise, using the packet manager, i dunno where its sored, and when iut does install using add remove, it dosnt show in the applications folder,so i deleted the file and reinstalled it and  nothing appears(that has to do with wine) in my folder,oh and i dunno how to create a virtual drive in winetools,

---

### Post by cnc95fan on 2007-03-10
wait, can we start this topic again, i found out i was missing some files and looking in the wrong folder...sry, eventually, i creted a c drive but i then remeapped it to go into my user file, so it got all screwed up,:lolflag:  and now i dunno how to tell it to create a c disk again. ive tried the autodetect and add buttons, and the file im using is in filesystem/usr/bin

---

### Post by zvacet on 2007-03-11
Delete wine with synaptic.Delete .wine folder in your home directory.Reinstall wine and now follow instructions you have from previous posts.

---

