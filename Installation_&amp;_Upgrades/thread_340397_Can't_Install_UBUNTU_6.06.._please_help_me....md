---
title: "Can't Install UBUNTU 6.06.. please help me..."
date: 2007-01-17
forum: Installation &amp; Upgrades
---

### Post by davitru on 2007-01-17
When i try to install this Linux from live CD... it said that No root file system ,,, Im using SATA hard drive...

All of my config and error is the same as here...


[http://72.14.235.104/search?q=cache:teNB5gyNqdUJ:clau.sparetimegroup.net/index.php/tech/ubuntu-610-installation-no-root-filesystem-error/+No+root+file+system&hl=vi&gl=vn&ct=clnk&cd=5&client=firefox](http://72.14.235.104/search?q=cache:teNB5gyNqdUJ:clau.sparetimegroup.net/index.php/tech/ubuntu-610-installation-no-root-filesystem-error/+No+root+file+system&hl=vi&gl=vn&ct=clnk&cd=5&client=firefox)

...But when i try to use the intructions... 

They said that "

[B]I quickly scoured through Ubuntu Forums and found the following solution:
Before you start the installer, hit Alt+F2 and type in

sudo gedit /usr/lib/ubiquity/ubiquity/validation.py

Gedit should start with that file open. Scroll all the way down to the bottom, and look for the next to last if statement there:

if not root:
result.add(MOUNTPOINT_NOROOT)
Change it into:
if not root:
pass
[/B]

But when i open that file .. it's not have that file there... this is the picture

[IMG]http://i44.photobucket.com/albums/f31/davitru/Screenshot-1.png[/IMG]

[http://i44.photobucket.com/albums/f31/davitru/Screenshot-1.png](http://i44.photobucket.com/albums/f31/davitru/Screenshot-1.png)


Please anyone tell me why ?// im using 6.06 version

---

### Post by wpshooter on 2007-01-17
First, have you checked the integrity of your CD by running the verification function found on the initial Ubuntu boot screen menu ?

Have you ran the memtest found on that same menu ?

Did you burn your CD at 4X or less ?

Do you have any other O/Ss already on this drive ?

---

