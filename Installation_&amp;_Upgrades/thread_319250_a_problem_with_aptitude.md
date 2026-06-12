---
title: "a problem with aptitude"
date: 2006-12-15
forum: Installation &amp; Upgrades
---

### Post by mykalreborn on 2006-12-15
when i tried to install something with apt-get i got a message saying the system cannot find qt, saying something about kde and asking if the libqt-perl is installed. so i installed it and now it gives this message, right after it downloads the package:
```

Fetched 716kB in 13s (52.2kB/s)
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
X Error: BadDevice, invalid or uninitialized input device 167
  Major opcode:  145
  Minor opcode:  3
  Resource id:  0x0
Failed to open device
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 2 during global destruction.
Selecting previously deselected package libsvn0.

```
and as you can see it carries on with installing the package. what i want to know is what the error is and if it's going to affect my system__

---

### Post by Bosonator on 2006-12-30
It's a problem that's typically encountered after one uses "automatix" or "easyubuntu". This thread describes how to fix it:

[http://www.ubuntuforums.org/showthread.php?t=208655](http://www.ubuntuforums.org/showthread.php?t=208655)

I only had the error that says
```
DESTROY created new reference to dead object ' Qt::VBoxLayout', <> line 6 during global destruction.

```

So you may have to do some more searching to completely fix your problem. Try entering the terms "Qt::VBoxLayout" in the search bar and look for threads that refer to wacom tablets (sorry I can't give you a specific thread, but I navigated away from my original search page :) )

---

### Post by mykalreborn on 2006-12-31
oh! i see! thanks! i thought it was something wrong with my system ^_^

---

