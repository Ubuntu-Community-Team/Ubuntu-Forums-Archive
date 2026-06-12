---
title: "Jaunty Jackalope update problem"
date: 2011-06-30
forum: Installation &amp; Upgrades
---

### Post by niraj_vara on 2011-06-30
Hi

  I am trying to install the update the [B]Jaunty Jackalope but it gives the following error.


If I want to install the latest the ubuntu version without formating this how can I do that...


W: Failed to fetch [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-backports/multiverse/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-updates/restricted/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-updates/main/binary-i386/Packages](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-updates/main/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-updates/multiverse/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-updates/universe/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-proposed/restricted/binary-i386/Packages](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-proposed/restricted/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-proposed/main/binary-i386/Packages](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-proposed/main/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-proposed/multiverse/binary-i386/Packages](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-proposed/multiverse/binary-i386/Packages)  404 Not Found

W: Failed to fetch [http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-proposed/universe/binary-i386/Packages](http://ftp.jaist.ac.jp/pub/Linux/ubuntu/dists/jaunty-proposed/universe/binary-i386/Packages)  404 Not Found

[/B]

---

### Post by mörgæs on 2011-06-30
Such an old installation is likely to run on Grub 1 and ext3. 

If you manage to upgrade to a new Ubuntu, which is a long and risky process, you will still have Grub 1 and ext3 as the foundation. 

I would go for a live boot of a new Ubuntu and after that a fresh install.

---

### Post by vicshrike on 2011-06-30
Jaunty is no longer supported.

[http://www.ubuntugeek.com/ubuntu-9-04-reaches-end-of-life-on-october-23-2010.html](http://www.ubuntugeek.com/ubuntu-9-04-reaches-end-of-life-on-october-23-2010.html)

---

