---
title: "cant up date"
date: 2007-04-22
forum: Installation &amp; Upgrades
---

### Post by garymc1 on 2007-04-22
when i run this command in terminal
sudo aptitude update
sudo aptitude upgrade
i get the following message 

garymc@garymc-desktop:~$ sudo aptitude update
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
garymc@garymc-desktop:~$ su
Password: 
root@garymc-desktop:/home/garymc# sudo aptitude update
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
root@garymc-desktop:/home/garymc# sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initialising package states... Done
Building tag database... Done      
The following packages have been kept back:
  subtitleripper 
The following packages will be upgraded:
  libswt3.2-gtk-java libswt3.2-gtk-jni libxine-extracodecs sun-java5-bin 
  sun-java5-jre x-window-system-core 
6 packages upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
Need to get 32.8MB of archives. After unpacking 471kB will be freed.
Do you want to continue? [Y/n/?] y
WARNING: untrusted versions of the following packages will be installed!

Untrusted packages could compromise your system's security.
You should only proceed with the installation if you are certain that
this is what you want to do.

  sun-java5-bin libxine-extracodecs x-window-system-core sun-java5-jre 
  libswt3.2-gtk-java libswt3.2-gtk-jni 

Do you want to ignore this warning and proceed anyway?
To continue, enter "Yes"; to abort, enter "No": yes
E: Could not get lock /var/lib/apt/lists/lock - open (11 Resource temporarily unavailable)
E: Couldn't lock list directory..are you root?
root@garymc-desktop:/home/garymc# 

how can i fix this so i can update i am using ubuntu 610 thanks gary

---

### Post by tkjacobsen on 2007-04-22
It sounds like some apt-get instance is running in the background (maybe automatic security updates). Try to log   out and in again, then try once more. If that's not working try to reboot.

EDIT:
For information:
/var/lib/apt/lists/lock is createt when apt-get (synaptic/aptitude/adept) is running. When this file exists a new apt-get cannot be started.

---

### Post by garymc1 on 2007-04-22
the update manager is running it tells me i have 11 updates but i cant download them, the connection keeps timing out its been like that for 2 weeks

---

### Post by tkjacobsen on 2007-04-22
try to close update-manager and make the command-line update as you did.

---

