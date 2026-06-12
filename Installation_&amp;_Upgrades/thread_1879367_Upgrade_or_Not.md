---
title: "Upgrade or Not?"
date: 2011-11-11
forum: Installation &amp; Upgrades
---

### Post by Robert the Kat on 2011-11-11
On one desktop I have Ubuntu 10.10 installed. I have several programs that I use often. Each time at start up I am asked if I want to upgrade to Natty-Narwhal. I have looked over this version and it looks great. My question would be if I do upgrade does that mean other programs I have installed are over written and not available or they just will not work with the upgrade?

---

### Post by Hakunka-Matata on 2011-11-11
Probably a combination of the two possibilities you pose.  There have been so many threads about screwed-up, failed upgrades to oneiric-11.10 I've been afraid to use upgrades forever.  
Now, just recently someone posted a reason and solution, which I haven't tried yet.

[LIST]
[*]**Upgrade Successfully to 11.10, oneiric:**
[LIST]
[*]add oneiric repositories to software sources before attempting upgrade.
[/LIST]
 
[*]your programs should be preserved, that does not guarantee your programs/apps will all work correctly with a new Release, some will have dependencies that may have problems at first.
[*]Why not just "Try it" w/o upgrading, i.e. install it to a separate new partition, with a /home directory.  Preserving your current OS.
[/LIST]

---

### Post by Hakunka-Matata on 2011-11-11
**Oneiric repos open!**             
                                                                The development cycle is uninterrupted!

```
sudo sed -i 's/natty/oneiric/g' /etc/apt/sources.list
sudo aptitude update
sudo aptitude dist-upgrade

```
(You might want to save the natty-updates, natty-backports, natty-security, and natty-proposed repo lines in sources.list)

eric@kingfisher:~/Downloads$ cat /etc/lsb-release 
DISTRIB_ID=Ubuntu
DISTRIB_RELEASE=11.10
DISTRIB_CODENAME=oneiric
DISTRIB_DESCRIPTION="Ubuntu oneiric (development branch)"
                                                                                                                                    *                                              Last edited by Starks; April 28th, 2011 at 09:10 PM..                                                           *

---

### Post by Robert the Kat on 2011-11-11
Interesting.  Thanks for the information.

---

