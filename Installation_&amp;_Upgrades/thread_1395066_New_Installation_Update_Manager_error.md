---
title: "New Installation Update Manager error"
date: 2010-01-31
forum: Installation &amp; Upgrades
---

### Post by djdan2k8 on 2010-01-31
Hi all at the moment im using 8.10 intrepid just done a fresh install and when trying to use update manager the loading bar goes to the end then just closes it does this most times.

When i finally able to get onto it i allways end up with errors whilst installing various updates .

This details of my system:

Release Ubuntu 8.10 (intrepid)
Kernel Linux 2.6.27-7-generic
Gnome 2.24.1

_**Hardware:**_
Memory: 1008.6 MiB
Processor: Intel (R) Premium (R) 4 CPU 3.06 GHZ

_**System Status**_: 
Available Disk Space 169.1 GB

If anyone could help this would be great as i really do love ubuntu and dont want to have to go back to using Windows XP.

Thanks in advance Daniel.:D

---

### Post by wojox on 2010-01-31
Open your Terminal ( Applications > Accessories > Terminal ) and copy and paste this command 

```
sudo apt-get update && sudo apt-get upgrade && sudo apt-get dist-upgrade
```

Any errors post back here.

---

### Post by djdan2k8 on 2010-01-31
Thanks for the very quick reply

Just doing it now will paste errors if any

---

### Post by djdan2k8 on 2010-01-31
I have used that command and updated no errors seemed to have happend but i still get the update manager closing i have attached the info from the terminal window if it helps at all. If i can provide anymore info just ask.

---

### Post by wojox on 2010-01-31
Did you reboot after the updates?

---

### Post by djdan2k8 on 2010-01-31
Yes as soon as they had done and the restart icon appeared in the toolbar

---

### Post by djdan2k8 on 2010-01-31
i dont know if this helps but it also happens with Add/Remove programs and the gdebi package installer

---

### Post by djdan2k8 on 2010-01-31
I have just looked in my system logs and it shows an error in there for update manager

Jan 31 19:46:40 djdan2k8-desktop kernel: [ 1400.309038] update-manager[6667]: segfault at 0 ip 08087d01 sp bfd92cc0 error 6 in python2.5[8048000+fc000]

---

### Post by djdan2k8 on 2010-02-01
JUst a quick reply i decided to do a fresh install and at the begining did a memory test and found my ram stick to have lots of memory faults so have now got a 512 MiB stick in and update manager seems ok just updating to 9.04 to see if alls well.

---

