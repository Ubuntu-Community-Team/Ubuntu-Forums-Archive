---
title: "Jaunty migration"
date: 2009-03-28
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by brazz43 on 2009-03-28
Hello! Here is my problem: I made a migration to jaunty beta from Intrepid. Now everything works much however I have a very serious problem: it is impossible to have the command line! if I start gnome-terminal I receive an error like "!" There was an error during the creation of the son process for this terminal! Anyway, all terminal programs give me the same thing: a window without prompt!
Excuse my bad English ...

---

### Post by Kevbert on 2009-03-28
Probably the best way to resolve this would be to go to System-Admin-Synaptic and search for gnome-terminal. Right-click on gnome-terminal and mark for re-installation. Do the same for gnome-terminal-data and then click on Apply.
Then close Synaptic and try opening terminal. Now run
```
sudo apt-get update
sudo apt-get install -f
```
To repair any damaged packages.

---

### Post by brazz43 on 2009-03-28
Oh thanks, Kevbert! I did it but in Synaptics I obtain a "	
failure of cloning pty" message and of course 	
nothing is done.

---

### Post by brazz43 on 2009-03-28
OK, infortunatly Synaptics does not work and  I have always the same message about cloning pty(?).

---

### Post by Kevbert on 2009-03-28
OK. Another way to get the packages is to download the deb file from [[COLOR="Red"]here[/COLOR]]("http://packages.ubuntu.com/jaunty/gnome/").  Download the gnome-terminal and gnome-terminal-data deb files for your system to the desktop. Then double click on each of the deb packages to install them. The only problem with this method is that you may not get all the support files (detailed on the page for each deb package). You should run the terminal commands afterwards detailed in my previous post.

---

### Post by brazz43 on 2009-03-28
Here's what I did: I changed my console with <Ctrl><Alt F3> and I installed using dpkg-i the two packages, After I run sudo apt-get -f install, and then sudo apt-get update ... And I return on <Ctrl><Alt F7> my gnome desktop but I have always the same.

---

### Post by Kevbert on 2009-03-28
> **brazz43 said:**
> Here's what I did: I changed my console with <Ctrl><Alt F3> and I installed using dpkg-i the two packages, After I run sudo apt-get -f install, and then sudo apt-get update ... And I return on <Ctrl><Alt F7> my gnome desktop but I have always the same.

Did you download the two packages ? If not, it's possible that you've installed the packages from the cache (the faulty ones which were originally installed).

---

### Post by brazz43 on 2009-03-28
OK I am here now :) yes I have the 2 debs from [http://packages.ubuntu.com/jaunty/gnome/](http://packages.ubuntu.com/jaunty/gnome/) and I have installed  with dpkg in command mode from the alternate console ( with Ctrl+Alt+F3 ). I think perhaps it is a gnome problem ?

---

### Post by Kevbert on 2009-03-28
Something has been corrupted during upgrade. The problem may be with the support files mentioned on the package download pages (some of these are important for other programs such as the libc6 library).
It may be safer to start again and install Jaunty from scratch.
I don't believe this is a bug (I'm running Jaunty Ubuntu Beta which has been upgraded from Alpha3 onwards).

---

### Post by brazz43 on 2009-03-28
OK, I have read this information about download problems yesterday and a possible bad .iso

I start again from beginning, thanks

---

### Post by brazz43 on 2009-03-28
Kevbert, now all is new (no my home of course !) and all run fine... and speedy! I am glad, thank you !

---

### Post by Kevbert on 2009-03-29
Well done. 
The problem with iso files is that often they aren't checksummed (md5summed) after downloading. It's even possible to pass this test and still have a faulty iso, the only symptoms being that the final install takes ages to verify and install (I've had this a couple of times).
Cheers
Kevin.

---

