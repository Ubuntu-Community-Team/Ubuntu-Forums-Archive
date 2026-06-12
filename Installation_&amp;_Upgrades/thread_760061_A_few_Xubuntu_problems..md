---
title: "A few Xubuntu problems."
date: 2008-04-19
forum: Installation &amp; Upgrades
---

### Post by nerd0795 on 2008-04-19
I just signed up.  please forgive me if i put this question in the wrong spot.


Yesterday, I fixed my old computer and put Xubuntu on it because it a Windows ME computer.  The Installation was good.  I got it working but everytime I try to install an app using add/remove it keeps on saying

"The list of applications is not availabe

Click on 'Reload' to load it. To reload the list you need a working internet connection

Refresh  Cancel"

I press refresh then it says Downloading i try to put the check mark by the program I want and it says it again...

I tried many times.

how do I fix this?

Also how do you install kiba dock I'm confused and it's not working!

How do you install kiba dock for xubuntu and get add/remove to work?

I am admin.

---

### Post by NightwishFan on 2008-04-19
Check your software sources, you may not have them enabled. I am not sure exactly how to in Xubuntu though. Also post the output of:
```
sudo apt-get update
```

---

### Post by nerd0795 on 2008-04-19
```

Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/main Translation-en_CA
Ign cdrom://Xubuntu 7.10 _Gutsy Gibbon_ - Release i386 (20071016) gutsy/restricted Translation-en_CA
Reading package lists... Done

```
I entered the code you said and got this...

---

### Post by NightwishFan on 2008-04-19
It is set up to install packages from the cd, rather than the internet. I will try to find how to edit sources.
EDIT: I believe there should be a "Software Sources" front end. Try to find one It might possibly be in the menu near Synaptic Package Manager.

---

### Post by nerd0795 on 2008-04-19
I found it and I'm in software sources.  Do I say find Third Party software from (a long website url) ?

---

### Post by nerd0795 on 2008-04-19
I did it and yay add/remove works now!!! yay now I can enjoy more software:popcorn:.  Thank you!!!!

---

### Post by NightwishFan on 2008-04-19
Ok when you are in software sources in the first tab, unmark the "installable from cd-rom/dvd" at the bottom. Then check the 4 under "downloadable from the internet".

In Updates make sure "important security updates" and "Recommend Updates" are checked. If you cant see something I point out post a screen shot of it for me.

EDIT: Nvm cool. Glad to help.

---

### Post by nerd0795 on 2008-04-19
YAY 122 UPDATES :lolflag:

---

### Post by NightwishFan on 2008-04-19
:)

---

