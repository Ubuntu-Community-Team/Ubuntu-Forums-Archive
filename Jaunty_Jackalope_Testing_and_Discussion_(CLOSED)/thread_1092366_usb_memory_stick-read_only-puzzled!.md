---
title: "usb memory stick-read only-puzzled!"
date: 2009-03-10
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by ancleessen4 on 2009-03-10
I copied some files to my removable usb memory stick.
No problem I can read them OK.
I then wanted to update the files and I am told the disk is read only:-?
I have tried sudo nautilus but the stick remains read only.

Any ideas??

---

### Post by aethralis on 2009-03-10
Same thing happened to me yesterday. After unmount I mounted it again and everything was Ok.

---

### Post by ancleessen4 on 2009-03-10
just tried unmount/mount-same problem...

---

### Post by nyarnon on 2009-03-10
Check user and permissions on the files.

---

### Post by ancleessen4 on 2009-03-10
Here is a screenshot. I have tried changing permissions but the stick remains read only.

[IMG]http://ancleessen4.com/myuploads/Screenshot-pension+benefits%20Properties.png[/IMG]

---

### Post by kurty_77 on 2009-03-10
there was probably an unclean mount at some point. you need to run fsck or chkdsk (MS) or remount with the force option i think

---

### Post by ancleessen4 on 2009-03-10
OK-as I did not have much data on the stick a quick VMWare fire up into Windows XP and a reformat of the stick.
Copied the files to the stick again and alll appears to be OK-reading and writing.

Still a bit confused as to wht this happened though...

---

### Post by reg-sux on 2009-03-10
is it VFAT?

---

### Post by ancleessen4 on 2009-03-10
yes

---

