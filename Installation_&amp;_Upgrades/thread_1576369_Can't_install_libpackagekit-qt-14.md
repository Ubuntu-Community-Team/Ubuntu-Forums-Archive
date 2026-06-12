---
title: "Can't install libpackagekit-qt-14"
date: 2010-09-17
forum: Installation &amp; Upgrades
---

### Post by cfw34683 on 2010-09-17
For some reason when i run this i can not get it installed. how can i fix this?

```
cfw@cfw-desktop:~$ sudo aptitude search qt-14

p   libpackagekit-qt-14                        - Library for accessing PackageKit using Qt. 
                                    
cfw@cfw-desktop:~$ sudo apt-get install libpackagekit-qt-14

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
  libpackagekit-qt-14: Depends: libqt4-dbus (>= 4:4.7.0~beta2) but 4:4.6.3-0ubuntu1 is to be installed
                       Depends: libqt4-sql (>= 4:4.7.0~beta2) but 4:4.6.3-0ubuntu1 is to be installed
                       Depends: libqt4-xml (>= 4:4.7.0~beta2) but 4:4.6.3-0ubuntu1 is to be installed
                       Depends: libqtcore4 (>= 4:4.7.0~beta2) but 4:4.6.3-0ubuntu1 is to be installed
E: Broken packages

```I have all the broken pkgs installed as well

---

### Post by cfw34683 on 2010-09-17
I think that the 
```
Depends: libqt4-dbus (>= 4:4.7.0~beta2) but 4:4.6.3-0ubuntu1 is to be installed 
```means that i need to install
4:4.7.0~beta2
that lead me to this page [https://launchpad.net/ubuntu/+source/qt4-x11/4:4.7.0~beta2-0ubuntu1]("https://launchpad.net/ubuntu/+source/qt4-x11/4:4.7.0%7Ebeta2-0ubuntu1")
i have that downloaded but i do not know how to install it. can anyone help?


this is what i want to install
[http://www.ubuntuupdates.org/packages/show/204331](http://www.ubuntuupdates.org/packages/show/204331)
how can i install the 4:4.7.0~beta2-0ubuntu1~lucid1~ppa1 from that page?

---

### Post by cfw34683 on 2010-09-17
can anyone lend some insight as to what i can do to fix this?

---

### Post by cfw34683 on 2010-09-17
Please post your thoughts on what I can do. i am all out of options.
it seems that the pkg is being told not to update. how can i force this?

---

### Post by Lateralis on 2010-09-17
Are you running Maverick?  I seem to remember seeing a lot of these errors when I was running the Karmic Alpha3->RC last year.  After the release date all of these dependency issues cleared up.  So, if you are running Maverick, you may just have to sit tight and wait for the unstable Maverick to become, well, a stable release.

---

### Post by cfw34683 on 2010-09-17
Thanks for your reply. i guess ill just have to wait

---

