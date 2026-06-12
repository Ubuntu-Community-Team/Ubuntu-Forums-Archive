---
title: "Deleting updates or preventing them"
date: 2008-03-07
forum: Installation &amp; Upgrades
---

### Post by radtek on 2008-03-07
One of the main problems of the update feature in 7.10 is it gives you no option to permanently decline an update. I'm assuming the terminal is the way to go.

In past versions I've just downloaded every update hoping everything is ok. However, I just got an unsigned update that I have no use for (as I could care less about daylight savings time in Chile). I was unable to uninstall the update (I think):

```
radtek@radtek-lpt:~$ sudo apt-get remove tzdata
[sudo] password for radtek:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ja-trans language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base locales tzdata ubuntu-minimal util-linux
  util-linux-locales
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  util-linux tzdata (due to util-linux)
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
E: Could not get lock /var/cache/apt/archives/lock - open (11 Resource temporarily unavailable)
E: Unable to lock the download directory
radtek@radtek-lpt:~$ 

```

Then I tried again after closing the update manager:

```
radtek@radtek-lpt:~$ sudo apt-get remove tzdata
[sudo] password for radtek:
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  ja-trans language-pack-en language-pack-en-base language-pack-gnome-en
  language-pack-gnome-en-base locales tzdata ubuntu-minimal util-linux
  util-linux-locales
WARNING: The following essential packages will be removed.
This should NOT be done unless you know exactly what you are doing!
  util-linux tzdata (due to util-linux)
0 upgraded, 0 newly installed, 10 to remove and 0 not upgraded.
Need to get 0B of archives.
After unpacking 51.1MB disk space will be freed.
You are about to do something potentially harmful.
To continue type in the phrase 'Yes, do as I say!'
 ?] exit
Abort.
radtek@radtek-lpt:~$ 
```

Helppp....!

---

### Post by ajgreeny on 2008-03-07
Open synaptic and search for and highlight the package you want to lock.  Now go to Package>Lock version and you will not be bothered with nudges to update it again.  It is possibly safer than removing packages you don't use, as they may be needed for something you do use, even if they aren't actually a dependency of it.

---

### Post by radtek on 2008-03-07
Thanks! Another niggling irritation removed!

However, is it possible to just remove the file and not any dependencies? How would one modify the command "apt-get remove tzdata" to do this?

Purely an academic question...

---

### Post by ajgreeny on 2008-03-08
Sorry, I don't know if it is possible, nor how to do it, if it is.

---

### Post by radtek on 2008-03-12
Well, I tried it on another pc I have (one of three running Ubuntu) and that's the ticket. Seems sort of cumbersome to have to do it this way. I figure as long as you have a GUI for the updates one should have the ability to control what is updated. My only concern is this would be one of the few ways to introduce a virus since most people trust the updater.

---

