---
title: "Google Chrome won't install"
date: 2009-10-04
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by dmillerw on 2009-10-04
Everytime I attempt to install Google Chrome through the unstable .deb file, I get this error

[[IMG]http://img33.imageshack.us/img33/7279/googlechromeinstallerro.th.png[/IMG]](http://img33.imageshack.us/my.php?image=googlechromeinstallerro.png)

Any ideas, also got this when installing Skype.

---

### Post by wilee-nilee on 2009-10-04
I believe that Google Chrome will only run through wine, you need Chromium if you are not using wine, it is in synaptic.

---

### Post by joey-elijah on 2009-10-04
> **wilee-nilee said:**
> I believe that Google Chrome will only run through wine, you need Chromium if you are not using wine, it is in synaptic.

Running a .deb file through wine?! Are you craaazy! :P

Google provide an official .deb snapshots of Google Chrome, that's what the OP is referring to. 

[ you can find them @ [http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux) ]

> **dmillerw said:**
> Everytime I attempt to install Google Chrome through the unstable .deb file, I get this error
 Any ideas, also got this when installing Skype.

Have you tried installing it via the terminal with dpkg -i ? 

cd to wherever you've saved the .deb
then
sudo dpkg -i google(just hit tab and it'll fill in the rest).deb 
et voila!

Annoyingly so far in Karmic there has been an issue with GDebi (the GUI for installing .debs) which fails to install pretty much everything you through at it, doing it via the terminal however works fine. :)

---

### Post by forcecore on 2009-10-04
Download daily build or update then it works, this was Ubuntu bug but now it is fixed.

---

### Post by dmillerw on 2009-10-04
Thanks joey-elijah, that worked

---

### Post by wilee-nilee on 2009-10-04
> **joey-elijah said:**
> Running a .deb file through wine?! Are you craaazy! :P

Google provide an official .deb snapshots of Google Chrome, that's what the OP is referring to. 

[ you can find them @ [http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux](http://dev.chromium.org/getting-involved/dev-channel#TOC-Linux) ]



Have you tried installing it via the terminal with dpkg -i ? 

cd to wherever you've saved the .deb
then
sudo dpkg -i google(just hit tab and it'll fill in the rest).deb 
et voila!

Annoyingly so far in Karmic there has been an issue with GDebi (the GUI for installing .debs) which fails to install pretty much everything you through at it, doing it via the terminal however works fine. :)

 A little crazy maybe ;) I don't use wine at all I just boot over to XP if I need windows, glad your advice worked for the OP

---

### Post by nanog on 2009-10-05
> I don't use wine at all I just boot over to XP if I need windows

You should really try virtualbox -- huge improvements including directx 3d support.

---

### Post by mobilediesel on 2009-10-05
I installed chrome from Google's Linux Software Repositories using the instructions [here]("http://www.google.com/linuxrepositories/ubuntu704.html"). It says Ubuntu 7.04 but it worked fine on 8.04.

---

