---
title: "Upgrade problem."
date: 2012-11-16
forum: Installation &amp; Upgrades
---

### Post by dlw on 2012-11-16
If I'm in the wrong forum, I apologize.

I keep getting a red triangle in the upper right hand corner of the screen.
Clicking on it says there is an upgrade problem.
Clicking on 'Check for updates' gives the following error.

W:Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/main/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, W:Failed to fetch cdrom://Ubuntu 12.04.1 LTS _Precise Pangolin_ - Release i386 (20120817.3)/dists/precise/restricted/binary-i386/Packages  Please use apt-cdrom to make this CD-ROM recognized by APT. apt-get update cannot be used to add new CD-ROMs
, E:Some index files failed to download. They have been ignored, or old ones used instead.

How do I solve this?
TIA

dlw

---

### Post by Mr_JMM on 2012-11-16
Unless you specifically want to use the installation DVD for something, remove it from the list of software sources.

You can do this directly from the Software Sources app or find it under "Edit" in Software Manager.

---

### Post by NikTh on 2012-11-16
Hi , 

please follow the instructions to resolve your problem.

Open a terminal (CTRL+ALT+T keys combo) and write 
```
gksudo gedit /etc/apt/sources.list
```At the opened window , search and find any line (search in the begin of the file , I think they are the first 3 lines) begins with this
```
**deb cdrom:**[Ubuntu 12.04.1 LTS _Precise Pangolin_
```and make them like this 
```
# deb cdrom:[Ubuntu 12.04.1 LTS _Precise Pangolin_
```add this symbol at the begin of each line # 

save the file and run in terminal 
```
sudo apt-get update
sudo apt-get dist-upgrade
```Thanks

---

### Post by dlw on 2012-11-16
Thank you.
The red triangle is gone.
I'm not sure what that means, but, it's gone.

Thanks again,
dlw

---

