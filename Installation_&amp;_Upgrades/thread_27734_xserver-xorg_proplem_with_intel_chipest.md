---
title: "xserver-xorg proplem with intel chipest"
date: 2005-04-17
forum: Installation &amp; Upgrades
---

### Post by abood on 2005-04-17
hi all,
first of all im a newbie in ubuntu, i was using another distro, so yesterday i had installed the new last fresh copy of ubuntu and it goes well as i saw, suddenly after installation i got a blank black screen and in it a small screen moves to all corrners and written in it " sincronismo Errato" i dont know whats thats means but, i tried to check this proplem on the irc, and i didnt get any thing new, i just tried to do 
"sudo dpkg-reconfigure xserver-xorg and it took the right driver setting and it must be the right one,and there is no new, and also i tried Ctrl + Alt + F1 and i entered the shell interface and logged in with my account correctly , so plz guys  help me to be a one of the users of ubuntu and try to help me with this proplrm ASAP.
my pc inormation:
Dell Dimension 2400
256 DDR 333 RAM
2.66 GH'Z
Video: Intel 82845G /GL/GE/PE/GV " Built in card"
Full cashe system.
Thanks For intresting.

---

### Post by alastair on 2005-04-17
It would be a good idea to post :

a) The X config file /etc/X11/xorg.conf

b) The X log : /var/log/Xorg.0.log

---

### Post by abood on 2005-04-18
hi again guys,

for my proplem which i posted up thier i found the solution for it after researching and  testing many times :),
if any body faced this proplem just do this steps :
1) sudo dpkg-reconfigure xserver-xorg
2) follow the computer autodetect and try to c if it correct or not
3) YOU MUST ADD THE VIDEO CARD MEMORY (i dont know maybe its just in my case) IN THE LINE *important
4)choose advanced and put the right frequntley numbers.
5) restart your pc, it may work or not if not go to the next step.
6) Ctrl + Alt + F1
7) login to your account
8) sudo nano /etc/X11/xorg.conf
9) in the monitor section " thats was my proplem" the config didnt put the refresh rates so u must enter them by ur self as the following :
Section monitior
identfier       "ur screen name"
HorizSync     Rate1-Rate2       <=- u must add this line and change the rates
VertRefresh  Rate1-Rate2       <=- u must add this line and change the rates

End Section

the horiz and the vert those are the important edit them and restart ur pc after that :)
and wish to u good luck.

---

### Post by abood on 2005-04-18
hi again guys,

for my proplem which i posted up thier i found the solution for it after researching and  testing many times :),
if any body faced this proplem just do this steps :
1) sudo dpkg-reconfigure xserver-xorg
2) follow the computer autodetect and try to c if it correct or not
3) YOU MUST ADD THE VIDEO CARD MEMORY (i dont know maybe its just in my case) IN THE LINE *important
4)choose advanced and put the right frequntley numbers.
5) restart your pc, it may work or not if not go to the next step.
6) Ctrl + Alt + F1
7) login to your account
8) sudo nano /etc/X11/xorg.conf
9) in the monitor section " thats was my proplem" the config didnt put the refresh rates so u must enter them by ur self as the following :
Section monitior
identfier       "ur screen name"
HorizSync     Rate1-Rate2       <=- u must add this line and change the rates
VertRefresh  Rate1-Rate2       <=- u must add this line and change the rates

End Section

the horiz and the vert those are the important edit them and restart ur pc after that :)
and wish to u good luck.

---

