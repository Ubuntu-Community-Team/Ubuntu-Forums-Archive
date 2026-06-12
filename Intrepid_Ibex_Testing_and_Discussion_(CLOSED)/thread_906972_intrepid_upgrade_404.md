---
title: "intrepid upgrade 404?"
date: 2008-09-01
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by eternal_sage on 2008-09-01
i decided to test intrepid on my laptop, as i pretty much use my desktop for everything and my laptop is kinda just for goofing off with. it upgraded fine (this was a week or two ago) but this weekend i got a upgrade in the update manager "http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfree86-driver-synaptics/xserver-xorg-input-synaptics_0.15.0+git20080820-1ubuntu2_i386.deb" which i got a 404 error for. has anyone else gotten this error?

i did set up a new wireless router, so i may have some issues with port forwarding (if its not http or ftp based, but i can't find information on this). if anyone knows what is up with this, or has gotten a similar problem, please let me know!

---

### Post by Sef on 2008-09-01
Moved to  Intrepid Ibex Testing and Discussion.

---

### Post by eternal_sage on 2008-09-01
thanks for moving me to the right place. i somehow didn't even notice this forum (go figure).

---

### Post by olskar on 2008-09-01
Strange..

The correct adress is "http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfree86-driver-synaptics/xserver-xorg-input-synaptics_0.15.0+git20080820-1ubuntu4_i386.deb" and not "http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfree86-driver-synaptics/xserver-xorg-input-synaptics_0.15.0+git20080820-1ubuntu2_i386.deb"

Try to download the package from the adress that is correct, install that and try to update again?

---

### Post by scradock on 2008-09-01
[QUOTE=eternal_sage;5704046]i decided to test intrepid on my laptop, as i pretty much use my desktop for everything and my laptop is kinda just for goofing off with. it upgraded fine (this was a week or two ago) but this weekend i got a upgrade in the update manager "http://us.archive.ubuntu.com/ubuntu/pool/main/x/xfree86-driver-synaptics/xserver-xorg-input-synaptics_0.15.0+git20080820-1ubuntu2_i386.deb" which i got a 404 error for. has anyone else gotten this error?[QUOTE]

That version of the xserver-xorg-input-synaptics driver didn't work in 64bit Intrepid, and was quickly replaced by a later one.

If you are still on the -1ubuntu1 version you can try upgrading again - you should get a version like -1ubuntu4.

---

### Post by eternal_sage on 2008-09-01
cool. although i'm not on a 64 bit machine.... so maybe my problem runs a little deeper than that... lol

i'll check on it. thanks guys. i'll post back if i have any success. or not... :D

---

### Post by eternal_sage on 2008-09-01
this seems to have fixed it! thanks guys!

---

