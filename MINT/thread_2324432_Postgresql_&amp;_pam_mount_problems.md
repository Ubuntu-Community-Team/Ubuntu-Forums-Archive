---
title: "Postgresql &amp; pam_mount problems"
date: 2016-05-13
forum: MINT
---

### Post by strungoutfan78 on 2016-05-13
I'm having a hell of a time trying to get postrgresql-9.3 installed on my 14.04 box (actually Mint 17.3).  Every time I try to install it it gets to the very end and gives me:
```
$ sudo aptitude install postgresql
The following NEW packages will be installed:
  postgresql
The following partially installed packages will be configured:
  postgresql-9.3 postgresql-common
0 packages upgraded, 1 newly installed, 0 to remove and 36 not upgraded.
Need to get 0 B/5,038 B of archives. After unpacking 72.7 kB will be used.
Selecting previously unselected package postgresql.
(Reading database ... 185002 files and directories currently installed.)
Preparing to unpack .../postgresql_9.3+154ubuntu1_all.deb ...
Unpacking postgresql (9.3+154ubuntu1) ...
Setting up postgresql-common (154ubuntu1) ...
reenter password for pam_mount:
```

It doesn't matter what password I type here.  It spells the password out in plain text and just sits there.  I have to go to great lengths to remove the lock and manually remove the broken, half-installed packages from dpkg in order to get apt to start working again after this.  I use pam_mount to mount my Windows network shares at work, otherwise I would just remove it.  Does anyone have any idea how to fix this?  I can only find one other instance of someone else asking this question and there seems to be no answer yet.  That question can be found here: [http://askubuntu.com/questions/755089/reenter-password-for-pam-mount-ubuntu-14-04]("http://askubuntu.com/questions/755089/reenter-password-for-pam-mount-ubuntu-14-04")

I realize I'm installing postgresql from a non-standard source in my example, but it doesn't matter if I use official repos or the [opennms]("http://www.opennms.org/wiki/Main_Page") repo, which I'm using above. It's always the same result.

I'm not at all familiar with configuration of the pam stack.  It was hard enough for me to figure out how to get my network shares to mount properly upon login.  This is far beyond my knowledge.  Any pam experts out there, your help would be greatly appreciated.

---

### Post by howefield on 2016-05-13
Thread moved to the "*MINT*" forum.

---

### Post by strungoutfan78 on 2016-05-17
Thanks.  I didn't realize there was a "mint" section here.  Been away for a while and things have changed quite a bit it seems.

---

