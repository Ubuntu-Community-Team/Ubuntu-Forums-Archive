---
title: "Reporting broken mirror?"
date: 2013-03-09
forum: Installation &amp; Upgrades
---

### Post by _Groove_ on 2013-03-09
Hi,

I just found that the mirror at mirror.dattobackup.com is out of sync. My installs are failing due to not getting the specific versions of packages I need.

For example, compare the following bad and good mirror sites:
[http://mirror.dattobackup.com/ubuntu/pool/main/liba/libav/](http://mirror.dattobackup.com/ubuntu/pool/main/liba/libav/)
[http://hive.ist.unomaha.edu/ubuntu-archive/pool/main/liba/libav/](http://hive.ist.unomaha.edu/ubuntu-archive/pool/main/liba/libav/)

The first has the latest version of libav-tools as 0.8.3-6ubuntu1.
The second has the latest version of libav-tools as 0.8.5-0ubuntu1.

The out of sync mirror is several patch releases behind.

What is the correct way to report this so that the mirror site can be removed from the mirror list until it is back in sync?

---

### Post by Elfy on 2013-03-09
As far as the mirror list is concerned it's 2 days behind. 

[https://launchpad.net/ubuntu/+archivemirrors](https://launchpad.net/ubuntu/+archivemirrors)

If you need to talk to someone - [https://wiki.ubuntu.com/Mirrors#Communication](https://wiki.ubuntu.com/Mirrors#Communication)

---

### Post by _Groove_ on 2013-03-09
@Elfy AFAICS that list says "Last update unknown" - where do you see 2 days behind?

In any case I did not know about that page - it's very useful, thank you!
I'll get in contact with the mirror admins.

---

### Post by Elfy on 2013-03-09
University of Nebraska at Omaha, College of IS&T 	http rsync 	1 Gbps 	Two days behind

I looked for unomaha

I see now the other one - if it's that far behind then I'd not use it, remove it from your servers perhaps ;)

---

### Post by _Groove_ on 2013-03-09
That's the problem - I can't remove it if it is being automatically provided by the mirror list.

---

### Post by Elfy on 2013-03-09
Try going to software sources - then main tab - sort of middle of there - Download from - change your server.

---

### Post by _Groove_ on 2013-03-09
These are automated installs with a boot script that sets up the apt mirror sources, so would need a way to tell the apt-mirror system to exclude a given server from the configuration file or command line.

---

### Post by Elfy on 2013-03-09
oh - well I guess you'll have to talk to someone about the mirror then.

---

### Post by _Groove_ on 2013-03-09
[http://mirrors.cs.wmich.edu/ubuntu/](http://mirrors.cs.wmich.edu/ubuntu/) seems to also be way behind in sync.

---

