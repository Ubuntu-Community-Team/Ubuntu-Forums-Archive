---
title: "Help me with APTonCD. can't restore the packages"
date: 2012-05-03
forum: Installation &amp; Upgrades
---

### Post by vanangamudi on 2012-05-03
[SIZE=2]I hav installed so many packages through online. and I used APTonCD to backup those packages. but now can't restore them.  when click the load button in Restore window of APTonCD it throws errors into the console[[http://www.pasteall.org/pic/show.php?id=31246]](http://www.pasteall.org/pic/show.php?id=31246]).

[IMG]http://www.pasteall.org/pic/show.php?id=31246[/IMG]

 is there any way to add the backuped packages back to var/apt/cache and make ubuntu that the packages are there in. Last time APTonCD worked for me on Karmic Koala(9.10) 

Internet speed is very slow here. I can't download all again. help me out.
[/SIZE]

---

### Post by mips on 2012-05-04
I have no idea how aptoncd works but if you can see the .deb packages on the cd you can simply copy them to /etc/var/cache/archive as root and then change the permissions to 644 or -rw-r--r--

In a terminal go to the root of the cd and post the output of **ls -R** here in code tags or post it on [http://paste.ubuntu.com/](http://paste.ubuntu.com/) and provide a link. I want to see the folder structure & contents of the cd/dvd.

---

### Post by DWade on 2012-05-29
Nice quick fix, but does not correct the APTonCD error of not loading an ISO or reading the APTonCD  CD in the DVD drive.

So if anybody knows of a fix.  Please post it.  -- If no fix APTonCD need to be repaired and the repositories replace with the repaired program.

And as usual nobody in Ubuntu main who develops the programing; ever loads or sets up to load into Ubuntu dpkg-dev. always have to load it so I don't get errors in apt-get...

So.. all of the packages for APTonCD are in the archive directory,
sudo apt-get source aptoncd --- processes correctly
sudo apt-get update         --- processes correctly
sudo apt-get install aptoncd -- processes correctly no new files to be installed.
Since I remove 11.10 and restored 10.04 I can not speak if APTonCD worked in 11.10 or not, but it does in 10.04

Tried to load a ISO Load button does nothing...

---

### Post by mungatsuma on 2012-08-14
Just install hal then restart APTonCD with this code

```
sudo apt-get install hal
```

---

### Post by phoenixzee on 2012-09-04
Worked just fine.

---

