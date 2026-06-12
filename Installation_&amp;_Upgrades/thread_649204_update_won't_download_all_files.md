---
title: "update won't download all files"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by theRevMom on 2007-12-24
Hello.

I'm trying to upgrade from Edgy to Feisty so I can go to Gutsy.  But.... there's always a but, isn't there!! :)

I have Edgy up to date.  It says an upgrade is available.  I click on UPGRADE. It begins to download the necessary files.  Then I get an error message:

ERROR DURING UPDATE
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://flomertens.keo.in/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found
Failed to fetch [http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz](http://ntfs-3g.sitesweetsite.info/ubuntu/dists/edgy/main-all/binary-i386/Packages.gz) 404 Not Found


Suggestions?  

I MUST upgrade because I have a dual boot system and can't afford to lose the XP Pro installation because I use it for work.  So....

Thanks!

---

### Post by linuxwizard on 2007-12-24
Remove or disable all extra repos YOU added to your source list. Than try upgrading again.

---

### Post by theRevMom on 2007-12-25
Thank you for your post.  Help me out here.   What are repos?  Sorry to be so newbie-ish....

---

### Post by taurus on 2007-12-25
Open a terminal, Applications -> Accessories -> Terminal, and edit /etc/apt/sources.list.

```
gksudo gedit /etc/apt/sources.list
```
Now, place a # in front of those lines, repos, to comment them out.  Save it and close gedit window.  See if you can upgrade to Feisty this time.

---

### Post by theRevMom on 2007-12-25
Thank you.... I am now downloading the updates.  I have a cable modem and it says it will take 14 hours 55 minutes.... is it THAT big?  Hmmm...

---

### Post by theRevMom on 2007-12-26
All is calm.  All is bright.  It worked perfectly.  Thank you all for your assistance.  

I LOVE Linux!!

---

