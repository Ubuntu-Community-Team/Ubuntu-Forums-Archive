---
title: "&quot;Package system broken&quot; error. Unmet dependencies."
date: 2012-09-14
forum: Installation &amp; Upgrades
---

### Post by Kilted on 2012-09-14
When I open up my software center, it asks me to repair my package system. When i do so, it returns with the error "package operation failed. The installation or removal of a package failed" the details show this: 

installArchives() failed: dpkg: dependency problems prevent configuration of python-glade2: 
 python-glade2 depends on python (<< 2.6); however: 
  Version of python on system is 2.7.3-0ubuntu2. 
 python-glade2 depends on python-gtk2 (= 2.12.1-0ubuntu1); however: 
  Version of python-gtk2 on system is 2.24.0-3. 
 python-glade2 depends on python-support (>= 0.7.1); however: 
  Package python-support is not installed. 
dpkg: error processing python-glade2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ndisgtk: 
 ndisgtk depends on python-glade2; however: 
  Package python-glade2 is not configured yet. 
dpkg: error processing ndisgtk (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because the error message indicates its a followup error from a previous failure.
No apport report written because the error message indicates its a followup error from a previous failure.
Errors were encountered while processing: 
 python-glade2 
 ndisgtk 
Error in function:  
dpkg: dependency problems prevent configuration of python-glade2: 
 python-glade2 depends on python (<< 2.6); however: 
  Version of python on system is 2.7.3-0ubuntu2. 
 python-glade2 depends on python-gtk2 (= 2.12.1-0ubuntu1); however: 
  Version of python-gtk2 on system is 2.24.0-3. 
 python-glade2 depends on python-support (>= 0.7.1); however: 
  Package python-support is not installed. 
dpkg: error processing python-glade2 (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of ndisgtk: 
 ndisgtk depends on python-glade2; however: 
  Package python-glade2 is not configured yet. 
dpkg: error processing ndisgtk (--configure): 
 dependency problems - leaving unconfigured 
 
If i try to install anything after that i get "Package system is broken" and the details show this:

python-glade2: Depends: libglade2-0 (>= 1:2.6.1) but 1:2.6.4-1ubuntu1.1 is installed
               Depends: libglib2.0-0 (>= 2.15.0) but 2.32.3-0ubuntu1 is installed
               Depends: python (< 2.6) but 2.7.3-0ubuntu2 is installed
               Depends: python-gtk2 (= 2.12.1-0ubuntu1) but 2.24.0-3 is installed
               Depends: python-support (>= 0.7.1) but it is not installed

I'm fairly new to ubuntu and i don't know what all of this means. How can i fix this problem?

---

### Post by jerrrys on 2012-09-14
[Open a terminal]("https://help.ubuntu.com/community/UsingTheTerminal#Starting_a_Terminal") and enter (one at a time):

sudo dpkg --configure -a 
sudo apt-get install -f
sudo apt-get update

Did that fix it or did you get some errors?

---

### Post by Kilted on 2012-09-14
after runnung sudo dpkg --configure -a I got:

dpkg: dependency problems prevent configuration of python-glade2:
 python-glade2 depends on python (<< 2.6); however:
  Version of python on system is 2.7.3-0ubuntu2.
 python-glade2 depends on python-gtk2 (= 2.12.1-0ubuntu1); however:
  Version of python-gtk2 on system is 2.24.0-3.
 python-glade2 depends on python-support (>= 0.7.1); however:
  Package python-support is not installed.
dpkg: error processing python-glade2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ndisgtk:
 ndisgtk depends on python-glade2; however:
  Package python-glade2 is not configured yet.
dpkg: error processing ndisgtk (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-glade2
 ndisgtk


after running sudo apt-get install -f  i got:

Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following extra packages will be installed:
  python-glade2
Suggested packages:
  python-gtk2-doc
The following packages will be upgraded:
  python-glade2
1 upgraded, 0 newly installed, 0 to remove and 14 not upgraded.
2 not fully installed or removed.
Need to get 0 B/9,870 B of archives.
After this operation, 31.7 kB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: dependency problems prevent configuration of python-glade2:
 python-glade2 depends on python (<< 2.6); however:
  Version of python on system is 2.7.3-0ubuntu2.
 python-glade2 depends on python-gtk2 (= 2.12.1-0ubuntu1); however:
  Version of python-gtk2 on system is 2.24.0-3.
 python-glade2 depends on python-support (>= 0.7.1); however:
  Package python-support is not installed.
dpkg: error processing python-glade2 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ndisgtk:
 ndisgtk depends on python-glade2; however:
  Package python-glade2 is not configured yet.No apport report written because MaxReports is reached already

dpkg: error processing ndisgtk (--configure):
 dependency problems - leaving unconfigured
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 python-glade2
 ndisgtk
E: Sub-process /usr/bin/dpkg returned an error code (1)

and after running sudo apt-get update i didnt get any errors but all of my updates in update manager are still there, waiting to be downoaded and installe. and my problem persists.

---

### Post by jerrrys on 2012-09-14
All your updates will be there until you do an upgrade.

sudo apt-get upgrade

And for ndisgtk, are you trying to use it?

[https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper](https://help.ubuntu.com/community/WifiDocs/Driver/Ndiswrapper)

---

### Post by Kilted on 2012-09-15
I've just decided to try a reinstall and see where that gets me. I'll update you when it's complete.

EDIT: Okay, did the reinstall and my package system is fixed. But now my wireless connection drops after a few minutes. I'll try updating and see if that fixes the problem. My wireless card has a linux driver which i've installed (No connection Whatsoever before i did that) so that's not the problem.

EDIT2: Updated, same problem, the wireless connection drops after a few minutes (although never while it was updating) and afterwords i get asked to authenticate my encryption every once and a while

---

### Post by jerrrys on 2012-09-15
Sorry, but I am not a wireless guy.  I would suggest starting a new thread in the wireless/networking sub-forum.

good luck

---

### Post by Kilted on 2012-09-15
I already have, thanks for your time and interest.

---

