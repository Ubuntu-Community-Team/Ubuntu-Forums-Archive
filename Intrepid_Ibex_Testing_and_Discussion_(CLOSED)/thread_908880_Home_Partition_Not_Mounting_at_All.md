---
title: "Home Partition Not Mounting at All"
date: 2008-09-02
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by Sef on 2008-09-02
I have a 24 GB home partition on my sole hard drive.  However, it is not mounted, and when I go to Places > 24.0 GB Media, nothing happens.  I can I get it mounted and working.  

Thank you in Advance.

---

### Post by ronacc on 2008-09-02
the not mounting from place>computer>**media is a bug or regression take your pick ,a normal user cannot mount any internal partitions, see this thread for a workaround  [http://ubuntuforums.org/showthread.php?t=905861](http://ubuntuforums.org/showthread.php?t=905861)  . for the /home not mounting try removing quiet and splash from the boot line and see what happens , usplash isn't respecting fsck and tries to mount a drive in the process of being checked and also seems to cause problems on some boxes , several posts on this .

---

### Post by Sef on 2008-09-03
Thank you.  I was not sure if it was the same one or not.

---

### Post by Gina on 2008-09-03
I get that at times too but haven't had the time lately to sort things out.  Getting it on my AMD64 ATM, laptop refuses to boot Intrepid, P4 is fine.

---

### Post by plun on 2008-09-03
Fix out

> Changes: 
 sysvinit (2.86.ds1-59ubuntu5) intrepid; urgency=low
 .
   * debian/initscripts/lib/init/usplash-fsck-functions.sh, get_fsck_status():
     fsck -C recently started to report a fourth parameter (current device)
     which was not expected by the read shell command, causing abortion of the
     script due to a division by zero error. Now use "read pass cur max tail"
     to allow for arbitrary extra info in the fsck progress lines.
     (LP: #255563)


[https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006378.html](https://lists.ubuntu.com/archives/intrepid-changes/2008-September/006378.html)

---

