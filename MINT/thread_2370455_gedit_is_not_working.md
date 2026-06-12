---
title: "gedit is not working"
date: 2017-09-03
forum: MINT
---

### Post by openation1 on 2017-09-03
Hello everyone, first of all i want to wish you all a very happy labor day! ............. well my question is. I am trying to install eclipse-oxygen in linux mint. The one it has it's kind of old and I am going to replace it with this one. I am a newbie in linux mint, I haven't learn it that well yet. The instructions they are giving me are these. To first download it, second extract it to home , and if I want it to run it from the menu to do this.
I started to do this but its telling me that : 
```

openation@ThinkCentre-A70 ~ $  sudo gedit /usr/share/applications/eclipse-oxygen.desktop
[sudo] password for openation: 
sudo: gedit: command not found
```


to run eclipse from the menu
   1. in the terminal enter this code:
```
sudo gedit /usr/share/applications/eclipse-luna.desktop
```
   eclipse-luna will be replaced  by your app name
   2. copy paste the following lines into the newly opened .desktop file
```
[Desktop Entry]
 Encoding=UTF-8
 Exec=/home/user/eclipse-version/eclipse/eclipse
 Icon=/home/user/eclipse-version/eclipse/icon.xpm
 Type=Application
 Terminal=false
 Comment=Eclipse Integrated Development Environment
 Name=Eclipse Luna
 GenericName=eclipse-4.4 M4
 StartupNotify=false
 Categories=Development;IDE;Java;
```
user will be replaced by your user name. (must).
For Exec and Icon, the path should be  correct i.e you must change "user"  & "eclipse-version" according to  your path. (must).
in "Name= Eclipse Luna " you can change the name whatever you want.(optional).

in "GenericName" you can put whatever you want. you can cut off this line too.(optional).
save & exit the .desktop file.
   a new entry named "Eclipse Luna" will be added in the menu under the programming section.
   3. now go to menu->programming->Eclipse Luna.
   Enjoy... your eclipse environment....

LOL I am not going to say I am dum but this is how I feel. If there's someone out there that can instruct me step by step I would appreciated very much. Thank you so much.

:D

---

### Post by SuperFreak on 2017-09-03
I don't think gedit is installed by default anymore because there were issues when used under sudo. Replace gedit with nano or other installed text editor (I like leafpad but you will need to install it)```
sudo apt update
sudo apt install leafpad
```

---

### Post by howefield on 2017-09-03
Thread moved to the "*MINT*" forum.

---

### Post by oldos2er on 2017-09-03
Which version of Mint?

---

### Post by openation1 on 2017-09-03
Hello, I am trying to install eclipse oxygen in the menu but it seems I can't do it.......it's one thing after another. I am giving up.
this is what is coming out after I do this. I am using Linux mint 18.02

```
penation@ThinkCentre-A70 ~ $ sudo /usr/share/applications/eclipse-oxygen.desktop
[sudo] password for openation: 
sudo: /usr/share/applications/eclipse-oxygen.desktop: command not found

```
What else can I do?
Please help me.

---

### Post by jeremy31 on 2017-09-04
Try this
```
sudo apt-get install gksu gedit
```
```
gksu gedit /usr/share/applications/eclipse-oxygen.desktop
```

---

### Post by openation1 on 2017-09-04
Hello jeremy31, I did it exactly like you told me, but it didn't work either I don't know what is going on.
this is what it came out :

openation@ThinkCentre-A70 ~ $ sudo apt-get install gksu gedit
[sudo] password for openation: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gedit is already the newest version (3.18.3-0ubuntu4).
gksu is already the newest version (2.0.2-9ubuntu1).
0 upgraded, 0 newly installed, 0 to remove and 2 not upgraded.
openation@ThinkCentre-A70 ~ $ gksu gedit /usr/share applications/eclipse-oxygen.desktop

** (gedit:25868): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported
openation@ThinkCentre-A70 ~ $ gksu gedit /usr/share/applications/eclipse-oxygen.desktop

** (gedit:25893): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:25893): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:25893): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:25893): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-spell-enabled not supported

** (gedit:25893): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-encoding not supported

** (gedit:25893): WARNING **: Set document metadata failed: Setting attribute metadata::gedit-position not supported

---

### Post by jeremy31 on 2017-09-07
Did the text editor open?  What Mint version are you using as I have used gedit in Cinnamon and I know they changed some things in LM18 where now xed is the GUI text editor instead of gedit

---

