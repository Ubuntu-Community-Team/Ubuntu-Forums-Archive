---
title: "apt-get no longer works!"
date: 2007-06-28
forum: Installation &amp; Upgrades
---

### Post by Mark Phelps on 2007-06-28
Yesterday, I installed kubuntu desktop and switched over to KDE to experiment with it for a while.  SMPlayer stopped working, so I downloaded several different .deb files and installed each in turn, trying to get it to work.  I gave up late last night.

Then today, after tweaking the video settings, I discovered how to fix smplayer, so I uninstalled it.  When I tried to reinstall it, apt-get failed, indicating it can't find the file.

So, I switched back to Gnome (where I know more about how to do things) and tried again, get the same error.  

ran apt-get update -- OK
ran apt-get upgrade -- OK
ran apt-get -f install -- no errors

even ran apt-get check on the deb package -- no errors

Tried several other deb packages, some of which I've installed before -- same results.

Example:
bill@bill-desktop-ubuntu:~$ ls *.deb
ntfs-3g_1.516-1_i386.deb  smplayer_0.5.21_i386.deb
bill@bill-desktop-ubuntu:~$ ls -l *.deb
-rwxrwx--- 1 bill bill  25908 2007-06-26 16:09 ntfs-3g_1.516-1_i386.deb
-rwxrwx--- 1 bill bill 951445 2007-06-28 00:05 smplayer_0.5.21_i386.deb
bill@bill-desktop-ubuntu:~$ sudo apt-get install smplayer*.deb
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package smplayer_0.5.21_i386.deb
bill@bill-desktop-ubuntu:~$ 

So, if apt-get can figure out the full filename, then how can it NOT find the package???

Don't know what to do now,  If I can't install anymore packages, then I'll have to go back to Windows (but I don't want do do that!!)

---

### Post by pingpongboss on 2007-06-28
for local deb files use ```
sudo dpkg -i <filename.deb>
```

---

### Post by benanzo on 2007-06-28
Use **dpkg** to install debs directly.

```
sudo dpkg -i package.deb
```

APT was really just designed to be the middleman between some GUI package manager like Synaptic and dpkg (which actually does all the work.)

---

### Post by Mark Phelps on 2007-06-29
Thanks for the feedback.  

I was confusing apt-get with dpkg and trying to get apt-get to use a specific instance of a .deb package for installation.  It took some digging into the apt-get tutorial to learn that it only uses packages from the repos, and, as you have both stated, dpkg must be used to specify a particular instance of a package.

Anyway,  I used apt-get to purge the installations I had corrupted, ran apt-get again (without filename entries), and the two package sets installed properly.

---

