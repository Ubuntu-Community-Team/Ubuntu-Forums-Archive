---
title: "partman: &quot;No volume groups found&quot; during installation"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by misterPhyrePhox on 2006-09-20
Hello, I am trying to install Ubuntu 6.06 Server on a very old Micron PC, but partman does not seem to like my hard drive. After the installer starts up partman, it just hangs; nothing happens. In the log, it says that no volume groups were found.
My HD model number is "WDC WD102BA." I don't know that much about hardware, so if there's any additional information I can provide, please tell me how I can figure it out (I have windows installed on the system currently, so I got the model number from the device manager).
Here's an excerpt from the end of the system log:
```
Sep 20 12:28:01 partman: File descriptor 3 left open
Sep 20 12:28:01 partman: File descriptor 4 left open
Sep 20 12:28:01 partman: File descriptor 5 left open
Sep 20 12:28:01 partman: File descriptor 6 left open
Sep 20 12:28:01 partman:   No matching physical volumes found
Sep 20 12:28:01 partman: File descriptor 3 left open
Sep 20 12:28:01 partman: File descriptor 4 left open
Sep 20 12:28:01 partman: File descriptor 5 left open
Sep 20 12:28:01 partman: File descriptor 6 left open
Sep 20 12:28:01 partman:   
Sep 20 12:28:01 partman: No volume groups found
Sep 20 12:28:01 partman:   Reading all physical volumes.  This may take a while...
```
I have the full syslog and the partman log, if either of those would shed any light on the situation.
I searched the Ubuntu forums, and found some thread which talked about "LVM" or something. I think the issue may have been related to a RAID setup in the thread I read, but I only have one hard drive on my machine.
So could anyone help a linux noob out?

---

### Post by misterPhyrePhox on 2006-09-21
Bump pretty please!

---

