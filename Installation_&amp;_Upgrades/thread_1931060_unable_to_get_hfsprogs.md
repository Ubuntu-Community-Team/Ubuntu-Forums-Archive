---
title: "unable to get hfsprogs"
date: 2012-02-24
forum: Installation &amp; Upgrades
---

### Post by bugjah on 2012-02-24
root@ubuntu:/home/ubuntu# sudo apt-get install hfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package hfsprogs


why?

This ubuntu beginner thanks you all for any ideas

---

### Post by 23dornot23d on 2012-02-24
Try doing this first please .... just to make sure your package lists are up todate ....
[B]
sudo apt-get update[/B]


then try again


[B]sudo apt-get install hfsprogs

[/B]
post any out put too please

---

### Post by bugjah on 2012-02-24
Dear 23

Many thanks.  I tried that already- same thing

root@ubuntu:/home/ubuntu# sudo apt-get update
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/main Translation-en_US
Get:2 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release.gpg [198B]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick/restricted Translation-en_US
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release.gpg [198B]
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/main Translation-en_US
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en
Ign [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) maverick-updates/restricted Translation-en_US
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick Release [39.8kB]
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en
Ign [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) maverick-security/restricted Translation-en_US
Get:5 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security Release [39.8kB]
Get:6 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates Release [39.8kB]
Get:7 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main Sources [103kB]
Get:8 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main Sources [829kB]
Get:9 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted Sources [14B]
Get:10 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/main i386 Packages [324kB]
Get:11 [http://security.ubuntu.com](http://security.ubuntu.com) maverick-security/restricted i386 Packages [14B]
Get:12 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted Sources [4,370B]
Get:13 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/main i386 Packages [1,492kB]
Get:14 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick/restricted i386 Packages [5,992B]
Get:15 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main Sources [176kB]
Get:16 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted Sources [778B]
Get:17 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/main i386 Packages [460kB]
Get:18 [http://archive.ubuntu.com](http://archive.ubuntu.com) maverick-updates/restricted i386 Packages [1,797B]
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/main Translation-en_US
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en
99% [Working]
Ign cdrom://Ubuntu 10.10 _Maverick Meerkat_ - Release i386 (20101007)/ maverick/restricted Translation-en_US
Fetched 3,517kB in 1min 12s (48.6kB/s)
Reading package lists... Done
root@ubuntu:/home/ubuntu# 
root@ubuntu:/home/ubuntu# sudo apt-get install hfsprogs
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package hfsprogs

---

### Post by bugjah on 2012-02-24
I found a downloadable package here:

[http://ftp.de.debian.org/debian/pool/main/h/hfsprogs/hfsprogs_332.14-4.diff.gz](http://ftp.de.debian.org/debian/pool/main/h/hfsprogs/hfsprogs_332.14-4.diff.gz)

so I now have it downloaded and unpacked on my ubuntu usb stick

...can I install it manually?  if so how?

---

### Post by 23dornot23d on 2012-02-24
Use Synaptic Package Manager 

Check the Repositories that are ticked .... you could be missing one ....

Check Universe .....

---

### Post by 23dornot23d on 2012-02-24
Try Synaptic ....... as installing from a compressed file means compiling it ....

I think one of your repositories is not ticked for use ......

I did a search too and think it should be available for maverick ....

[https://www.google.com/search?q=hfsprogs#hl=en&sclient=psy-ab&q=hfsprogs+maverick+deb+ppa&pbx=1&oq=hfsprogs+maverick+deb+ppa&aq=f&aqi=&aql=&gs_sm=3&gs_upl=37396l40761l2l41157l6l5l1l0l0l0l133l596l0.5l6l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=89c626dd8ba41db5&biw=1149&bih=526](https://www.google.com/search?q=hfsprogs#hl=en&sclient=psy-ab&q=hfsprogs+maverick+deb+ppa&pbx=1&oq=hfsprogs+maverick+deb+ppa&aq=f&aqi=&aql=&gs_sm=3&gs_upl=37396l40761l2l41157l6l5l1l0l0l0l133l596l0.5l6l0&bav=on.2,or.r_gc.r_pw.r_qf.,cf.osb&fp=89c626dd8ba41db5&biw=1149&bih=526)

---

### Post by bugjah on 2012-02-24
yay!  got it!  thank you!

---

