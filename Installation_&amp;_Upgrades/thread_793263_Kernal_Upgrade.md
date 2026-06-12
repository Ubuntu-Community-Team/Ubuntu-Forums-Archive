---
title: "Kernal Upgrade"
date: 2008-05-13
forum: Installation &amp; Upgrades
---

### Post by The Minder on 2008-05-13
I'm having many probs with 8.04 especially with nVidia drivers.   One thing I've noticed is that my kernel is 2.6.22-14-generic which I do not think is the latest incarnation.   I've tried walkerk's excellent tutorial at [http://ubuntuforums.org/showthread.php?t=646755&highlight=update+kernal](http://ubuntuforums.org/showthread.php?t=646755&highlight=update+kernal) but when I run the script it tells me my kernel is the latest, when I know it's not.

So, how do I update the Ubuntu kernel to the latest version?   And yes, I have searched the forum to no avail.

Advice appreciated

---

### Post by vorgusa on 2008-05-13
hmm I am currently in the middle of an upgrade now so I can not check to see exactly what you are looking for.  but if you go to System -> admin -> Synaptic packet manager and then search for kernel it may lead you in the right direction.. also double check your software sources (System -> admin -> Software Sources) and make sure you have the correct repositories, not sure why they would be incorrect, but worth a check.

---

### Post by bobnutfield on 2008-05-13
> **The Minder said:**
> I'm having many probs with 8.04 especially with nVidia drivers.   One thing I've noticed is that my kernel is 2.6.22-14-generic which I do not think is the latest incarnation.   I've tried walkerk's excellent tutorial at [http://ubuntuforums.org/showthread.php?t=646755&highlight=update+kernal](http://ubuntuforums.org/showthread.php?t=646755&highlight=update+kernal) but when I run the script it tells me my kernel is the latest, when I know it's not.

So, how do I update the Ubuntu kernel to the latest version?   And yes, I have searched the forum to no avail.

Advice appreciated

I am guessing that you upgraded rather than did a fresh install and during the process you elected to keep your original menu.lst.  If you will check your menu.lst list file, I believe you will find Hardy's correct kernel and all you need to do is point grub to it.

Bob

---

### Post by The Minder on 2008-05-13
vorgusa:
I checked as you suggested... everything appears correct

bobnutfield
This was a fresh install on a new hard drive.  I originally had problems with latest kernel and found the easiest option was to edit the menu.lst file.   Unfortunately, I deleted rather than commenting out the lines pointing to the latest kernel and now can't seem to get them back... my bad!   I have time on my hands so I might try another fresh install on a new hard drive... I have plenty of hardware laying around.

---

### Post by The Minder on 2008-05-13
Problem solved with a fresh install on a new hard drive.   This is like taking a sledge hammer to an acorn, but it worked.

---

