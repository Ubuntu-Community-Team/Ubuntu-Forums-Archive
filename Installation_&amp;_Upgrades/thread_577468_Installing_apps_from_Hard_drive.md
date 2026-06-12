---
title: "Installing apps from Hard drive"
date: 2007-10-16
forum: Installation &amp; Upgrades
---

### Post by AlienTech on 2007-10-16
Hello, 

nOOb asking a nOObish questions. Here goes. I just installed Ubuntu a my PC at home (where I have no Internet) but I'm able to download the app's I want and desperately need (like ndiswrapper and updates) from work and transfer them to a cd-r or hdd. I don't know much about the terminal, but since I have no internet I can't use wget or wgetapp. Iis this idea possible? It seems silly that I have to ask but I been searching for an answer for over 2 weeks now. I'm normally pretty good about finding my answers. ANY AND ALL HELP is greatly appreciated. Is a .tar.gz file = to a Windows .exe file?



(SOLVED) [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)     Also, the information from epimeteo was extremely useful

---

### Post by PacketCollision on 2007-10-16
.tar.gz is an archive like .zip, double-clicking on it in gnome should launch the archive manager.  You can also type "tar zxf *filename*" from the commandline.  Once you have the files extracted, you should be able to follow the instructions included with it (you will probably be asked to run commands from the commandline).  Keep in mind though that you would be much better off getting a deb package (.deb) for the programs you need, which is the official install format of Ubuntu.

---

### Post by AlienTech on 2007-10-16
OK... let's say I have The .deb files, then how would i go about installing those from the hdd? Is .deb another format for compression like .zip or .tar? Do you know what the command should be in the terminal?

---

### Post by taurus on 2007-10-16
[http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

---

### Post by ruibernardo on 2007-10-16
If you have all the .deb files you could use dpkg to install them

```
sudo dpkg -i name_of_the_deb_file.deb

```
Please note that you might need other deb files (dependencies and other packages) to install one deb file. If you don't have all the dependencies packages, you will remain with a broken package and won't be able to install anything else until you resolve that.

To check what would happen if you try to install that package, type:

```
sudo dpkg --simulate -i name_of_the_deb_file.deb
```

If you get any errors, don't install it until you got them solved.

Another alternative (graphical) is gdebi. Just double click in the deb package in Nautilus.

---

### Post by AlienTech on 2007-10-16
> **taurus said:**
> [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

TY.... This looks EXTREMELY Helpful..... I'm going to try some of this right now. Please anyone who has anything to add do so.

---

### Post by AlienTech on 2007-10-16
The link and info left by the above individuals will answer both these questions..... Thank you guys for your help!!!!

---

