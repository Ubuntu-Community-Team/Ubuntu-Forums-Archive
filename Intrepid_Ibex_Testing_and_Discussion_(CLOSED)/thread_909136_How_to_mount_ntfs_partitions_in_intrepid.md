---
title: "How to mount ntfs partitions in intrepid?"
date: 2008-09-03
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by hardhu on 2008-09-03
Dolphin shows my two ntfs partitions on disk in places both as Volume(ntfs), but when I click on them nothing happens.
I looked in System Preferences -> Advanced for something related to Disk and Filesystems, but I couldn't find anything. Am I missing some packages?

---

### Post by ronacc on 2008-09-03
have a look at system>administration>authorizations>freedesktop>hal>storage  and change mount file systems from internal drives to yes , I don't know if ths will work for ntfs but it does let you mount other linux drives .

---

### Post by jbernardo on 2008-09-03
Check bugs [162863 ]("https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/162863")and [205081]("https://bugs.launchpad.net/ubuntu/+source/ntfs-3g/+bug/205081"), as they might be related.

---

### Post by hardhu on 2008-09-10
> **ronacc said:**
> have a look at system>administration>authorizations>freedesktop>hal>storage  and change mount file systems from internal drives to yes , I don't know if ths will work for ntfs but it does let you mount other linux drives .

I don't have this on kde 4, so I cannot test.

From what I have googled around, it seems that my problem is (at least partially), related to this bug:

[https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/255236](https://bugs.launchpad.net/ubuntu/+source/kubuntu-default-settings/+bug/255236)

Nobody else is complaining about it?

---

### Post by awakatanka on 2008-09-10
On kubuntu alpha 5 and don't have that problem. it mounts my ntfs drive without problems

---

### Post by linomac on 2008-10-11
i have the same problem

---

### Post by Delvien on 2008-10-11
You could do it via fstab...

First type "mount" into a terminal, and then you should see your hard drive (note: you should have your drive mounted already, or if not, know your /dev/HDD#)

```
 sudo mkdir /media/THENAMEOFYOURFOLDER 
```

```
 sudo gedit /etc/fstab 
```

My entry looks like this, insert your drive information "/dev/HDA OR SDA#"

```
 /dev/sda2 /media/2nd ntfs users,defaults,umask=000 0 0 
```

---

### Post by kansasnoob on 2008-10-11
With ntfsprogs installed I can mount any of my ntfs partitions or drives:

[http://www.linux-ntfs.org/doku.php](http://www.linux-ntfs.org/doku.php)

It's in the repos so you can either install from synaptic or:

```
sudo apt-get install ntfsprogs
```

I've also been told that ntfs-config works well, I just chose to use ntfsprogs and I'm used to it. ntfs-config is also in the repos.

Just a brief word of warning - both of these programs allow read & write support so you can potentially damage files necessary for Win to run properly!

---

### Post by TWO on 2008-10-14
The only way I've managed to do this so far is to run ```
sudo dolphin
``` in Konsole. Then and only then am I able to access the other partitions for the rest of the session. External memory such as memory sticks still seem to be a no go at the moment. 
Running ```
kdesudo dolphin
``` doesn't allow me to access any partitions in the Dolphin window that pops up, however if I open up another instance of Dolphin via the same menu at the same time, that window can then access all partitions. 

Running ```
kdesu Dolphin
``` doesn't work at all. ```
kdesu
``` was the command I had used for graphical sudo right up until Kubuntu Hardy Heron but it doesn't seem to work under KDE 4 for anything.

This bug [#269615]("https://bugs.launchpad.net/ubuntu/+source/kde4libs/+bug/269615") seems to be the main one concerning this problem at the moment, and there are a couple of duplicates which have been linked to this bug too, which may reflect your problem. 
 
There isn't much information in that particular bug report but if you have any ideas for workarounds, I'd suggest posting in that report.  

TWO

---

