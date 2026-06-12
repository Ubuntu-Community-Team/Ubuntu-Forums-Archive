---
title: "quit installation?"
date: 2012-10-16
forum: Installation &amp; Upgrades
---

### Post by Carlos Araujo on 2012-10-16
Ubuntu installation Fails.

boot-repair info details:

[http://paste.ubuntu.com/1283981/](http://paste.ubuntu.com/1283981/)

On Dell Inspiron 5423

---

### Post by oldfred on 2012-10-16
This looks like another Intel SRT system. It uses a RAID configuration and the standard desktop installer does not have the RAID drivers as RAID is usually servers. The alternative installer is text based but also has RAID drivers.

But some have just turned the RAID off, removed the RAID meta-data and then installed. Some other threads where users discuss how they did it.

 Intel Smart Response Technology & Dell XPS
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2036204](http://ubuntuforums.org/showthread.php?t=2036204)
[http://ubuntuforums.org/showthread.php?t=2020155](http://ubuntuforums.org/showthread.php?t=2020155)
Some info on re-instating 
[http://ubuntuforums.org/showthread.php?t=2038121](http://ubuntuforums.org/showthread.php?t=2038121)
[http://ubuntuforums.org/showthread.php?t=2070491](http://ubuntuforums.org/showthread.php?t=2070491)
> Disable the RAID, for me it was using the Intel rapid management thingy and telling it to disable the acceleration or the use of the SSD. If you have a different system, just disable the RAID system then install Ubuntu. Once installed you can then re-enable it.

> You will need to use the dmraid command prior to running the Ubuntu Installer so that it will be able to see the partitions on the drive because otherwise with the raid metadata in place it will see the drive as part of a raid set and ignore its partitions.


---

