---
title: "Replace Windows for Ubuntu"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by eddy147 on 2008-11-23
I have 2 partitions: a C drive with windows installed and a D drive with all my data.
I want to install Ubuntu on my C drive (and herefore wipe C: clean)
but in the installation step "Prepare disk space" I dont know what to choose (of the four options), and I do not know how C-drive and D-drive are to be recognized during this installation process.
Also, my keyboard doesnt work during the installation, the mouse does.
Can somebody help me?

---

### Post by oilchangeguy on 2008-11-23
> **eddy147 said:**
> I have 2 partitions: a C drive with windows installed and a D drive with all my data.
I want to install Ubuntu on my C drive (and herefore wipe C: clean)
but in the installation step "Prepare disk space" I dont know what to choose (of the four options), and I do not know how C-drive and D-drive are to be recognized during this installation process.
Also, my keyboard doesnt work during the installation, the mouse does.
Can somebody help me?

this may help:
[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)
also try entering the bios, and enable usb legacy support (if you have a usb keyboard)
also i'd keep windows, "just in case" or at least until you get used to ubuntu.

---

### Post by steveneddy on 2008-11-23
Linux will label them

```
hda1, hda2, etc
```

meaning

[B]hard drive "a" first partition

hard drive "a" second partition[/B]

and if you have two hard drives they will be

```
hdb1
```

for hard drive "b" first partition, etc

if you know the physical size in Gigs of each drive it will also give you a clue as to which one is which.

hda1 is probably the "C:" drive for you.

Try this link to help you understand it further:

[http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)

there are many links on that page to help you and I decided to give you the main page instead of picking one for you so you can see all of the choices available from this one resource.

Check out the links in my sig for further information.

---

### Post by vigya on 2008-11-23
during the partitioning step of installation, u can guess which drive is c or d, by d disk space. it shows the size of partition..

if both are of the same size, then u can remove the c partition in the os u r curently using.
for windows, go to the default disk management tool
i.e
right click on my computer>manage>disk management(from d left panel)

it will show u all ur drives.
now right click on ur c drive and select, 'remove this partition'.
it would remove that drive and show dat disk space as unallocated.

d same space would again show as unallocated when u install ubuntu. dere, create a new partition and install ext3 file system in it.


>>if u have problems deleting the c partition, coz it is marked active and windows boots from it, then right click on the d partition, and mark it as active..

try it out and let me know.

---

### Post by WhyZeeGuy on 2008-11-23
This may not be the technically correct way to handle this but when faced with the same issue I boot my windows XP CD, deleted the C partition and exited the XP installation.  Loaded the Ubuntu CD and hit the reset button and took all the defaults.  Everything worked perfectly and any remnants of Windows was gone.

Later I installed Sun's VirtualBox and installed XP virtual system for some desperately need apps and fun.

---

### Post by oilchangeguy on 2008-11-23
> **vigya said:**
> during the partitioning step of installation, u can guess which drive is c or d, by d disk space. it shows the size of partition..

if both are of the same size, then u can remove the c partition in the os u r curently using.
for windows, go to the default disk management tool
i.e
right click on my computer>manage>disk management(from d left panel)

it will show u all ur drives.
now right click on ur c drive and select, 'remove this partition'.
it would remove that drive and show dat disk space as unallocated.

d same space would again show as unallocated when u install ubuntu. dere, create a new partition and install ext3 file system in it.


>>if u have problems deleting the c partition, coz it is marked active and windows boots from it, then right click on the d partition, and mark it as active..

try it out and let me know.

Please spell all words. u, and ur, d, dere, and coz are NOT words! Not everybody who uses this forum speaks english as their first language. And therefore may not understand your use of slang. And this is a forum! Not a chat room. Confine your use of chat slang to chat rooms!!

---

### Post by vigya on 2008-11-25
allright. sorry.
i'll keep that in mind.

---

