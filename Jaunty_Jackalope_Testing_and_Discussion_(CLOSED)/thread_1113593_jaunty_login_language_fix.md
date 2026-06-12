---
title: "jaunty login language fix"
date: 2009-04-01
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by utnr6 on 2009-04-01
ok, after reading 1billion unsuccessful answers to my problem I came up with the perfect fit to finally login to my ubuntu 9.04.  

the problem was that after my first session, when i logged in again the language was in arabic and wouldnt allow me to login... i know its affecting many others so here is the fix

login with your jaunty iso cd that you installed from and when the initial screen appears... choose "try ubuntu without any changes to my computer"

at the login screen, allow it to automatic log-on after the 10 seconds and then open a terminal

click the places tab and choose the location of your ubuntu install.  browse the folders to find the location of the problem which is etc/default/console-setup

inside this folder, if you open it with text editor, you are not allowed to change the language.  the language you are set to is "af" and it should be "us"

you must run from your temporary terminal the "sudo" command and change the "af" to "us" from there and save it, then you are done and can login to your ubuntu

i believe the exact terminal command "sudo gedit /media/etc/default/console-setup

then just change "af" to "us" and voila

---

### Post by Zorael on 2009-04-02
Small correction!
> **utnr6 said:**
> i believe the exact terminal command "sudo gedit /media/etc/default/console-setup
Here Be Dragons. You *always* want to use **gksu** or **kdesudo** for obtaining superuser permissions for graphical applications. Using sudo like that may/will eventually bork file permissions in your home directory. You want to stick to terminal commands with sudo; sudo nano, sudo apt-get, sudo mv, sudo cp, etc.

</tangent>

---

