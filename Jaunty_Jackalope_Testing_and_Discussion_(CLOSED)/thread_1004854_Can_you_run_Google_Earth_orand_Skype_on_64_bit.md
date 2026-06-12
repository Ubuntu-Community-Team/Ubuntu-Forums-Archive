---
title: "Can you run Google Earth or/and Skype on 64 bit?"
date: 2008-12-07
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by mdurham on 2008-12-07
When running Skype or GoogleEarth I get this >  error while loading shared libraries: libuuid.so.1: cannot open shared object file: No such file or directory

I'm using Ubuntu64
Cheers, Mike

---

### Post by amauk on 2008-12-07
yes,
in fact I run both skype & google earth on 64bit
you do need the 32bit compatibility libraries, though

easiest way to get them, is to install wine
installing wine will pull in all the necessary 32bit libs
(you can then uninstall wine - and the 32bit libs will remain)

for skype, you need to download the generic linux binaries (Ie. not the pre-packaged deb that skype provides for Ubuntu)
download the generic binaries, bung them in your home folder (I use ~/apps for example)
and manually create a menu item for skype

---

### Post by ronacc on 2008-12-07
I think we need to file a bug on that . libuuid is there just a later version , I and others have goten that error with several  things .

---

### Post by amauk on 2008-12-07
oops,
got to this thread through "new posts"
didn't realise it was about Jaunty

(just assumed it was in one of the beginners forums :oops:)

---

### Post by ronacc on 2008-12-07
filed bug#306101 add your comments and confirm .

---

### Post by mdurham on 2008-12-07
> **ronacc said:**
> filed bug#306101 add your comments and confirm .
Will do.

---

### Post by Naddiseo on 2008-12-07
See bug #298611

---

### Post by ronacc on 2008-12-07
I am already at the version of the lib that they recommend to "fix" the problem , the 64bit build though not the i386.
thanks for the referecce though .

---

### Post by Naddiseo on 2008-12-07
Yes, that bug is the 64bit issue. From what I can tell, it's the 32bit library for the 64bit platform.

---

### Post by ronacc on 2008-12-07
ok I see what you are saying , the triager will mark it as a dupe , but the real problem resides with 64bit version of libuuid not the ia32pkg that bug 298611 points at .

---

