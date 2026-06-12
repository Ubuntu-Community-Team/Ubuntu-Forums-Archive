---
title: "/var/lock vs mountkernfs.sh"
date: 2010-05-03
forum: Installation &amp; Upgrades
---

### Post by scifan on 2010-05-03
OK...

I've upgraded from 9.04 to 10.04...

The upgrade process was kind of lame because I had to step through 9.10 to upgrade to 10.04.

I had to re-compile a couple of applications because they required libraries that had been updated... this all works fine

Now I'm struggling with a problem I see MANY people having issues with... and that's /var/lock/mrtg ends up owned by ROOT and is set at 755...

How in the world can I set this to default to something else?

I don't use the "Standard" configuration for MRTG as I have ~170 devices I want to monitor and I'm used to the configuration I have with a separate configuration file for each switch... 

I need this system to be able to reboot and come up without user intervention.

I don't want to implement a rc.local KLUDGE, and the suggested mod to my cron-event doesn't seem to work because the directory is already owned by root... and I'm not running mrtg as root.

In 9.04, I altered /etc/init.d/mountkernfs.sh, but that doesn't exist under 10.04.

I can't figure out where this tmpfs is being mounted from, and I'm very frustrated that this has been altered.

Where can I make the changes that USED to reside in mountkernfs.sh under 10.04?

help!

---

### Post by scifan on 2010-05-03
Ok... I found what I wanted..

/lib/init/fstab

I've added this line: 

none            /var/lock/mrtg            tmpfs           mode=1777   0 0


What would I need to add to define a specific user for the folder so I can drop the permissions back to 0755 so mrtg will work like it's supposed to when it's not run as a "root" user?

---

