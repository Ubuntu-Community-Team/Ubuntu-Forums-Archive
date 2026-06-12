---
title: "Utter morons guide: no news = Good news? 7.10 updates."
date: 2008-07-13
forum: Installation &amp; Upgrades
---

### Post by CJ_Hudson on 2008-07-13
I initially upgraded from 7.10 gutsy Gibbon to 8.04 Hardy Heron and mashed-up my kernal. My nice local computer shop very kindly re-installed Gutsy Gibbon with instructions NOT to upgrade to 8.04.
with a bit of tinkering I got the multimedia aspects of the desktops functionality working (thanks to user reassuringlythreatening's posts).
However, a) I haven't had any updates for ages for 7.10; b) there may be a problem regarding 'medibuntu' ; and
b) is it normal to have a boot-up which has to prompted every second by pressing 'Return' (=Enter)? This only happened once so I thought it may have been some kind of security check/disc scan?!
Thanks.

---

### Post by Sef on 2008-07-18
> a) I haven't had any updates for ages for 7.10; b) there may be a problem regarding 'medibuntu' ;

Applications > Accessories > Terminal

```
sudo apt-get update
```

What errors do you get?  Please copy and paste your errors in another post.

> b) is it normal to have a boot-up which has to prompted every second by pressing 'Return' (=Enter)? This only happened once so I thought it may have been some kind of security check/disc scan?!

About once every 25 or 30 times, ext3 will defragment the hard drive.  It will do it automatically upon boot up.  What happened to you is not normal.

---

### Post by CJ_Hudson on 2008-07-24
Hi Sef,
No error reported on initial suggested step. However if I carry on to do 

<< sudo apt-get upgrade >>

the mplayer update is witheld.
However, here is the complete copy of the result of the initial step:

Get:1 [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release.gpg [189B]
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Translation-en_US
Ign [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy Release
Get:2 [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy Release.gpg [191B]
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/multiverse Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/free Packages
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/restricted Translation-en_US
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/universe Translation-en_US
Ign [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/main Translation-en_US
Hit [http://packages.medibuntu.org](http://packages.medibuntu.org) gutsy/non-free Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy Release
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/multiverse Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/restricted Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/universe Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/main Packages
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/restricted Sources
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/main Sources
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/multiverse Sources
Hit [http://mirror.ox.ac.uk](http://mirror.ox.ac.uk) gutsy/universe Sources
Fetched 2B in 0s (2B/s)
Reading package lists... Done

(No repeat of the second error by the way.)

Thankyou very much.

---

