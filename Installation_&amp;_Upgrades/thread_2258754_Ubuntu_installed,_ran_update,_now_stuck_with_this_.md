---
title: "Ubuntu installed, ran update, now stuck with this error ata3.00: status: { DRDY ERR }"
date: 2014-12-30
forum: Installation &amp; Upgrades
---

### Post by lithiumKid1976 on 2014-12-30
hi
i finally got ubuntu14.10 installed on a ssd.
had a quick look around, changed the desktop etc. everything running well.
then i ran an update, system asked for a reboot, and now im stuck with this..


ata3.00: status: { DRDY ERR }

any ideas,,,,,?
thanks

---

### Post by schragge on 2014-12-31
[post=6963209]Here[/post] is one possbility. But the file to put that line in should better be named */etc/modprobe.d/ata.conf*.
Other posts in the same thread suggest adding boot parameters *acpi=off* and *noapic* to kernel command line.

---

### Post by lithiumKid1976 on 2015-01-01
powered on pc, to have a look at this today, and its working. 
in the end i didn't do anything bar moving the sata cable on the MB.

its a Christmas miracle!

---

### Post by lithiumKid1976 on 2015-01-04
update
issue kept returning.
in the end, removed the old ide 500gb storage disk, and now the issue is gone.
so, looks like ill be in the market for a new storage disk.

---

### Post by lithiumKid1976 on 2015-01-04
update
issue kept returning.
in the end, removed the old ide 500gb storage disk, and now the issue is gone.
so, looks like ill be in the market for a new storage disk.

---

