---
title: "problem upgrading debian packages"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by chuve on 2012-10-14
hello, well, i've got a little big problem over here, i cant upgrade any debian packages because theupdater returns me an error:

Reading database ... 90%%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'gnome-icon-theme-full': Input/output error
Error in function: 

can anyone help me please? i have 66 upgrades waiting and i cant do anything by now =/

---

### Post by g_s_patra on 2012-10-14
(1) terminal --> (a) sudo apt-get update, then (b) sudo apt-get install -f
(2) Synaptic --> (a) Reload (b) Mark All Upgrades (c) Apply
(3) Update

---

### Post by jrog on 2012-10-14
> **chuve said:**
> hello, well, i've got a little big problem over here, i cant upgrade any debian packages because theupdater returns me an error:

Reading database ... 90%%dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'gnome-icon-theme-full': Input/output error
Error in function: 

can anyone help me please? i have 66 upgrades waiting and i cant do anything by now =/
The post above mine is unlikely to solve this problem, I think, as it looks like there's something wrong with your files list. So, if the preceding commands don't work, try these commands at the terminal (CTRL + ALT +T):
```
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo mv /var/lib/dpkg/status /var/lib/dpkg/status-bad 
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status 
sudo mv /var/lib/dpkg/available /var/lib/dpkg/available-bad 
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available 
sudo rm -rf /var/lib/dpkg/updates/* 
sudo rm -rf /var/lib/apt/lists/* 
sudo mkdir /var/lib/apt/lists/partial 
sudo rm /var/cache/apt/*.bin 
sudo apt-get clean 
sudo apt-get autoremove 
sudo apt-get update 
sudo dpkg --configure -a 
sudo apt-get install -f
```Be careful to type them correctly, as the 'rm -rf' commands in particular could delete a lot of stuff if you make a typo. It might be a good idea just to copy and paste them.

If even this doesn't work, you can find a more extensive list of commands to try at the following link: [https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure](https://help.ubuntu.com/community/PackageManagerTroubleshootingProcedure). I think the commands above should be (more than) enough, though.

---

### Post by chuve on 2012-10-14
sorry, that didnt work either =/ ill check the thread you left me.... also, do you think it could be fixed instaling(or updating) to the upcoming version of ubuntu? i've heard that its coming in a few days or so...

---

### Post by jrog on 2012-10-14
> **chuve said:**
> sorry, that didnt work either =/ ill check the thread you left me.... also, do you think it could be fixed instaling(or updating) to the upcoming version of ubuntu? i've heard that its coming in a few days or so...
Installing from scratch would fix the problem, though it would be a drastic solution. You probably wouldn't be able to update with your package manager in this state.

At this point, can you paste a more complete error message? What you pasted in the first post is partial, and additional details may help.

---

