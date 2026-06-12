---
title: "synaptic not finding repository due to wrong name"
date: 2011-03-20
forum: Installation &amp; Upgrades
---

### Post by oedipod on 2011-03-20
Hi guys hope someone can help. I have had trouble updating for ages, but only just got round to checking it. Updated to Maverick at christmas 2010. 

The essential problem is synaptic (or updte manager) won't talk to the repository.

I get:

Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/maverick/Release.gpg)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick/main/i18n/Translation-en_IE.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick/multiverse/i18n/Translation-en_IE.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick/restricted/i18n/Translation-en_IE.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick/universe/i18n/Translation-en_IE.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg](http://ie.archive.ubuntu.com/ubuntu/dists/maverick-updates/Release.gpg)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en.bz2)  
Failed to fetch [http://ie.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IE.bz2](http://ie.archive.ubuntu.com/ubuntu/dists/maverick-updates/main/i18n/Translation-en_IE.bz2)  
...., 

I have truncated the above.
When I go through these manually on the heanet server, it's not surprising because these files are not there ... instaed there are file with en_GB and en_US suffixes.

However, even when I reset my sources file to contain just these:

deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick main universe restricted multiverse
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick-updates universe main multiverse restricted
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick-proposed universe main multiverse restricted
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick-security universe main multiverse restricted
deb [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick-backports main multiverse restricted universe
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick main universe restricted multiverse
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick-security universe main multiverse restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick-updates universe main multiverse restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick-proposed universe main multiverse restricted
deb-src [http://ie.archive.ubuntu.com/ubuntu/](http://ie.archive.ubuntu.com/ubuntu/) maverick-backports universe main multiverse restricted
deb [http://extras.ubuntu.com/ubuntu](http://extras.ubuntu.com/ubuntu) maverick main #Third party developers repository

I still get the error.

Where has the system got these filenames stored or where is it getting these aberrant filenames from?

Thanks

O

---

### Post by zvacet on 2011-03-21
Most of errors coming from not been able to get translation packages.I think you can live without them for a wile.But maybe you can change server to main to get other updates if they exist.

---

### Post by oedipod on 2011-03-21
Thanks, but being unable to get the translation packages is hanging the whole process,I'm real stuck.!!! Can't update anything through synaptic, can't download new applications etc. 

Thanks for advice anyway!!

---

### Post by zvacet on 2011-03-22
As I told you in previous post go to the ubuntu software center>edit>repositories and there change servwer to main.I think that way you will not get translation updates so you will be able to update packages.

---

