---
title: "Waiting For Update Manager"
date: 2012-05-10
forum: Installation &amp; Upgrades
---

### Post by AlexNagy on 2012-05-10
I've set my update manager to only show me LTS upgrades as I'm going to check out 12.04LTS (to see if I want to stick with Ubuntu or not) vs. the regular update path. Do I have to wait until July (for 12.04.1) as with the 10.04LTS users to use update manager? Seems silly to me. I'm using 11.10 fwiw.

---

### Post by darkod on 2012-05-10
No, the wait until the .1 release is only for systems running 10.04 LTS. With 11.10 you should get prompted for the upgrade.

Did you make sure you have all updates installed? It needs to be fully updated first.

You can also see what this command in terminal will do:
sudo update-manager -d

It should open the Update Manager, see if it offers the upgrade to 12.04 LTS.

It's best to check 12.04 in live mode first, just to make sure it has some issues with your hardware.

---

### Post by AlexNagy on 2012-05-11
I did and all hardware seems to work, I should be fully updated but I will run that command any way

Edit: the result is as follows:
[http://www.flickr.com/photos/38205303@N08/7177068854/in/photostream/](http://www.flickr.com/photos/38205303@N08/7177068854/in/photostream/)

this has been typical since release. I have my updater set to check daily (when I'm connected) for updates and to display them immediately.

---

### Post by AlexNagy on 2012-05-19
bump, ideas anyone?

---

### Post by darkod on 2012-05-19
What if you try something like:
sudo apt-get dist-upgrade

By the looks on that screenshot, to the right, you are running 3.0.0 which is 11.10, not 12.04.

Also, not sure if there are any broken packages blocking the upgrade option to show. You can also try:
sudo dpkg --configure -a

---

### Post by AlexNagy on 2012-05-19
> **darkod said:**
> What if you try something like:
sudo apt-get dist-upgrade

will give it a go

> By the looks on that screenshot, to the right, you are running 3.0.0 which is 11.10, not 12.04.11.10 is what I said from the start

> Also, not sure if there are any broken packages blocking the upgrade option to show. You can also try:
sudo dpkg --configure -awill run that first

*****@carla-laptop:~# sudo dpkg --configure -a
*****@carla-laptop:~# sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
*****@carla-laptop:~#

---

### Post by darkod on 2012-05-19
OK, if you open update manager after that, does it have option for 12.04?

Another idea is, change the setting from Long Term releases to normal releases. I know 12.04 is LTS, but since it's also the next release after 11.10, it should come up even if normal releases is selected.

After changing the setting search for updates and see if the upgrade to 12.04 comes up.

---

### Post by AlexNagy on 2012-05-23
that did it

---

