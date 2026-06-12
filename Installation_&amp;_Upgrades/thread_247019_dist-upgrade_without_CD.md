---
title: "dist-upgrade without CD"
date: 2006-08-30
forum: Installation &amp; Upgrades
---

### Post by alecjw on 2006-08-30
Is there any way of running dist-upgrade without a CD? Whenever i try it, it asks me to insert the CD into /cdrom/, which doesn't exist. I want to upgrade to edgy/grumpy.

---

### Post by ciscosurfer on 2006-08-30
First off, you most probably have a line in your sources.list file that tells it to look for upgrades off of a CD that you probably installed your old/current version with.

You can either go into your sources.list file and change all occurences of "dapper" to "edgy", save the file, quit.  Comment the line (prob.) at the top that starts with "CDROM" with a pound sign (#)...and of course, make sure you have the appropriate repositories enabled (search the forums for "clean dapper sources.list" or something like that.  Copy those over to your sources.list file, then do```
sudo aptitude update
sudo aptitude dist-upgrade
``` or

Try this out in a terminal```
sudo update-manager -c -d
```

---

### Post by alecjw on 2006-08-30
Cheers. It's downloading from the internet now.

---

