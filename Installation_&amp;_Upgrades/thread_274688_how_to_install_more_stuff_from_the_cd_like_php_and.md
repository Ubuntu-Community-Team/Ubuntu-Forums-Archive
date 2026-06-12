---
title: "how to install more stuff from the cd like php and mysql"
date: 2006-10-10
forum: Installation &amp; Upgrades
---

### Post by prusu83 on 2006-10-10
I tried:

apt-get install mysql
E: Could not open lock file /var/lib/apt/lists/lock - open (13 Permission denied)
E: Unable to lock the list directory

I also tried:

sudo apt-get install php5
it asks for the password but i see no instalation going on.

The install cd is in the cd drive.

Please help.

Paul

---

### Post by taurus on 2006-10-10
You need to add your CD to your /etc/apt/sources.list before you install install stuff from it!!!

```

sudo apt-cdrom add
sudo aptitude update
sudo aptitude install mysql 
(assuming musql is on the CD!!!)

```

---

### Post by vernonBarcelona on 2006-10-10
sudo -s, to not type sudo all the time.

if it helps :)

---

