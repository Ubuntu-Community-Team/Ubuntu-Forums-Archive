---
title: "gvim installation"
date: 2015-11-26
forum: Installation &amp; Upgrades
---

### Post by praveen_kumar3 on 2015-11-26
HI, when I am trying to install vim-gnome in ubuntu 12.04 LTS version it says 

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vim-gnome : Depends: libbonoboui2-0 (>= 2.15.1) but it is not going to be installed
             Depends: libgnome2-0 (>= 2.17.3) but it is not going to be installed
             Depends: libgnomeui-0 (>= 2.22.0) but it is not installable
             Depends: libruby1.8 (>= 1.8.7.352) but it is not going to be installed
             Depends: tcl8.5 (>= 8.5.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

What could be the issue, please resolve it..?

----- But when i installed vim, it installed without any dependencies package errors...
----- when i tried to open vim from terminal, it is opening in terminal itself...what is the command to open it from the terminal?

---

### Post by Bucky Ball on 2015-11-26
Welcome. Do you mean 12.04 LTS? 12.10 is no longer supported, wasn't an LTS release (long term support) and if you're using that it might be the cause of your issues as you can not access the 12.10 repositories (to install anything, update, upgrade). If this is the case, upgrade to a supported release, 14.04 LTS or 15.10.

---

### Post by praveen_kumar3 on 2015-11-27
yes trying to build gvim installation on 12.04LTS.. but showing some packages not found..the error is listed in abouve thread..please help me?

---

### Post by deadflowr on 2015-11-27
Have you run a full system update yet?
(via the update manager)

---

### Post by praveen_kumar3 on 2015-11-27
Want to install gvim in ubuntu 12.04 LTS...

started doing in the following manner, but listing these issues..please help me how to fix it....

sudo apt-get install vim-gnome

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vim-gnome : Depends: libbonoboui2-0 (>= 2.15.1) but it is not going to be installed
             Depends: libgnome2-0 (>= 2.17.3) but it is not going to be installed
             Depends: libgnomeui-0 (>= 2.22.0) but it is not installable
             Depends: libruby1.8 (>= 1.8.7.352) but it is not going to be installed
             Depends: tcl8.5 (>= 8.5.0) but it is not installable
E: Unable to correct problems, you have held broken packages.

---

### Post by Bucky Ball on 2015-11-27
Help us help you by reading and responding to posts else you may end up going round in circles.

[QUOTE=deadflowr] Have you run a full system update yet?
(via the update manager)[/QUOTE]

:)

---

