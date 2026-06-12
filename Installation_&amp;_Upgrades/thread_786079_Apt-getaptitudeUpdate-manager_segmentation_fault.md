---
title: "Apt-get/aptitude/Update-manager segmentation fault"
date: 2008-05-07
forum: Installation &amp; Upgrades
---

### Post by mrcorey on 2008-05-07
Hi.  I took the plunge and "upgraded" from Gutsy to Hardy and all seemed to go fine, after about 9 hours of upgrading...so I thought.

Now, anything apt won't work as it should.  If updates are available, update manager, apt-get or aptitude will find the upgrades and fetch them for me, but when its time to install, it breaks with a segmentation fault.  Here's what I mean using apt-get:
```
me@mybox:~$ sudo apt-get dist-upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Calculating upgrade... Done
The following packages will be upgraded:
  gnome-about gnome-desktop-data gnome-system-monitor
  kcontrol kdebase-bin kdebase-bin-kde3 kdebase-data
  kdebase-kio-plugins kdesktop kfind kicker konqueror
  konqueror-nsplugins libglib2.0-0 libgnome-desktop-2
  libkonq4
16 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 24.1MB of archives.
After this operation, 0B of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gulus.usherbrooke.ca hardy-proposed/main gnome-about 1:2.22.1-0ubuntu6.2 [159kB]
Get:2 http://gulus.usherbrooke.ca hardy-proposed/main gnome-desktop-data 1:2.22.1-0ubuntu6.2 [574kB]
Get:3 http://gulus.usherbrooke.ca hardy-proposed/main libglib2.0-0 2.16.3-1ubuntu1 [752kB]
Get:4 http://gulus.usherbrooke.ca hardy-proposed/main gnome-system-monitor 2.22.1-0ubuntu2 [1481kB]
Get:5 http://gulus.usherbrooke.ca hardy-proposed/main kdebase-bin-kde3 4:3.5.9-0ubuntu7.2 [101kB]
Get:6 http://gulus.usherbrooke.ca hardy-proposed/main konqueror 4:3.5.9-0ubuntu7.2 [1967kB]
Get:7 http://gulus.usherbrooke.ca hardy-proposed/main kdesktop 4:3.5.9-0ubuntu7.2 [749kB]
Get:8 http://gulus.usherbrooke.ca hardy-proposed/main kdebase-bin 4:3.5.9-0ubuntu7.2 [1229kB]
Get:9 http://gulus.usherbrooke.ca hardy-proposed/main libkonq4 4:3.5.9-0ubuntu7.2 [287kB]
Get:10 http://gulus.usherbrooke.ca hardy-proposed/main kdebase-kio-plugins 4:3.5.9-0ubuntu7.2 [2046kB]
Get:11 http://gulus.usherbrooke.ca hardy-proposed/main kfind 4:3.5.9-0ubuntu7.2 [175kB]
Get:12 http://gulus.usherbrooke.ca hardy-proposed/main konqueror-nsplugins 4:3.5.9-0ubuntu7.2 [178kB]
Get:13 http://gulus.usherbrooke.ca hardy-proposed/main kdebase-data 4:3.5.9-0ubuntu7.2 [9436kB]
Get:14 http://gulus.usherbrooke.ca hardy-proposed/main kicker 4:3.5.9-0ubuntu7.2 [1986kB]
Get:15 http://gulus.usherbrooke.ca hardy-proposed/main kcontrol 4:3.5.9-0ubuntu7.2 [2909kB]
Get:16 http://gulus.usherbrooke.ca hardy-proposed/main libgnome-desktop-2 1:2.22.1-0ubuntu6.2 [94.3kB]
Fetched 24.1MB in 2min32s (159kB/s)                         
Segmentation fault
me@mybox:~$
```
It doesn't matter if I upgrade, install, autoclean, clean, remove.  All commands result in a segfault without any other indication of why.  Update manager just shows the "installing" box for a second and then recalculates, showing everything still ready to install (which prompted me to try apt-get only).

dpkg works, though.  I can install the files with dpkg from the /var/cache/apt/archives directory, but its a pain when you have several to do and you don't know which depends on what.

This is not a problem that can be solved by wiping out the .bin files in the /var/cache/apt directory.  I've tried it several times.  That fixes something else.

Has anybody got a solution that will work?

---

### Post by mrcorey on 2008-05-09
Is there anything that I can provide to help solve this? Any takers?

---

### Post by mrcorey on 2008-05-17
It seems that this is an unsolvable problem.  Oh well.  I've reinstalled the operating system, which is NOT the way to solve a problem, but I cannot figuure it out and cannot wait any longer for anyone to chime in with an answer.

PLEASE, anyone who has experienced this problem and solved it, could you post your experience so that someone else can solve theirs.

---

### Post by Arthur Archnix on 2008-05-26
Whatever it is, i've been hit by it too I think. I was apt-get dist-upgrade, and packages were being downloaded, then I lost my internet connection and after that I couldn't sudo anything. Even sudo fdisk -l results in "segmentation fault".

I also tried removing files in /var/cache, var/apt/cache, /tmp, /lost+found to no good effect. I reinstalled sudo with no effect. The only error message that I can produce to help is this, which appears in dmesg:
  	 	 	 	 	 	  > sudo[5357]: segfault at bf380a74 eip b7ea8b79 esp bf380a58 error  
 
Not sure what to say or do at this point. I'm on my working gutsy install now.

---

