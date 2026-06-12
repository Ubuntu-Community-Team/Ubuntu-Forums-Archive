---
title: "All files lost after upgrade 10.10 to 11.04"
date: 2011-04-29
forum: Installation &amp; Upgrades
---

### Post by ijoaum on 2011-04-29
Hi folks.. 

My apt-get was really really slow since the installation of 10.10. Doing downloads at 100~2000 B/s.
So,  I decided to upgrade the Ubuntu version by the CD, a big mistake by the way.

Near end, the installation got crashed and frozen. Over 3 hours on same command line.
Then, I hardly rebooted the system to get in the OS, and it works.

BUT.... all data within /etc and /var IS GONE! 
My whole life was in "/var/www" and "/var/lib/mysql" and that is gone too.

Have any way to recover that?

=]

---

### Post by collisionystm on 2011-04-29
> **ijoaum said:**
> Hi folks.. 

My apt-get was really really slow since the installation of 10.10. Doing downloads at 100~2000 B/s.
So,  I decided to upgrade the Ubuntu version by the CD, a big mistake by the way.

Near end, the installation got crashed and frozen. Over 3 hours on same command line.
Then, I hardly rebooted the system to get in the OS, and it works.

BUT.... all data within /etc and /var IS GONE! 
My whole life was in "/var/www" and "/var/lib/mysql" and that is gone too.

Have any way to recover that?

=]

a backup? =)

---

### Post by matt_symes on 2011-04-29
Hi

> **collisionystm said:**
> a backup? =)

+1. Clonezilla. Live and learn.

Kind regards

---

### Post by Joe of loath on 2011-04-29
Doesn't the upgrade tell you to backup before doing anything else?

---

### Post by Bitrate on 2011-04-29
1. Boot a live cd such as SystemRescueCD or Parted Magic then run Testdisk/PhotoRec.

2. Pray

---

### Post by ijoaum on 2011-05-03
i have a backup.. but it seems to be broken..
after 3º or 4º folders level down has no file, only more folders.. 

LOL

anyway... thank you all.. =]

---

### Post by markjreed on 2012-05-01
Yeah, of course, always have a backup.  But that's still quite annoying.  Why would an upgrade delete everything under /var?  and /usr/local? I had the same thing happen just now, so this apparently hasn't been corrected.  CouchDB data, gone.  Doc root of web server, gone.  My home directory is the only thing on the box that seems to have survived.  That's not an "upgrade".

---

### Post by uRock on 2012-05-01
Necromancy,

Thread Closed

---

