---
title: "No repositories?"
date: 2007-01-07
forum: Installation &amp; Upgrades
---

### Post by clownius on 2007-01-07
I just spent some time installing Kubuntu dapper on a mates computer for them.  obviously everything usually works.  In this case when i went to adept expecting it was time to do a nice big update.  When i opened adept the only packages listed there were the installed packages.  Not a single package available to install. I tried a fetch updates and it didn't seem to even try to update from the repositories.  Now the machine works fine web browsing and stuff so i know the network is ok but its cant seem to find updates.
I did notice during install it couldn't find the mirrors but i passed that off to myself as the network not being setup correctly.  Does anyone know what could cause this? Should i try for another install?  the same also happened to someone else who i have convinced to install Kubuntu but ive installed at least 6 or 7 times on my own computers without this problem.
Is there a particular port that the Router may be blocking?
Are the mirrors just plain offline?
Id really like to solve this problem as im trying to convince them to convert to Linux and they loved the look on Kubuntu but not being able to install FF etc for them means they are less able to explore their new systems.

---

### Post by Rippey on 2007-01-07
have you checked if the repositories are listed in /etc/apt/sources.list? 
(cat /etc/apt/sources.list)
if there not there you can add them manualy by going to [_this_]("http://www.ubuntu-nl.org/source-o-matic/") page.
you can generate a source list there and paste in to sources.list.
sudo gedit /etc/apt/sources.list then paste the output from mentioned site.

---

### Post by clownius on 2007-01-07
Thanks for the quick reply.  This makes sense it would be the issue as it doesn't seem to look for anything when you fetch updates. Why didn't i think of this lol.
Ill report back if it works but its early AM here so might not get it looked at till tomorrow.

---

### Post by Koybe on 2007-01-07
What happend when you try to :
```
sudo apt-get update
```

---

### Post by teaker1s on 2007-01-07
can also be
repositories down

or

ubuntu having trouble resolving DNS
I had this-firefox worked,synaptic and apt get would not
to resolve set static ip and your ISP DNS ip

---

### Post by clownius on 2007-01-07
Ill get them to try the sources list idea first as i didn't see it attempt to download a package list at all.  If that doesn't work ill try the network side of things.  I think i tried one on a static IP already but not 100% shure.

---

### Post by clownius on 2007-01-07
Thank you everyone for your help.  Problem solved.  For some reason the sources list was missing from the install.  Add one and i have a very happy new Linux user.

Is there a way to have this marked as solved lol

---

### Post by Koybe on 2007-01-07
Just edit the first post and change the title by adding [RESOLVED] in front ;)

---

### Post by teaker1s on 2007-01-07
edit your first post, think you will find tick box to say resolved

---

