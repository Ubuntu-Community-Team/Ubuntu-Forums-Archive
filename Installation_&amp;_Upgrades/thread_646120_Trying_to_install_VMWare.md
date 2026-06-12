---
title: "Trying to install VMWare"
date: 2007-12-20
forum: Installation &amp; Upgrades
---

### Post by Drethon on 2007-12-20
I'm new at Ubuntu and linux in general and trying to install VMWare.  I reached the point of telling it where the include files are and get the follow error.  How would I resolve this?

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.20-15-generic/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.20-15-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.

---

### Post by yabbadabbadont on 2007-12-20
[http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto](http://ubuntuforums.org/showthread.php?t=183209&highlight=vmware+howto)

You might read through that tutorial and see if it helps.

---

### Post by Drethon on 2007-12-20
I installed the new headers as directed by the link but little change, its just complaning about v 16 instead of 15:

What is the location of the directory of C header files that match your running 
kernel? [/usr/src/linux/include] /usr/src/linux-headers-2.6.20-16-generic/include

The directory of kernel headers (version @@VMWARE@@ UTS_RELEASE) does not match 
your running kernel (version 2.6.20-16-generic).  Even if the module were to 
compile successfully, it would not load into the running kernel.

---

### Post by yabbadabbadont on 2007-12-20
Try using just:

/usr/src/linux-headers-2.6.20-16-generic

and see if it helps.

---

### Post by Drethon on 2007-12-20
Linux didn't seem to happy with the 'uname -r' so I ran it manually and put the return from that into the apt-get command, 2.6.20-16-generic is what was installed.  Makes me wonder if the kernal build is slightly off but I'm too unfamiliar with Linux to know.

---

### Post by Drethon on 2007-12-21
No one can help?

---

