---
title: "DVD CD-Rom Keeps getting accessed by EVMS"
date: 2008-01-12
forum: Installation &amp; Upgrades
---

### Post by dayhawk4 on 2008-01-12
I have a new Dell Inspiron system with Ubuntu installed.  Waiting for some new hard-drives for a new RAID system I wanted to set-up, I installed EVMS.  After installation and reboot, the CD-DVD drive kept trying to access.  Hitting eject, the system would immediately pull the drive back in.  Finally, the system would all but crash.  Going to another terminal using alt-crt F1, I got pages of kernel errors.  

I tracked this problem down to EVMS....  Another posts reads that if you remove evms and associated packages, the problem goes away.  I needed this package though.  I couldn't use the configur tools because the daemon was being used by evms-activate process (which kept dying and re-spawning as different process numbers)

Solution....  the file /etc/evms.conf has a line called include.  It looks like the following:

include [ * ]
exclude [ ]

By removing the asterisk which automatically checks all devices for a raid array, and putting a star in the exclude in the activate section, the access immediately stopped...


Now I can get into all of my administrative tools, and setup the system to begin with.....

The star is no good in include when you first begin if you haven't setup a raid array yet because you can't even get into the tools to set it up.  Additionally, it raises trouble....

dayhawk4

---

