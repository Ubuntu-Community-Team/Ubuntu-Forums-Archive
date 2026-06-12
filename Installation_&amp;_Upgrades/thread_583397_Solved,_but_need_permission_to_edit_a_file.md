---
title: "Solved, but need permission to edit a file"
date: 2007-10-20
forum: Installation &amp; Upgrades
---

### Post by JGT on 2007-10-20
Hi

I'm trying to follow the following advice

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862)

i.e. add a couple of lines

import os
import dbus

to the following file

/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py

I don't seem to have permission to edit the file.

Sorry for silly question, but can you please tell me how to do this. I'm not experienced enough to edit a file from the command line, and I don't know how to log in as root (can't seem to do it from the log in screen).

Thanks

John

---

### Post by confused57 on 2007-10-20
> **JGT said:**
> Hi

I'm trying to follow the following advice

[https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862](https://bugs.launchpad.net/ubuntu/+source/update-manager/+bug/118862)

i.e. add a couple of lines

import os
import dbus

to the following file

/usr/lib/python2.5/site-packages/UpdateManager/DistUpgradeFetcher.py

I don't seem to have permission to edit the file.

Sorry for silly question, but can you please tell me how to do this. I'm not experienced enough to edit a file from the command line, and I don't know how to log in as root (can't seem to do it from the log in screen).

Thanks

John

Press "Alt+F2", enter:
```
gksudo nautilus
```

You should then be able to add the lines as root...be sure to close nautilus as soon as you make the changes.

---

### Post by JGT on 2007-10-20
Many thanks

John

---

### Post by erdley on 2007-11-24
Am having the same permission problem in trying to edit a file, but am a rank beginner and don't know what happens after I type 
gksudo nautilis into the terminal.  I get a choice of "run in terminal" and other, and the need to enter my password, but can't get the text editor to edit the file in question because I still don't have permission to do so, no matter what I have done so far.  A little more detailed help here would be very much appreciated.

---

