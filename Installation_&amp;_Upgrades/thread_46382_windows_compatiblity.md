---
title: "windows compatiblity"
date: 2005-07-04
forum: Installation &amp; Upgrades
---

### Post by dutch_boi1 on 2005-07-04
hi i was just wondering if there is a way 2 use windows programs or games on ubuntu using a program or something. at the moment i have WINE but i cant seem 2 install it. if u could help me 2 install that it would help unless u have another solution to making ubuntu more compatible with windows.

wen running synaptic i get this error saying cant find the source or cd and cant read from this file, i am new to ubuntu and have no idea at all on wat is goin on, plz help

---

### Post by jarrett.wold on 2005-07-06
Drop the YM slang.


Instructions:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)

---

### Post by nocturn on 2005-07-06
[QUOTE=jarrett.wold]Drop the YM slang.


Instructions:
[http://www.winehq.com/site/download-deb](http://www.winehq.com/site/download-deb)[/QUOTE]

What is YM slang?

---

### Post by dutch_boi1 on 2005-07-06
yeh is ym slang meant to be something like young man slang ?

that still doesnt help me on installing wine, i have downloaded them maunally , like from the website, because ubuntu doesnt have internet yet, i burned the downloaded packages to a cd, how do i install them?

---

### Post by nocturn on 2005-07-06
[QUOTE=dutch_boi1]yeh is ym slang meant to be something like young man slang ?

that still doesnt help me on installing wine, i have downloaded them maunally , like from the website, because ubuntu doesnt have internet yet, i burned the downloaded packages to a cd, how do i install them?[/QUOTE]

sudo dpkg -i <package.deb>

---

### Post by dutch_boi1 on 2005-07-06
o ok, will this relize to look in the cd or not? cauz it should just plain install with everything in the right place right? and add shortcuts? etc?

---

### Post by nocturn on 2005-07-06
[QUOTE=dutch_boi1]o ok, will this relize to look in the cd or not? cauz it should just plain install with everything in the right place right? and add shortcuts? etc?[/QUOTE]

If you want to install from CD, pop it in.
Open a terminal and move to the directory where the debs are (cd /media/cdrom/)

Execute the sudo dpkg command there, this will install wine.
To run a windows app, you will need to run the command 'wine <pathtoexe>'

---

### Post by dutch_boi1 on 2005-07-07
1st i went into synaptic and tried to add the cdrom and it says it cant find the log type file in var/libs/apt/lists. i have it in the wine thingy but i cant copy+paste it into there because it says that i dont have root permissions, and i dont know how 2 log into root because at the login i type in root and the password which i set and it doesnt do anything, is there a way i could copy that file into var/libs/apt/lists?

i tried typing in sudo dpkg, in the cdrom directory with in the terminal but it says it cant find the log file i was going on about before, i think it needs it to say what packages to install. there are 5 packages in total, that belong to wine, 4 2kb ones and 1 14mb 1.

what should i do? please help

---

### Post by nocturn on 2005-07-07
[QUOTE=dutch_boi1]1st i went into synaptic and tried to add the cdrom and it says it cant find the log type file in var/libs/apt/lists. i have it in the wine thingy but i cant copy+paste it into there because it says that i dont have root permissions, and i dont know how 2 log into root because at the login i type in root and the password which i set and it doesnt do anything, is there a way i could copy that file into var/libs/apt/lists?

i tried typing in sudo dpkg, in the cdrom directory with in the terminal but it says it cant find the log file i was going on about before, i think it needs it to say what packages to install. there are 5 packages in total, that belong to wine, 4 2kb ones and 1 14mb 1.

what should i do? please help[/QUOTE]

Ok, first the copy.  You cannot log in as root on Ubuntu, you log in as a user and become root by using sudo.
So 
```
sudo cp file /var/libs/apt/lists
```
should work.

---

### Post by dutch_boi1 on 2005-07-11
um by any chance are you using hoary? and by typing in the consol 

> sudo cp file /var/libs/apt/lists 

where is the file that i want to copy? is the that the thing that says " file " in the command?

thankx

---

