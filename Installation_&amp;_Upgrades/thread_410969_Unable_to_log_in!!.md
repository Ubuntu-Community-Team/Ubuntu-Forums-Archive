---
title: "Unable to log in!!"
date: 2007-04-16
forum: Installation &amp; Upgrades
---

### Post by mauriceplus on 2007-04-16
Hi.. this morning I've installed the last upgrades of this weekend on Kubuntu 7.04.. then, after restart.. it doesn't let me to log in!!! only in the recovery mode it starts and on Gnome style (this coz I made the installation of KDE, but previous I had Gnome..)!! 
so, I write ID and Password, but it return on the login page..:confused: 

 can someone help me??! 
THANX A LOT!!!!!

---

### Post by bapoumba on 2007-04-16
Hello :)
from recovery mode, run ```
df -H
``` and see if you are running out of space.
You can run ```
# aptitude clean
``` to make some room on the root (/) partition in addition to deleting some personal files in your /home. (in recovery mode, you are root, with the # prompt, so you do not need sudo).

---

### Post by mauriceplus on 2007-04-17
:popcorn: 
THANK YOU so much!!!
I'm not a newby, but some troubles I can't recognize yet... :oops:

---

### Post by bapoumba on 2007-04-17
You are welcome :)

---

