---
title: "Tasksel Destroyed Ubuntu"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by PureW on 2007-10-31
Hello, I have really screwed Ubuntu up.

When trying to install LAMP, I fired up tasksel in a terminal and checked LAMP and hit ok.

After this, Tasksel started removing a lot of programs. This made me scared so I tried quitting with ctrl+z which didn't work so I closed the terminal window.

My thirst thought was that Tasksel started transforming my Ubuntu 7.10 install to a Server install, removing all unnecessary programs.

Now I can't even open up a terminal and try to reverse the action, what do I do???

---

### Post by louieb on 2007-10-31
See if you can get into Synaptic and do a reinstall of ubuntu-desktop. 

Apt sometimes weirds out and removes stuff it should not. BTW: tasksel  is the way I got LAMP up and running so I know it can work. 

IF you cant get Synaptic  Ctrl+Alt+F1 and log on to a tty session. and try installing again.    

Hindsight is 20/20 but I learned the same way you did about reading the stuff about what its going to do before telling it to do it.

---

### Post by PureW on 2007-10-31
> **louieb said:**
> See if you can get into Synaptic and do a reinstall of ubuntu-desktop. 

Apt sometimes weirds out and removes stuff it should not. BTW: tasksel  is the way I got LAMP up and running so I know it can work. 

IF you cant get Synaptic  Ctrl+Alt+F1 and log on to a tty session. and try installing again.    

Hindsight is 20/20 but I learned the same way you did about reading the stuff about what its going to do before telling it to do it.

Internet stopped working so I couldn't install new packages. I have now reinstalled Ubuntu :(

---

### Post by accel on 2007-11-02
I have the same problem as PureW with tasksel and Gutsy.

I want to add a LAMP server and OpenSSH server to the standard Ubuntu desktop.
(the ubuntu-desktop I leave checked in the options)
After: sudo tasksel --> Ubuntu starts to delete all the packages of the Ubuntu-desktop
and stops with an error.

My system is an AMD Athlon 64 3500+ with i386 Ubuntu 7.10.

Is it a Gutsy bug or am I doing something wrong?

---

