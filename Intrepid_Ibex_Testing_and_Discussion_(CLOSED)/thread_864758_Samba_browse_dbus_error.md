---
title: "Samba browse dbus error"
date: 2008-07-20
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by linux6994 on 2008-07-20
After upgrading to Ibex I have found that when attempting to search external shares (XP & Vista) is get a dbus error stating that the mount is already there. The desired mount shows on the desktop but I can not get to it. I have attached the error.

Found that samba browse works with Dolphin and not Nautilus

foound same error in Launchpad - already reported

---

### Post by mattismyname on 2008-07-20
I reported it in Launchpad yesterday:  [https://bugs.launchpad.net/ubuntu/+bug/249733](https://bugs.launchpad.net/ubuntu/+bug/249733)

---

### Post by scradock on 2008-07-22
> **mattismyname said:**
> I reported it in Launchpad yesterday:  [https://bugs.launchpad.net/ubuntu/+bug/249733](https://bugs.launchpad.net/ubuntu/+bug/249733)

I confirmed the bug on Launchpad; now it has been marked as a duplicate of an older bug that appeared in Hardy. I have requested that it be de-duplicated and treated as an independent bug, which it seems to be.

---

### Post by scradock on 2008-07-23
Update if anyone is still interested: the launchpad bug was de-duplicated and I did some testing with gvfs-bin utilities that seemed to show that it has to be a gvfs error, as the "mounted" share is inaccessible using gvfs-ls without involving nautilus at all.

There is an earlier bug report #241139 about the same issue, so I have marked the current one as a dup of that, and reported the gvfs results under #241139 to try to get it all fixed.

---

### Post by gmxgeek on 2008-08-29
i know this is rather old, but here is a quick and dirty mounting tool until a fix comes out



#!/bin/bash
echo "Enter Server Name:"
read Server
echo "Enter Share Name:"
read Share
SMB="smb://$Server/$Share/"
DIR="$HOME/.gvfs/$Share on $Server"
/usr/bin/gvfs-mount "$SMB"
/usr/bin/nautilus "$DIR"

---

### Post by scradock on 2008-09-16
Looks as if the Sep 16th update to gvfs finally fixed this bug. The shares now open correctly in Nautilus..

Whoopee - one more bug bites the dust! Now Intrepid has one less glaring flaw.

---

