---
title: "Just Installed Hearty Heron...Unable to Update It"
date: 2008-07-27
forum: Installation &amp; Upgrades
---

### Post by SunThief on 2008-07-27
When I try to update, I get an error message saying E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report.

What do I do?  I am completely new to Linux.

---

### Post by ad_267 on 2008-07-27
Go to applications - accessories - terminal.

Enter:
```
sudo dpkg --configure -a
```
press enter then enter your password. Nothing will appear on the screen when you enter your password but just type it in and then press enter.

This fixes up problems with the package information which sometimes happens when an update or package installation is interrupted.

---

### Post by Partyboi2 on 2008-07-27
Open a terminal (Applications>Accessories>Terminal) and type or paste
```
sudo dpkg --configure -a
```

---

### Post by SunThief on 2008-07-27
This is what happened after I did that.

You have 1 broken package on your system!

Use the "Broken" filter to locate it.

What do I do now?

---

### Post by ad_267 on 2008-07-27
Go to system - administration - synaptic package manager then click on Edit - Fix broken packages.

---

### Post by SunThief on 2008-07-27
It says it installed the updates, but I don't know how to find the broken file.

---

### Post by ad_267 on 2008-07-27
Sorry I'm not exactly sure how this works as I haven't had this problem before.

Are you saying that you clicked on Edit - Fix broken packages and then it downloaded and installed the packages? Then everything should be fixed I think. If it just marked packages for reinstallation you might have to click apply.

---

### Post by Partyboi2 on 2008-07-27
Open a terminal and type
```
sudo apt-get update
sudo apt-get upgrade
``` If you get no errors then you are ok.

If it says you have a broken package then type
```
 sudo apt-get -f install
``` to try and fix the broken package.

---

### Post by SunThief on 2008-07-27
Thanks.

---

