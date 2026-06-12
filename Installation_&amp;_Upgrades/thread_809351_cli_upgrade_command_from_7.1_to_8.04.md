---
title: "cli upgrade command from 7.1 to 8.04"
date: 2008-05-27
forum: Installation &amp; Upgrades
---

### Post by atl_CCk on 2008-05-27
I am running 7.10 with problems.  I can't do an upgrade from gnome desktop, no ? for root password.  Can someone tell me the command sequence to perform this function from a command line?

---

### Post by ibutho on 2008-05-27
You first need to edit your /etc/apt/sources.list and change all instances of gutsy to hardy. After that run 
```
sudo aptitude update
sudo aptitude full-upgrade
```

---

### Post by zvacet on 2008-05-27
>  I can't do an upgrade from gnome desktop, no ?

Yes,you can.**System>admin>update manager** but before you do that be sure that your system is up-to-date

```
sudo aptitude update && sudo aptitude safe-upgrade
```

After that you should see in update manager message that new version is available for upgrade.

---

### Post by atl_CCk on 2008-05-29
Problem turned out to be error in /etc/sudoers file line 20 had a carriage return(CR).  Removed the CR as in root ALL=(
ALL) ALL
to
root     ALL=(ALL) ALL
And it worked!

Cleaned up a lot of problems?

---

