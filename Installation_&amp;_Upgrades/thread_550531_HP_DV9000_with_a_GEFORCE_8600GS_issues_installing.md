---
title: "HP DV9000 with a GEFORCE 8600GS issues installing"
date: 2007-09-14
forum: Installation &amp; Upgrades
---

### Post by tached.out on 2007-09-14
OMG I just got a new laptop with vista and i want to throw it away right now.

I have tried to install Ubuntu on it meny times and it does not seem to work some one please help. I am not totally retarted because i use to run redhat but still a little brain dead on this.

I couldnt do the regular installation so I did the text version of it and installed it great. It will not boot into the GUI at all. It sticks in the command prompt. 

Some thing about my x server and stuff like that is not working. After some research I think it is because of my graphics card.

My computer is a new HP DV9000 with a Geforce 8600GS. 

Has any one ran into this or can help me with this. I have ran tons of Sudo commands that I have read on here but I still cant seem to do it. Some one please help.

---

### Post by forestpixie on 2007-09-14
try this 
```
sudo dpkg-reconfigure xserver-xorg
```

when you get to choose card type try to use nv, if it doesnt work use vesa instead.

once you're in try the restricted drivers management in system>admin

or you could try to use [envy]("http://albertomilone.com/nvidia_scripts1.html") -

you should be able to find plenty of threads on the Abs Beg Forum for your card - I've seen many

---

### Post by tached.out on 2007-09-14
why is it that when i use VMWARE it installs right away. but when i try to install it to wipe out my vista it wont let me install it with the pretty way but i have to use the text installation.

i still have not seen any gui at all its all command prompt

---

### Post by forestpixie on 2007-09-14
does X still fail ? 

> why is it that when i use VMWARE it installs right away. but when i try to install it to wipe out my vista

I'm not understanding how you're using vmware to wipe vista :(

---

### Post by tached.out on 2007-09-14
no im not using VM i just tested VM to see if my cds work or not they the work perfect on VM but not from a BOOT

---

### Post by forestpixie on 2007-09-14
did you run the reconfigure x command?

---

