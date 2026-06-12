---
title: "Upgrade to Ubuntu 9.10 64bit"
date: 2010-02-15
forum: Installation &amp; Upgrades
---

### Post by MrWylbur on 2010-02-15
Over the last 6 months I have installed Ubuntu and upgraded to 9.10.  Today I installed a new AMD 64 x2 processor in my machine, and would like to move to the 64bit version of Ubuntu.  What are my options?  

It looks like there is no migration path in the installers.  

If I have to do a clean install, will I have to reinstall everything?  

Is there a way to find out all the packages I have installed? 

How about all the custom stuff like the Lamp, host files, etc?  

I am getting pretty comfortable with details, but I need the big picture on this one.  Thanks!

---

### Post by mikewhatever on 2010-02-15
You have to reinstall. To get the list of all installed packages, use **dpkg -l**, or **dpkg -l > ~/Desktop/installed-packages.txt**. Backup whatever custom configurations you have.

---

