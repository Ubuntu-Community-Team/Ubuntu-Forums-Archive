---
title: "Ubuntu Install for MythTV"
date: 2007-05-03
forum: Installation &amp; Upgrades
---

### Post by maeks84 on 2007-05-03
As per the guide at [https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend]("https://help.ubuntu.com/community/MythTV_Feisty_Backend_Frontend").  I installed Ubuntu from the alternate disk.  Apparently this doesn't install a full OS, with the menus, apps, and things as is on the LiveCD?  For my user 'eks', I want to be able use it with the menus.  Do I have to re-install from a regular disk or can I add the menus in without a full re-install?

---

### Post by newlinux on 2007-05-03
try:
```

sudo aptitude update
sudo aptitude install ubuntu-desktop

```

That should install the ubuntu-desktop. Then you will probably want to reboot.

---

### Post by maeks84 on 2007-05-03
Wow, that was much easier than I expected.  Took a little bit of time, but no problems at all.  Thanks newlinux!

---

### Post by newlinux on 2007-05-04
No problem. Yeah, it takes a while, but it has to install a lot of stuff :)

Happy ubuntuing and mything!

---

### Post by maeks84 on 2007-05-07
Just out of curiosity.
Could I uninstall the Ubuntu desktop with...
```
sudo aptitude remove ubuntu-desktop
sudo aptitude purge ubuntu-desktop
```
or would that cause other problems?  or would I just need the purge line?

---

### Post by newlinux on 2007-05-07
The purge one would get rid of configuration files as well as the packages. The remove would just get rid of the packages. So you would probably just want purge. It *shouldn't* screw up anything, but I make no guarantees :).

---

### Post by superm1 on 2007-05-07
Well actually it will only take out the metapackage.  You will have to remove the other ones manually, or possibly by apt-get autoremove

---

### Post by newlinux on 2007-05-07
> **superm1 said:**
> Well actually it will only take out the metapackage.  You will have to remove the other ones manually, or possibly by apt-get autoremove

Even if you used aptitude instead of apt-get to install it?

---

### Post by rsambuca on 2007-05-07
Apt-get has been improved and is now considered better than aptitude.

---

### Post by newlinux on 2007-05-07
> **rsambuca said:**
> Apt-get has been improved and is now considered better than aptitude.

I'm pretty sure aptitude would remove the dependencies for unused packages (that used to be its advantage over apt-get, assuming you installed with aptitude as well). So if apt-get is better it would too, I would assume, if it was installed with apt-get? What makes apt-get better now?

---

### Post by superm1 on 2007-05-07
Ever since I found out aptitude treats all suggestions for packages dependencies, I stopped using it.  

I'm pretty sure that this will handle what he needs to do, but if aptitude does it in one fail swoop - go for that:

```
apt-get remove --purge ubuntu-desktop
apt-get autoremove --purge
```

---

### Post by newlinux on 2007-05-07
Apparently both our methods would work:

[http://www.psychocats.net/ubuntu/purekde](http://www.psychocats.net/ubuntu/purekde)
[http://www.psychocats.net/ubuntu/aptitude](http://www.psychocats.net/ubuntu/aptitude)

---

### Post by maeks84 on 2007-05-07
Interesting discussion...  
I've never used Linux before a week or so ago and I've learned many things in that week.  It's quite fun to tinker with, although I don't think I want to use it as a main OS yet.  Once my MythTV box is working, I'll probably dual boot Ubuntu on my Mac though.  Thanks for the info all.

---

