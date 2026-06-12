---
title: "Dell Mini 9 Repository issues"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by davepoth on 2010-01-03
I've spent a frustrating afternoon trying to get the answer to this but I'm having no luck at all.

For my sins I have a Dell Mini 9 running Hardy which is set up with custom repositories which haven't been updated for months. I can't find out what I need to do to change from these repositories to the standard ones. Can anyone help?

---

### Post by earthpigg on 2010-01-03
hi,

[http://repogen.simplylinux.ch/](http://repogen.simplylinux.ch/)

you probably want the 4 main ones, but not the 4 'source' ones.

your repo information is stored in a text file, which you will need to edit:

```
sudo gedit /etc/apt/sources.list
```

---

### Post by davepoth on 2010-01-03
> #############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://uk.archive.ubuntu.com/ubuntu/](http://uk.archive.ubuntu.com/ubuntu/) hardy main restricted universe multiverse 


Was the result I got in Update Manager:

Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/main/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/restricted/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/universe/binary-lpia/Packages.gz)  404 Not Found
Failed to fetch [http://uk.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz](http://uk.archive.ubuntu.com/ubuntu/dists/hardy/multiverse/binary-lpia/Packages.gz)  404 Not Found
Some index files failed to download, they have been ignored, or old ones used instead.

-edit-

But that has led me to find where the actual repos for lpia are. ;)

---

### Post by davepoth on 2010-01-03
Interesting new problem. Despite doing the above and finding the lpia port at ports.ubuntu.com, Update manager is still looking for it at archive.ubuntu.com. 

Sources.list now reads:

> 
#############################################################
################### OFFICIAL UBUNTU REPOS ###################
#############################################################

###### Ubuntu Main Repos
deb [http://ports.ubuntu.com/](http://ports.ubuntu.com/) hardy main restricted universe multiverse

Any thoughts?

---

### Post by snowpine on 2010-01-04
Why not simply install the current Ubuntu release (9.10)? Support for so-called "Dellbuntu" is terrible (in my opinion) and the applications are almost 2 years old. I deleted it within 15 minutes of receiving my Mini 9 and never looked back. :)

Here's a website with some good installation guides: [http://www.ubuntumini.com/](http://www.ubuntumini.com/)

---

### Post by =not4prophet= on 2010-01-04
I would strongly recommend installing the latest UNR.  I am running it on my Mini 9 and it works great, though I did have some issues getting the wireless drivers installed initially.

---

