---
title: "access to /documents partition"
date: 2007-07-24
forum: Installation &amp; Upgrades
---

### Post by peas on my plate on 2007-07-24
This is my first post; I have always been able to find the answers to my questions before- Thanks forums!

This is my second Ubuntu install.  The first went perfectly.  This time I installed Fiesty, and decided to create a /documents ext3 partition in addition to my windows xp ntfs partition and ubuntu ext3 partition.

I cannot access the /documents ext3 partition in either ubuntu or windows.  It is likely that I mounted it incorrectly.  Also, there is a lost+found folder in that directory that I cannot access nor have I ever seen it before.

Here's the output from the df command:

```
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sda3              7692908   2064640   5237488  29% /
varrun                  517756       108    517648   1% /var/run
varlock                 517756         0    517756   0% /var/lock
procbususb              517756       112    517644   1% /proc/bus/usb
udev                    517756       112    517644   1% /dev
devshm                  517756         0    517756   0% /dev/shm
lrm                     517756     33788    483968   7% /lib/modules/2.6.20-15-generic/volatile
/dev/sda4             38456340    180240  36322596   1% /documents
/dev/sda1             29302524  10368248  18934276  36% /media/sda1
```

Thanks in advance!!:)

---

### Post by Pumalite on 2007-07-24
Lost+Found is probably it. Change permission: sudo chmod 777 /<directory>/lost+found. Then check again. Post back.

---

### Post by peas on my plate on 2007-07-24
Ran the command:
```
sudo chmod 777 /documents/lost+found
```

It went in fine, but when I tried to save a open office document, it gives the error "general inpou/output error"

The path I am taking is filesystem, documents.

thanks for helping!

---

### Post by Pumalite on 2007-07-24
make sure 'documents' is a directory in root (/)

---

### Post by peas on my plate on 2007-07-24
Okay, here's some progress:

I can now open the mysterious lost+found folder in /documents *and* read and write to it.  The funny thing, though, is that I can't read or write directly into the /documents directory.  I can't even create a folder there.

I've attached a screen shot of the file browser.  hello2 is the document I've been playing with.

---

### Post by Pumalite on 2007-07-24
Just do this: sudo chmod 777 /documents ( if that's where 'documents' is )

---

### Post by peas on my plate on 2007-07-24
Worked perfectly!!  Thanks for your help.  It would have taken me a LONG time to find that command.:)

---

