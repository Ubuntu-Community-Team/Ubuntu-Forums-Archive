---
title: "Cant update in Ubuntu 12.04LTS"
date: 2012-09-26
forum: Installation &amp; Upgrades
---

### Post by Edgar117 on 2012-09-26
I get these errors in the terminal::lolflag:

W: Failed to fetch [http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Any Help Mates???

---

### Post by Edgar117 on 2012-09-26
> **Edgar117 said:**
> I get these errors in the terminal::lolflag:

W: Failed to fetch [http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/dists/precise/main/source/Sources](http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/dists/precise/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/dists/precise/main/binary-i386/Packages](http://ppa.launchpad.net/and471/kazam-daily-builds/ubuntu/dists/precise/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

Any Help Mates???

Ok now i am getting from the update manager that there is no internet connection (Which I do) 
And it just updated but looks like the Kazaam is giving problems?!):P

---

### Post by jerrrys on 2012-09-26
You need to edit out (comment out (#)) Kazaam PPA in your sources.list.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=edit+sources.list&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=edit+sources.list&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

---

### Post by Edgar117 on 2012-09-26
> **jerrrys said:**
> You need to edit out (comment out (#)) Kazaam PPA in your sources.list.

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=edit+sources.list&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=edit+sources.list&as_qdr=all&sa=Google+Search&lang=en&siteurl=http%3A%2F%2Fwww.googlubuntu.com%2F)

But will kazaam still work???:popcorn:

---

### Post by jerrrys on 2012-09-27
check it out

[https://launchpad.net/kazam/+announcements#j9692](https://launchpad.net/kazam/+announcements#j9692)

---

