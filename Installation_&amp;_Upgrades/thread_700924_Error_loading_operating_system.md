---
title: "Error loading operating system"
date: 2008-02-18
forum: Installation &amp; Upgrades
---

### Post by Peter-B on 2008-02-18
I have read quite a few relevent posts but non seem to help.

I am unable to install Ubuntu 7.10 x64, I have know knowledge of Linux & have tried 4 times, 

Everything worked ok when I booted it from the CD while still using XP.		

So decided to install it over XP.

1 problem I have is that I can only boot in safe grafix mode, the other option I cannot see the install icon, have tried F4 without any success.
Sometimes it just loads to the desktop without any toobars just the cursor.

When I get to the install icon click it and it starts the installation, every thing works ok asks the usual questions , I choose the wizard &  format the whole disk and it starts the install
When it reaches 79% complete it says something like system locals then disappears and the /target drive icon appears.

The trouble is If I use any of the applications they seem to load from the CD as it spins up, and I can’t remove it!

Another problem is that I want to run BOINC,  I downloaded the file using open with “gedit (default) and I get “could not open boinc_ubuntu_5.10.28 x86 64pc linux-gnu.sh”
gedit has not been able to detect the character coding etc. have tried both options Current locale (UTF-8) & Western (ISO 8859-15)

Have checked the CD with the utility and all’s OK

System is Asus P5B-E 3GHz pressler & 15GB IDE HDD, Grafix card is I think a radeon 550?

Any help would be appreciated as I would like to get back to crunching BOINC tonight else it back to XP!

---

### Post by Partyboi2 on 2008-02-18
try  installing with the [alternate]("http://releases.ubuntu.com/releases/7.10/") cd.

for boinc open a terminal (applications>Accessories>Terminal) and change directory to where the boinc_ubuntu_5.10.28 x86 64pc linux-gnu.sh file is. So if it is found of the Desktop you would
```
cd Desktop
```
then make it executable
```
chmod a+x boinc_ubuntu_5.10.28 x86 64pc linux-gnu.sh
```
then run it
```
sh boinc_ubuntu_5.10.28 x86 64pc linux-gnu.sh
```
or you could try install like  [this]("https://wiki.ubuntu.com/BOINC")

---

### Post by Peter-B on 2008-02-18
Thanks Partyboi2

Its getting late here in pom land so I'm off to bed. will give it a try later.

Gday to ya.

---

