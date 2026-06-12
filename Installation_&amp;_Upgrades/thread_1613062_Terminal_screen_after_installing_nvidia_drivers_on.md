---
title: "Terminal screen after installing nvidia drivers on ubuntu 10.04!!"
date: 2010-11-04
forum: Installation &amp; Upgrades
---

### Post by extremejosh on 2010-11-04
OK, this is for anyone who installed nvidia drivers on Ubuntu 10.04 and gets a terminal screen on reboot with no GUI.I came across this fix trying to install the drivers on Ubuntu 10.10. later i find that the same thing happens to me on 10.04 but one of the fixes i came across works perfect with it. Ok, so you just installed ubuntu 10.04 updated it through update manager and installed your nvidia drivers but when you rebooted and tried to log on you find yourself in a terminal interface well i found an easy fix for that and i hope it works for you not saying it will though im new to the linux world only just coming out of windows and i dont know much anyways just log on the terminal and use command "sudo dpkg-reconfigure xserver-xorg" then run 
nvidia-xconfig command reboot and you should be fine only wish this would work for ubuntu 10.10 but it doesn't and if this is a common i didnt know i search all over these forums and others for the past 4 days looking for these answers hope this helps

---

### Post by linux18 on 2010-11-04
did you use the binary drivers from the repositories or from nvidia's website?

if you type startx or xinit what error message do you get?

---

### Post by extremejosh on 2010-11-04
> **linux18 said:**
> did you use the binary drivers from the repositories or from nvidia's website?

if you type startx or xinit what error message do you get?
yes i used the repository drivers the current recommended ones ive tried the others too and i once install newer drivers from a ppa all with the same results although the one with the ppa was a little bit better anyways i ran those two commands i get the same errors stuff like "failed to initialize nvidia graphic device" "xinit: unable to connect to xserver" xinit: no such process  and on and on
ive been working on this problem in another thread maybe something in there will help you help me:)

[http://ubuntuforums.org/showthread.php?t=1611450](http://ubuntuforums.org/showthread.php?t=1611450)

---

### Post by linux18 on 2010-11-04
your hands will get very tired but:

```
sudo chmod 755 /usr/bin/dpkg
sudo aptitude clean; sudo apt-get autoclean; sudo apt-get update; sudo sudo apt-get upgrade dpkg synaptic
sudo apt-get autoremove; sudo apt-get -f install; sudo aptitude -f install; sudo apt-get --fix-broken upgrade
sudo apt-get purge nvidia* 
sudo dpkg-reconfigure -a  

```

---

### Post by extremejosh on 2010-11-04
> **linux18 said:**
> your hands will get very tired but:

```
sudo chmod 755 /usr/bin/dpkg
sudo aptitude clean; sudo apt-get autoclean; sudo apt-get update; sudo sudo apt-get upgrade dpkg synaptic
sudo apt-get autoremove; sudo apt-get -f install; sudo aptitude -f install; sudo apt-get --fix-broken upgrade
sudo apt-get purge nvidia* 
sudo dpkg-reconfigure -a  

```
LOL wow thats so many commands it makes me think it will definitely work it have to wait like 30 mins though because ive been installing and uninstall different drivers now instead of a terminal screen i get a blank screen so after im done reinstalling should i run those commands first or install the drivers and should i install the drivers from the repository or should i download newer drivers?

---

### Post by linux18 on 2010-11-04
just run the commands the next chance you get to try and return the system to the way it was before the drivers were installed, my theory at this point is that the driver installation made a mistake at some point which borked your X configuration which is why I have so many apt fixing commands in the list.

---

### Post by extremejosh on 2010-11-04
Oh I see ok well thanks ill definitely try it hope it works out

---

### Post by extremejosh on 2010-11-04
ill try it thanks hope it works out

---

### Post by extremejosh on 2010-11-04
Should i run these commands one at a time and checking to see if they had any affect or run them all at once then check?

---

### Post by extremejosh on 2010-11-04
> **linux18 said:**
> just run the commands the next chance you get to try and return the system to the way it was before the drivers were installed, my theory at this point is that the driver installation made a mistake at some point which borked your X configuration which is why I have so many apt fixing commands in the list.
when you say "return the system to the way it was before the drivers" does that mean it uninstalls the drivers? cause i can pretty much do that by going into recovery mode and just turning the drivers off from the repository then reboot and all is good just that the drivers wont be installed witch i really need.

---

### Post by linux18 on 2010-11-04
this will uninstall them but do it very cleanly and fix any apt issues at the same time, it's much more effective than the regular uninstall and allows you to reinstall with a very good chance that everything will work

---

### Post by laylow45 on 2010-11-04
> **linux18 said:**
> this will uninstall them but do it very cleanly and fix any apt issues at the same time, it's much more effective than the regular uninstall and allows you to reinstall with a very good chance that everything will work
Hi Linux18

I went through the same pains when I inadvertently updated from 10.04 LTS 64 bit to 10.10 64 bit...

Think I found the solution to my particular problem... :P
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by extremejosh on 2010-11-04
Unfortunately it didn't work out...those commands so im going to start using 10.04 or maybe try out other dirstro's i did come across one that i thought was interesting called ultimate edition i guess its built off of ubuntu? idk im new to linux

---

### Post by extremejosh on 2010-11-07
Just wanted to add and this worked for me on both 10.04 and 10.10 go into the grub at start up and after quiet splash type vmalloc=192M then hit ctrl+x to restart

---

