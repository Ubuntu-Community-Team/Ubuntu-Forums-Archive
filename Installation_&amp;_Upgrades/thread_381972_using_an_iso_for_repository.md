---
title: "using an iso for repository"
date: 2007-03-11
forum: Installation &amp; Upgrades
---

### Post by Josey on 2007-03-11
I've been trying to get ubuntu on an old toshiba 1625 but the cdrom drive doesn't work very well.
I've burned alot of iso's to cdrw's and finally I have xubuntu alternate 6.06 on the machine. It doesn't have internet at this point but I think that if I can add a regular 6.06 live cd and install unbuntu-desktop that it will be online and my headache will be mostly over.

I have been able to mount the ubuntu 6.06 cd.  It shows up in whatever folder I mount it to but basically synaptic doesn't accept it as a cdrom or something. First I mounted it to /mnt/iso/ but apparently synaptic doesn't even look there.  Then I mounted it to places like /media/cdrom0/ and I got the error after clicking 'add cdrom' in synaptic 'Error scanning the CD' E: Failed to mount the cdrom.

I've been searching the forums but I can't figure out how to use iso's for repositories.

Thanks :)

---

### Post by Nikron on 2007-03-11
First, can you bring up your text editor, and check /etc/apt/sources.list to see if a deb similiar to

deb cdrom:[Ubuntu 6.10 _Edgy Eft_ - Release i386 (20061025)]/ edgy main restricted

exits already in the comments?

If so, uncomment it...  If not.. well I guess you can try changing the version numbers like
below, but I that long number probably needs to be different too...

deb cdrom:[Ubuntu 6.10 _Dapper Drake_ - Release i386 (20061025)]/ dapper main restricted

---

### Post by Josey on 2007-03-11
yes it added the xubuntu cd to the sources.list but that doesn't have ubuntu-desktop on it.  I think that if i can get that from a cd in iso form that my wireless card will work and then I won't have to worry about getting packages from cd's.

---

### Post by zvacet on 2007-03-11
if you don´t have ubuntu-desktop it means that you installed server.Search the forum to find out how to set up wireless in terminal.After that 
```
sudo aptitude update && sudo aptitude install xubuntu-desktop
```

---

### Post by Josey on 2007-03-11
I found the answer in another thread.

> sudo synaptic --add-cdrom /media/iso/

Installing ubuntu-desktop now.  :)

---

