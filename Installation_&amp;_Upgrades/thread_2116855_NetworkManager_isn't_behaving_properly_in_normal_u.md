---
title: "NetworkManager isn't behaving properly in normal user, but works well in root user."
date: 2013-02-16
forum: Installation &amp; Upgrades
---

### Post by NewUserFF on 2013-02-16
Hi, everyone. I'm using ubuntu 12.04, but I have replaced Unity with Mate(a fork of gnome2) by unistalling and installing lots of softwares. Everything seems fine, except the Network-Manager applet on the top panel. It just displays: 
```
NetworkManager is not running.
```

OK, I run the code in terminal:
```
sudo service network-manager start
```
, then I get the message: 
```
start: Job is already running: network-manager. 
```
Then I tried to restart:
```
sudo service network-manager restart. 
```
All right, something seems changed, 
```
network-manager stop/waiting, network-manager start/running, process 8955.
```
But NetworkManager still cannot manage wireless and wired connections. It told me:
```
No network devices are available.
```
But I'm sure that the network devices are running properly, for I am using wireless network to communicate with you! What's more, If I login Mate with root instead of normal user, I can use the NetworkManager-applet properly. Can anyone tell me what's the matter? 

P.S. I cannot find the option or button to shutdown in normal user, but when I login by root, I can easily find the option in top menu to shutdown. Can anyone tell me how to add the shutdown option in normal user? What's the name of that shutdown software in top menu? Thanks a lot!

---

### Post by ahallubuntu on 2013-02-16
~

---

### Post by NewUserFF on 2013-02-17
> **ahallubuntu said:**
> Out of curiosity, why did you go with Mate vs. Gnome Classic (that looks almost identical to Gnome 2)?  I've been quite happy with Gnome Classic and it took all of 60 seconds to install (by installing "Gnome Shell") in Ubuntu Software Center.  I don't care for Unity either; I haven't seen it since the day I installed Gnome Shell a month ago.

Some people do have reasons to prefer the old Gnome 2 environment vs. Gnome Classic in Gnome shell, I guess, but after using Ubuntu 10.04 for years, I'm quite happy with Gnome Classic.  I may move to Gnome 3 itself sooner or later, though.

In my view, Gnome Classic based on Gnome 3 is a little different with the real Gnome 2, which is displayed in many slight aspects. I still like the original Gnome 2. Maybe it's too many people like me that led to the project of Mate:p By the way, I have solved the problem by installing mdm(Mate Display Manager).

---

