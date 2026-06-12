---
title: "sudo aptitude updatedoesn't update"
date: 2006-11-29
forum: Installation &amp; Upgrades
---

### Post by figo2476 on 2006-11-29
hi guys:
When I try sudo aptitude update. It said that

Reading package lists... Done
Building dependency tree... Done
Reading extended state information
Initializing package states... Done
Building tag database... Done
Reading package lists... Done
So... it is the end.

Also when I try to install something. eg. kword. It said that there is no candidate for it.

Regards
gary

---

### Post by bapoumba on 2006-11-29
Hi, can you post the output of **cat /etc/apt/sources.list** ?

---

### Post by figo2476 on 2006-11-29
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper main restricted

## Major bug fix updates produced after the final release of the
## distribution.
# Line commented out by installer because it failed to verify:
#deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted
# Line commented out by installer because it failed to verify:
#deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse
# deb-src [http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) dapper-backports main restricted universe multiverse

# Line commented out by installer because it failed to verify:
#deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# Line commented out by installer because it failed to verify:
#deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security main
# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) dapper-security universe

I am not sure how to solve this kind of problem

---

### Post by cronholio on 2006-11-29
Uncomment (remove "#") all the lines starting with deb or deb-src and try again.

---

### Post by figo2476 on 2006-11-29
It works now. That is good. I updated & installed firefox, but how can i run firefox. 

If I run in konsole by typing 'firefox', it complained "Gtk-WARNING **: cannot open display". So I guess it is not the right way to do. So what is the correct way to run firefox.

---

### Post by cronholio on 2006-11-29
Probably you are trying to run Firefox(tm) as root. Run it as the user that owns the X session.

Usually you run Firefox(tm) from the Applications->Internet menu or the panel. There should be a Firefox(tm) icon on your panel, if not, right click on your upper panel and add it.

---

### Post by cronholio on 2006-11-29
Sorry, you wrote "konsole" so probably you are in KDE. You will find Firefox in the KDE menu.

---

