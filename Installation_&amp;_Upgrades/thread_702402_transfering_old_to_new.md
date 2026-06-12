---
title: "transfering old to new"
date: 2008-02-20
forum: Installation &amp; Upgrades
---

### Post by jhonijim on 2008-02-20
i recently installed 7.10 on my computer to solve a video issue i was having with 6.06 my question is there a way to transfer all the programs and librarys i had to my new install i can no longer boot my old install all i get is a blank screen but my new install gives me access to all the files on my old drive i have dial-up and it took an extermly long time to download all the packages i used to install the software and i need it i use the computer for a/v editing and djing

---

### Post by aashay on 2008-02-20
If you are lucky, most of the .deb files for the installations may still be in the folder
/var/cache/apt/archives
Just copy these to the same folder on the new machine. If the apps have not updated since, apt-get would take the debs from the cache without downloading them. If the apps have been updated, you could try "lock version" feature from synaptic but i'm not sure how that works.
I've also heard that copying the /usr folder from old to new works but have had no experience with it.

---

