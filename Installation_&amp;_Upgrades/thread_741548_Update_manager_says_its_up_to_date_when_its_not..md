---
title: "Update manager says its up to date when its not."
date: 2008-03-31
forum: Installation &amp; Upgrades
---

### Post by spacesearcher on 2008-03-31
I am reposting this here because I put it in beginner forums and I think I will get better help here.
I installed ubuntu 7.10 and whenever I go to update manager it says my system is up to date but I never have updated it since I installed it a couple of days ago. 

doing sudo apt-get update
and sudo apt-get upgrade I get this:

joe@joe-laptop:~$ sudo apt-get update
Get:1 [http://archive.canonical.com](http://archive.canonical.com) gutsy Release.gpg [191B]
Ign [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Translation-en_US
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release.gpg [191B]
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Translation-en_US
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy Release
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Translation-en_US
Ign [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Translation-en_US
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy Release
Hit [http://archive.canonical.com](http://archive.canonical.com) gutsy/partner Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/universe Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/restricted Packages
Hit [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/multiverse Packages
Fetched 2B in 0s (2B/s)
Reading package lists... Done
joe@joe-laptop:~$ sudo apt-get upgrade
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
joe@joe-laptop:~$


the repository settings in synaptic are
under Ubuntu software tab only main universe restricted and multiverse are selected.
under the third party software the first one is checked
and under updates only check for updates and "only notify about available updates" is checked. (should other things in here be checked?)

it still does not update it acts like its doing something but then never has any to download. this is like this in terminal synaptic and update manager.
The only thing I have installed is the restricted Nvidea driver.

Does anyone have a solution?

---

### Post by Pumalite on 2008-03-31
System>Administration>Software Sources Make sure all you repos are available (tick)
Reload
sudo aptitude update
sudo aptitude upgrade

---

### Post by spacesearcher on 2008-03-31
> **Pumalite said:**
> System>Administration>Software Sources Make sure all you repos are available (tick)
Reload
sudo aptitude update
sudo aptitude upgrade

main, universe, multiverse, and restricted are all ticked.

---

### Post by Pumalite on 2008-03-31
What about 'updates'?

---

### Post by spacesearcher on 2008-03-31
none are ticked under updates should they be?

---

### Post by Pumalite on 2008-03-31
What do you think?

---

### Post by spacesearcher on 2008-03-31
I think they should but would you recomend doing pre-released? or not

---

### Post by Pumalite on 2008-03-31
I have them all ticked, but I like to live dangerously. No problems so far.

---

### Post by spacesearcher on 2008-03-31
lol thanks its working now.

---

### Post by Pumalite on 2008-03-31
You are welcome. Good luck.

---

