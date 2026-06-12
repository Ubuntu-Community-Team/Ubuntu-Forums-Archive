---
title: "Upgrading 11.10 to 12.04, many problems along the way"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by ajohnson2371 on 2012-04-27
First off, laptop specs:
HP Pavilion zv5000. Took 11.10 without issue.
Processor = Intel Pentium 4, 3GHz
RAM = 640MB originally, upgraded to 2GB. Pretty zippy now.
HDD = 80GB, 20GB free space


First try, online update through Update Manager.
Received following error:

An unresolvable problem occurred while calculating the upgrade: 
E:Unable to correct problems, you have held broken packages. 

This can be caused by: 
* Upgrading to a pre-release version of Ubuntu 
* Running the current pre-release version of Ubuntu 
* Unofficial software packages not provided by Ubuntu 

If none of this applies, then please report this bug using the 
command 'ubuntu-bug update-manager' in a terminal. 

Tried through a terminal window, just in case -- same error.



I then did the following:
sudo apt-get clean
sudo apt-get update
sudo apt-get upgrade

All came back clean, nothing broken.

Ran the 12.04 upgrade again, same error.



Tried the Live CD option where I could overlay 12.04 on top of 11.10 and keep my files.
The CD option wouldn't even let me select it -- I could choose to install it aside 11.10 and choose at boot, or do a fresh install...


I'm in my second day of attempting to upgrade, and still getting nowhere.
I'm about at the point on doing a clean install, as I have cloned my laptop onto a portable USB drive...
I would just hate to spend the time reinstalling all those apps...

Anyone else encountering this issue, particularly with the Live CD install, trying to upgrade via CD with the overlay option?


Any thoughts, suggestions would be welcome

---

### Post by ajohnson2371 on 2012-04-27
Did a little research on the Live CD issue. Apparently, for whatever reason, you can select the option to install 12.04 on top of the 11.10 installation when you're connected to the internet.
Not a problem, typically, but my Broadcomm wireless adapter doesn't work under the Live CD.
So I had to wait until I got home, and ran a long Cat5 cable to my router. Now I have the option to upgrade using the Live CD.

Updates as they happen.

---

