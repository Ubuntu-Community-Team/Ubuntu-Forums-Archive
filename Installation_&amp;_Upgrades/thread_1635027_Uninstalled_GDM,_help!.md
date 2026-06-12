---
title: "Uninstalled GDM, help!"
date: 2010-12-01
forum: Installation &amp; Upgrades
---

### Post by Eneco on 2010-12-01
I have a problem, Some how I uninstalled the GDM now I can only start Ubuntu by going to into safemode and typing "startx" but I can only log into root and my resolution is messed up. I have been using Ubuntu for about two weeks now and this is the only problem I have uncounted so far... :confused:

Any help will be greatly appreiated. :)

---

### Post by sikander3786 on 2010-12-01
Try re-installing GDM.

```
sudo apt-get install gdm
```

---

### Post by Eneco on 2010-12-02
> **sikander3786 said:**
> Try re-installing GDM.

```
sudo apt-get install gdm
```


It says: 

```
root@travis-laptop:~# sudo apt-get install gdm
Reading package lists... Done
Building dependency tree       
Reading state information... Done
gdm is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 33 not upgraded.
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-i386_Packages)
W: Duplicate sources.list entry http://archive.canonical.com/ lucid/partner i386 Packages (/var/lib/apt/lists/archive.canonical.com_dists_lucid_partner_binary-i386_Packages)
W: You may want to run apt-get update to correct these problems
root@travis-laptop:~#
```

Even though it isn't installed, it says it is. Is there anyway to repair? Also I tried running "apt-get update" :frown:

---

### Post by garvinrick4 on 2010-12-02
The dupicate sources is not the problem just run this code and open source.list and put 
a comment sign (#) in front of one of the duplicate lines. (archive.canonical.com /lucid/partner)
```
gksudo gedit /etc/apt/sources.list
```
and then hit save.

Now the gdm or ubuntu-desktop or whatever you where fooling with and deleted sometimes will take out a lot of other packages or dependencies needed to run the
GUI (desktop)
You can try and install
```
sudo apt-get install ubuntu-desktop
``````
sudo apt-get install xorg
``````
sudo apt-get install gdm
``````
sudo dpkg --configure -a
``````
sudo apt-get update && sudo apt-get upgrade
```And then say a prayer, who really knows what has been removed from system.
Good luck partner.

---

### Post by garvinrick4 on 2010-12-02
I notice you were in root in previous install of gdm. Do not use sudo when in root.

---

### Post by Yougo on 2010-12-02
can you get to a command prompt login? if you then login with your own account and then use ```
sudo startx
``` you could atleast get to your own desktop session

---

### Post by Eneco on 2010-12-03
Okay I couldn't get it fixed this is what I did just to let you guys know.

I was running a multi-boot with windows 7 Ultimate and Ubuntu 10.10 I only have a Ubuntu 10.04 Live CD so I ran it and decided to decided to kill windows 7 and my Ubuntu 10.10 install. :-D

So I installed Ubuntu 10.04 and have only that I am going to be staying with Ubuntu and will make sure I won't mess up  my GDM again. ;)

I like Ubuntu it is much faster than Windows and overall better...

Annyway thanks guys for trying to help; see you on the forums. :guitar:

P.S: I love how easier it is to do a fresh install. ^_^

---

