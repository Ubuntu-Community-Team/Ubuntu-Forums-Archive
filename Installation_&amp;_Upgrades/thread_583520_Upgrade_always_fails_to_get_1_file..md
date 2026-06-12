---
title: "Upgrade always fails to get 1 file."
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by slappgat on 2007-10-20
Hi i'm a noobie to linux. 

I'm running the update manager and after a while it pops up a windows "Error during update"
Failed to fetch [http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz](http://archive.canonical.com/ubuntu/dists/gutsy/partner/binary-i386/Packages.gz) MD5Sum mismatch

I've tried changing my download source. 

can anyone help me. 

Thx.

---

### Post by Stemp on 2007-10-20
Could you try it by command line ? 

```
sudo aptitude update
```
and if you don't see this error
```
sudo aptitude full-upgrade
```

---

### Post by slappgat on 2007-10-20
Thanks for the reply.

This is what i get once i run sudo aptitude full-upgrade

ubuntu@ubuntulap:~$ sudo aptitude upgrade
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Initializing package states... Done
Building tag database... Done      
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.

no change in update same error. Seems to be trying to get opera and it fails on that

---

### Post by slappgat on 2007-10-20
Found the solution here [http://ubuntuforums.org/showthread.php?p=3582546#post3582546](http://ubuntuforums.org/showthread.php?p=3582546#post3582546)

Thx :)

---

