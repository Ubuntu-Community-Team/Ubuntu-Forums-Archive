---
title: "Creation of Offline Repository for Ubuntu"
date: 2014-04-21
forum: Installation &amp; Upgrades
---

### Post by THE_KD on 2014-04-21
Hi,

before you flag this as a duplicate, I reviewed the below and it does not help.
[https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)

I am trying to create an offline repository on a PC that has no access to the internet - So that anytime i need an app/package/dependancy that is not already installed, i do not have to go online but can find it in the offline repository.

The link above gives good instructions but it does not describe how to download the actual apps/packages that form the repository. I assume all the apps for a given platform (eg. amd64) would be many gigabytes in size.

Debian offers a simple solution by offering users the option to download 4 dvd iso images containing all its apps. You can then create a repository using these dvds - and when you need to install an app, you simply insert the DVD - you never have to go online.

How do I download the complete Ubuntu repository for a given platform (amd64, x86) ? or are there DVD images of these repositories that I can download ?

---

### Post by ian-weisser on 2014-04-21
Creating a bunch of DVDs (or a sinlge external drive) is simple in the sense that what you are looking for is probably already in there somewhere.
But really only in that sense.

Most of those applications you will never have reason to use. Many others will require network access to function.
All of that download and storage capacity is simply wasted.

But if you *really* want to download every package, pick a close/fast mirror and iterate through it. All the packages are easily available using http and ftp.

For example, If I used the U.S. mirror at Argonne National Laboratory, I would download all the subdirectories and files at [http://mirror.anl.gov/pub/ubuntu/dists/](http://mirror.anl.gov/pub/ubuntu/dists/)
And then I would send their webmaster an apology for all their bandwidth I just hogged.

---

### Post by ibjsb4 on 2014-04-21
14o4 is not out yet, but ..

[https://www.osdisc.com/products/linux/ubuntu/ubuntu-1310-software-repository-64bit-pc.html](https://www.osdisc.com/products/linux/ubuntu/ubuntu-1310-software-repository-64bit-pc.html)

If you would instead pick and choose ..

[https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection](https://help.ubuntu.com/community/InstallingSoftware#Installing_packages_without_an_Internet_connection)

EDIT: Just noticed that the keryx project looks dead; bad lead, sorry

---

