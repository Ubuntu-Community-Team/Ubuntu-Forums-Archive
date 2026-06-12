---
title: "Upgraded from Fiesty to Gutsy - Now mysterious vanishing disk space"
date: 2007-10-27
forum: Installation &amp; Upgrades
---

### Post by vadar007 on 2007-10-27
I upgraded from Fiesty ot Gutsy. Space was tight but everything seemed to go well. Now, my system is telling me I have 0% available disk space. I tried the following:

1) sudo apt-get clean
2) Cleared all /.Trash folders
3) Deleted excess files to make more room
4) Ran LiveCD and fsck'd on umounted volume (no errors)

df tells me there is an 8GB delta between size and used but 0% available.
Gpart show 8GB unused on /dev/sda1

Something very screwy is going on and I need some guidance on where to look. The othe problem is that any program that needs to use extra disk space (cache files, etc.) won't run becuase of the 0% available issue.

---

### Post by jedibuntu on 2007-10-30
I had a similar problem when I upgraded to Gutsy in  Kubuntu. Traced it to the stupid desktop search daemon Strigi which was hogging half of all available disk space for it's indexes! Uninstalled it and knocked off ~/.strigi to free up close to 10GB of data.
I'm not sure about Gnome, but if there's desktop search installed by default in Ubuntu too, that should very likely be the culprit for you too.
Hope this helps!

---

### Post by Crafty Kisses on 2007-10-30
> **jedibuntu said:**
> I had a similar problem when I upgraded to Gutsy in  Kubuntu. Traced it to the stupid desktop search daemon Strigi which was hogging half of all available disk space for it's indexes! Uninstalled it and knocked off ~/.strigi to free up close to 10GB of data.
I'm not sure about Gnome, but if there's desktop search installed by default in Ubuntu too, that should very likely be the culprit for you too.
Hope this helps!

Same here, those were in my case.

---

### Post by ijkn on 2007-10-30
i got similar problem too.:(

Originally, my computer was running Fiesty which used about 3GB only. After upgrading it to Gutsy, the system use about 7GB disk space.


I want to know how come the system use 4GB more disk space in Gutsy when comparing to Fiesty.:confused:
Are there any files I can delete to make more space?

---

### Post by chrinabuntu on 2008-01-07
So how did you guys (jedi and codename) get rid of the desktop search thingy?  I'm new so I don't know about the different commands yet.  I am having issues that I think may fall under this and want to go ahead and be ready to do that as well...but I do intend to try apt-get clean first.

---

