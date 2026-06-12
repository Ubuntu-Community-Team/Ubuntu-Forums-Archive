---
title: "Breezy Badger to Dapper Drake"
date: 2006-07-26
forum: Installation &amp; Upgrades
---

### Post by geniusvicks on 2006-07-26
Should I download the whole release of DD to install it. Or is there some upgrade from which I can convert my BB to DD.

Also what makes DD better than BB?

---

### Post by aysiu on 2006-07-26
You need broadband (not dial-up) internet and/or the **Alternate CD** (not the **Desktop CD**) in order to upgrade.

As to the differences...
[http://www.ubuntu.com/download/releasenotes/606](http://www.ubuntu.com/download/releasenotes/606)

---

### Post by moma on 2006-07-26
Upgrade from Ubuntu 5.10(Breezy) to Ubuntu 6.06(Dapper).

**Method A)**
[http://daniel.holba.ch/blog/?p=14]("http://daniel.holba.ch/blog/?p=14")
[B]
Method B)[/B]
Do:

$ sudo mv /etc/apt/sources.list /etc/apt/sources.list_backup

$ cd /etc/apt
$ sudo wget [www.futuredesktop.org/dapper/sources.list](www.futuredesktop.org/dapper/sources.list)

$ sudo apt-get update
$ sudo apt-get dist-upgrade 

Study also
[http://www.futuredesktop.net/ubuntu6.06.html]("http://www.futuredesktop.net/ubuntu6.06.html")

// moma

---

### Post by rocketman768 on 2006-07-26
If you want my opinion, don't upgrade to Dapper. Dapper gave me a buttload of problems that I never got with Breezy. If you want the new kde or gnome, just use apt-get to install these.

---

### Post by SexyGorilla on 2006-08-22
Just goes to show that linux gives greatly differed experience. I have had nothing but good luck with Dapper on my workstation (HP Laptop) and my servers (assorted). There do seem to be a lot of changes between the two versions though, so definitely do your homework before you upgrade... as always. :0)

SG

---

### Post by confused57 on 2006-08-22
I just upgraded from Breezy to Dapper a couple of days ago, using this method:
[http://psychocats.net/ubuntu/dapper.php](http://psychocats.net/ubuntu/dapper.php)

Had to download 620 Mb from the internet to do the upgrade, everything seems to be working normally in the Dapper upgrade...I have a GeForce XFX5500, but I use the "nv" driver so I didn't have any issues with graphics.

If you decide to go with the above method, I suggest that after you press Ctrl+Alt+F1 and login, that you then:
```
sudo /etc/init.d/gdm stop
```

before you continue...I say this because about 80% through the installation of downloaded packages, I was presented with the splash login screen...I thought the install was complete, so I logged in, but received numerous error messages and couldn't do anything...so I pressed Ctrl+Alt+F1 and realized that the Dapper upgrade packages were still installing.
Other than that, everything went smoothly...just took a long time.  If you used Automatix to install Firefox 1.15.06 in Breezy, you might want to follow the Automatix directions for removing the Automatix Firefox & revert back to the Breezy FF(1.08) before upgrading.  I didn't and now in Dapper I have the Automatix 1.15.06 Firefox installed in Breezy...not a problem now, but I won't be able to update FF from the Dapper repositories.   I suppose I can use the Breezy FF Automatix removal instructions in Dapper...I'll cross that bridge eventually.
That's about all I can think of at the moment.

---

