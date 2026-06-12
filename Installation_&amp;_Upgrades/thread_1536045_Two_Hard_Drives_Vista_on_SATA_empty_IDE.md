---
title: "Two Hard Drives Vista on SATA empty IDE"
date: 2010-07-21
forum: Installation &amp; Upgrades
---

### Post by revelationman on 2010-07-21
Just wondering, I have two drives one is a 500 gig SATA drive running Vista SP 2 now the other Maxtor 160 Gig drive is empty. I would like to install Ubuntu on that drive.

Now I just though of installing from the setup however  would this screw up my Vista partition ?

I just would like to know can this be done and how ?

Thanks ;)

---

### Post by oldfred on 2010-07-21
Herman has a good example:

Dual boot 2 drives
[http://members.iinet.net.au/~herman546/p24.html]("http://members.iinet.net.au/%7Eherman546/p24.html")
Install karmic Screens shown with advanced button
[http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml](http://news.softpedia.com/news/Installing-Ubuntu-9-10-126370.shtml)
[http://members.iinet.net/~herman546/p28/032_install-now.png]("http://members.iinet.net/%7Eherman546/p28/032_install-now.png")


The important thing is to be sure which drive is which, sometimes IDE drives become sda. Then on the last install screen is an advanced button that lets you choose which drive to install grub. Then in BIOS set the 160GB drive as the boot drive (primary master).

---

