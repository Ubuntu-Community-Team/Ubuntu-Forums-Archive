---
title: "hardy 8.04: how to make a repository cd of the copied packages in /var/cache/apt?"
date: 2008-05-24
forum: Installation &amp; Upgrades
---

### Post by prosenjit.das on 2008-05-24
I had installed ubuntu hardy (8.04) in my comp using virtualbox (for test) and copied all the packaged in /var/cache/apt (the file "lock" was not copied!) and made a cd to make use of the packages later. Now i have deleted that test installation and installed hardy in my comp permanently. But i can't make use of cd as a repository cd using synaptic. Is there a way out to make repository cd out of that cd?

---

### Post by PmDematagoda on 2008-05-24
You should add the cdrom as a repository with:-
```
sudo apt-cdrom add -d /media/mount-point
```

---

### Post by prosenjit.das on 2008-05-24
Thanks for trying to solve it ... but it didn't work :(
The code was not working so i tried that with slight change and the following error is generated:

root@rhos33:/home/guest# apt-cdrom add -d /media/cdrom0
Using CD-ROM mount point /media/cdrom0/
Unmounting CD-ROM
Waiting for disc...
Please insert a Disc in the drive and press enter 
Mounting CD-ROM...
Identifying.. [ca48d8a3fd3bd9302b77eb2e7c63cfb8-2]
Scanning disc for index files..
Found 0 package indexes, 0 source indexes, 0 translation indexes and 0 signatures
E: Unable to locate any package files, perhaps this is not a Debian Disc

---

### Post by prosenjit.das on 2008-05-25
got the answer :)

its in the following link:
[http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/](http://odzangba.wordpress.com/2006/10/13/how-to-build-local-apt-repositories/)

---

### Post by sparklyprgs on 2008-08-24
[*BUMP*]

Ahhhh .. after looking for hours how to do this, I finally found your link prosenjit.das. It worked **PERFECTLY!!!** :)

Thanks odzangba (odzangba.wordpress.com), here is a tinyurl link to the same post:

[http://tinyurl.com/6nzytr]("http://tinyurl.com/6nzytr")

The only bit I'll add (for the new-ish users aka - me!) is when you eventually add the CD and get back to the main screen of Synaptic, just click "Mark All Upgrades" to mark all the ones you just added so you can then click Apply.

Cool!  No more 3 hour upgrades after every friggin build!

---

