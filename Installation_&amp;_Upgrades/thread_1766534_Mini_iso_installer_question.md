---
title: "Mini iso installer question"
date: 2011-05-24
forum: Installation &amp; Upgrades
---

### Post by Billxyzzy on 2011-05-24
I have been trying to use the amd64 version of the
natty mini iso installer.
The installer crashes with the log stating bad address
us.archive.ubuntu.com.
This is true for any archive I select.
error is: mirror does not support the specified release
(natty)
Anyone know of a working mirror or if one will ever work?
Not a confidence builder in the development.

I also tried the Maveric version of the mini iso.
It also crashes with complaints about a bad kernel.
So far a wasted day.

Just add to this I tried the normal natty iso.
The problem is in the manual partitioning. It locks
up solid while trying to set partitions.
Is there a later release of the iso?

---

### Post by zvacet on 2011-05-24
IS it iso O.K.?Did you checked [md5sum]("https://help.ubuntu.com/community/HowToMD5SUM") of Natty iso?Other way to do partitions is to download [gpartred live cd.]("http://gparted.sourceforge.net/")Make pattitions with it and after that try to install Natty on previously made partitions.

---

### Post by Billxyzzy on 2011-05-24
Way ahead of you.  MD5sum ok. gparted no help in installer
must overwrite all gparted does.  This is an archive and installer problem

---

### Post by satanselbow on 2011-05-24
I've used both the mini ISO's within the last week and had no problems... you have had both maverick and natty live CD's up and working as they should? 

The oneiric mini is good too btw - but changes on an almost daily basis ;)

---

### Post by Billxyzzy on 2011-05-24
Have both maverick and natty iso's Have used both.
However the natty amd64 iso has a problem with manual
partitoning.  It hangs during the procedure.
Not a md5sum problem.

---

### Post by satanselbow on 2011-05-24
> **Billxyzzy said:**
> ...natty amd64 iso has a problem with manual
partitoning.  It hangs during the procedure...

If you can boot into a full live ISO could you not create your partitions there and then just point the mini installer to the pre-existing partition(s) without reformatting the partitions?

Just an idea - and doesn't explain why the mini installer fails. I always do it that way truth be told so there may be a problem with the mini partition tools that I bypass by sheer luck ;)

---

### Post by Billxyzzy on 2011-05-24
I wish it were that simple.  The installer overwrites
any previous partitions.  It forces you to reset the
partitions.
This is true in both the full installer and the mini
installer.

---

### Post by stevehanler on 2011-05-25
> **Billxyzzy said:**
> I have been trying to use the amd64 version of the
natty mini iso installer.
The installer crashes with the log stating bad address
us.archive.ubuntu.com.
This is true for any archive I select.
error is: mirror does not support the specified release
(natty)
Anyone know of a working mirror or if one will ever work?
Not a confidence builder in the development.


I'm running into a problem installing from the Natty x86 mini.iso. The problem I am having is with the steps "Detect disks" and "Install the base system". [Here are the errors I am seeing]("http://razorsoup.imgur.com/ubuntu_mini_errors"). Are you getting these same errors?

---

### Post by Billxyzzy on 2011-05-25
I looked at your error messages and they are the same as
what I am seeing.  No one seems to have a solution yet.
The Maverick mini installer has its own problems so
that was not a solution.
The new oneiric installer is even worse.

However,  I got tired of fooling withe mini installers and
downloaded the full alternate installer.  Mission completed.

---

