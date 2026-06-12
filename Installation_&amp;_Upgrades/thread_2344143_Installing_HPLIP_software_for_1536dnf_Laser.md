---
title: "Installing HPLIP software for 1536dnf Laser"
date: 2016-11-22
forum: Installation &amp; Upgrades
---

### Post by RichardET on 2016-11-22
The issue is scanning.  The printer is setup as a network printer and the stock driver for Ubuntu mate works well for printing, but scanner software cannot connect.  Its no problem on Windows.  Thus I downloaded the driver available from HP for Linux, but it wants to add many dependencies.  One is dbus support.  Should I do this or not?

---

### Post by RichardET on 2016-11-23
I solved this - I downloaded the run file from HP and let it run under a terminal screen, now scanning works well.  Also I suggest running the script from /tmp, otherwise you will have to clean up after its installed.

---

