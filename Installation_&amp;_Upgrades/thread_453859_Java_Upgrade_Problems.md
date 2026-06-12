---
title: "Java Upgrade Problems"
date: 2007-05-24
forum: Installation &amp; Upgrades
---

### Post by oneadvent on 2007-05-24
I am trying to install Java jre on my laptop.

I  am getting an error that

```
rsmith@rsmith-laptop:~$ sudo aptitude install sun-java6-bin sun-java6-plugin sun-java6-font
Password:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
Couldn't find any package whose name or description matched "sun-java6-bin"
Couldn't find any package whose name or description matched "sun-java6-plugin"
Couldn't find any package whose name or description matched "sun-java6-font"
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

```

I tried to download it from the website, and it still does not work in FIreFox. 

Any ideas?

---

### Post by rondackcpu on 2007-05-26
You might be trying to do it the hard way.  Have you looked in Synaptic Package Manager's list for sun-java related packages?  Simple enough, choose   System, Administration, Synaptic (enter password when asked), scroll down to the sun-java section, choose the plugin you want, mark for installation, accept dependencies (you'll get the whole thing), apply, accept again, accept license, and it's automatic.

CRS

---

### Post by oneadvent on 2007-05-27
For some reason, it never did list in the software manager. I ended up finding a thread that worked. I unblocked all the "universal" sources, and used aptitude to get it downloaded and installed.

What a headache.

Now my vpn wont work at all.... I will have to post about this. 

My desktop did not have this much trouble. I wonder what the difference is.

---

