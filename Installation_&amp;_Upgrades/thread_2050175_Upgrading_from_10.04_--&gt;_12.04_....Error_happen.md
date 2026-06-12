---
title: "Upgrading from 10.04 --&gt; 12.04 ....Error happens."
date: 2012-08-30
forum: Installation &amp; Upgrades
---

### Post by satyamM on 2012-08-30
Hello Everyone,
I was upgrading my system to 12.04 from 10.04 as it offered in "Show Updates" page..
It passed out "Preparing system Upgrade" and "Setting new Software Channels" options very well without any problem.

But when it came to "Installing new software packages"...it almost completed it too...but at last, suddenly comes the following error:

Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/libtorrent-rasterbar6_0.15.10-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/libtorrent-rasterbar6_0.15.10-1_i386.deb) 403  Forbidden
Failed to fetch [http://in.archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/python-libtorrent_0.15.10-1_i386.deb](http://in.archive.ubuntu.com/ubuntu/pool/universe/libt/libtorrent-rasterbar/python-libtorrent_0.15.10-1_i386.deb) 403  Forbidden


Please help someone with this.

---

### Post by kansasnoob on 2012-08-30
You're going to have to disable or remove the two "libtorrent-rasterbar/python-libtorrent" entries in software sources.

[http://www.rasterbar.com/products/libtorrent/building.html](http://www.rasterbar.com/products/libtorrent/building.html)

---

### Post by satyamM on 2012-08-30
I have removed these two things.....
Lets wait and see what happens...
Just started the Upgrade again....!!!!

---

### Post by satyamM on 2012-08-30
So after 7 hours of little tweaks and tricks and much of waiting and sometimes hopes were gone and sometimes looked it would just upgrade in a minute or two, seeing its speed of upgrading.......I am writing this reply from upgraded version of 12.04   \m/ \m/.... 
Thanks to @kansasnoob for that advice, otherwise I couldn't have figured out the problem...
This version certainly looks better than previous ones.....hope it goes well for me ........!!

Party time...!! :popcorn:

---

