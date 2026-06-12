---
title: "dbus failure"
date: 2009-09-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by bumanie on 2009-09-16
Karmic had a major break with recent update. Initially had a frozen GUI (no mouse) with message during update that grub 1.97-beta3 did not install nor did apic. Did a further update later from tty1 - now have following message > init: Unable to connect to the system bus: Failed to connect to socket /ver/run/dbus/system_dbus_socket: No such file or directoryI think grub is now installed after manually running sudo update-grub2 - not sure about apic. Anyone know what the message means? Google has not been very helpful.

---

### Post by psyke83 on 2009-09-16
There are *many* threads on the breakage introduced in the last day or so. Check them before posting.

---

### Post by bumanie on 2009-09-16
I did not see any with the same error message - there are others posts, but the error messages were different as far as I could tell - may be I missed something, but I did read number of them and none that I saw had the dbus message. If you have seen one, I am quite happy to be pointed to it and I will read it. And I did put the error into search, and nothing similar came up.

---

### Post by dino99 on 2009-09-16
got this when i update repos:

Failed to open connection to "system" message bus: Failed to connect to socket /var/run/dbus/system_bus_socket: No such file or directory

E: Problem executing scripts APT: :Update: Post-Invoke-Success '/usr/bin/dbus-send --system --dest=org.debian.apt --type=signal /org/debian/apt org.debian.apt.CacheChanged'

E: Sub-process returned an error code

---

### Post by psyke83 on 2009-09-16
> **bumanie said:**
> I did not see any with the same error message - there are others posts, but the error messages were different as far as I could tell - may be I missed something, but I did read number of them and none that I saw had the dbus message. If you have seen one, I am quite happy to be pointed to it and I will read it. And I did put the error into search, and nothing similar came up.

[http://ubuntuforums.org/showthread.php?t=1267183&highlight=dbus](http://ubuntuforums.org/showthread.php?t=1267183&highlight=dbus)

I recommend that you do an update (but keep in mind that regional mirrors may be out of date), as people have reported these problems to be fixed in the latest batch of updates.

---

### Post by bumanie on 2009-09-16
Thanks for that. I have updated since the first lot of errors, that is when this present error occurred. There are no more updates available at present, but I will try later today or tomorrow.

---

