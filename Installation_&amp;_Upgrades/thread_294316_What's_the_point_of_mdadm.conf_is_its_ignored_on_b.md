---
title: "What's the point of mdadm.conf is its ignored on boot?"
date: 2006-11-06
forum: Installation &amp; Upgrades
---

### Post by wkulecz on 2006-11-06
Adding a raid5 array for data to an existing boot from raid1 system broke it!

See: [http://www.ubuntuforums.org/showthread.php?t=289720](http://www.ubuntuforums.org/showthread.php?t=289720) for the details.

Unplugging the raid5 array lets it boot.  Removing my raid5 entry from /etc/mdadm.conf didn't fix the md re-assignmet problem when I shutdown and rebooted with the raid5 now attached.

What's the point of mdadm.conf if its md assignments are ignored on boot up!
This of course means /root= is wrong on boot and fstab is wrong should you force a bootup with an option.

--wally.

---

