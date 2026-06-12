---
title: "Help!  Something changed mdadm /dev/md drive assignments, won't boot!"
date: 2006-10-31
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2006-10-31
System was working perfectly for about ten days, had three mdadm created raid1 partitions:

/ on /dev/md0 raid1, 2 drives
swap on /dev/md1 raid1, 2 drives
/home on /dev/md2 raid1, 2 drives

I shut the system down to add three SATA drives and rebooted to setup /data on /dev/md3 raid5, 3 drives.  All seemed to go smoothly, I copied a bunch of images to the raid5 and was using picasa.  I left it scanning the directories of images I'd copied over.  When I returned it had crashed with an error dialog that effectively locked up the X server.  I did a reboot from the Gnome menu.

Unfortunately the reboot failed with "no init process" because the /dev/md assignments had changed!

mdadm /dev/md0 has been started with 3 drives
mdadm /dev/md1 has been started with 2 drives
mdadm /dev/md2 has been started with 2 drives
mdadm /dev/md3 has been started with 2 drives

effectively making the raid5 be my / disk which of course won't work.


I tried booting Knoppix but it wouldn't give a display with the LCD panel I was using.  Any ideas?  I'll move an older 1024x768 panel when I get some time and try Knoppix again.  But I'm at a loss as to why this had changed, I'd added the md3 raid5 3 drives line to /etc/mdadm/mdadm.conf as soon as /proc/mdstat said the raid5 build was complete.

--wally.

---

