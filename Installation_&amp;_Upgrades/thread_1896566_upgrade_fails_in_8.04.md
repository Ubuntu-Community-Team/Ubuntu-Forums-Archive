---
title: "upgrade fails in 8.04"
date: 2011-12-17
forum: Installation &amp; Upgrades
---

### Post by mavijitr on 2011-12-17
Failed to fetch [http://toshiba-arizona.archive.canonical.com/updates/dists/hardy-toshiba-arizona/Release](http://toshiba-arizona.archive.canonical.com/updates/dists/hardy-toshiba-arizona/Release)  Unable to find expected entry  multiverse/binary-lpia/Packages in Meta-index file (malformed Release file?)
Some index files failed to download, they have been ignored, or old ones used instead.

---

### Post by mavijitr on 2011-12-17
help required:(

---

### Post by overdrank on 2011-12-17
Hi and welcome, you may look here [_EOLUpgrades_]("https://help.ubuntu.com/community/EOLUpgrades").

---

### Post by mavijitr on 2011-12-17
Thank you very much for your quick suggestion.  I went through the link and found 8.04 is the last release in that series.  

Now, I want to upgrade my mini toshiba NB100 laotop from 8.04 to 11.04 the latest one.  i have downloaded the software too, but I could not install it in this machine.

i copied the image file in a USB. I am not able to execute the wubi.exe in this machine.  If I plug the USB into a windows machine then i can.  

What is the procedure to get it done?

Please provide me suggestion.

---

### Post by 2F4U on 2011-12-17
Wubi is for Windows, not for Linux. How comes you want to install and use Wubi, nowhere on the site is reference to Wubi.

---

### Post by mavijitr on 2011-12-18
iis this the last one for mini laptop? atom processor?

---

### Post by snowpine on 2011-12-22
Your 8.04 used the "lpia" architecture, which is no longer supported since 2010. Therefore you cannot upgrade; you'll have to do a fresh install.

You can download and install the latest Ubuntu 11.10 32-bit following these instructions: [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

I do not know how well it will support your specific netbook model (you can use the forum Search feature for that) but in general it runs fine on most Atom netbooks.

---

