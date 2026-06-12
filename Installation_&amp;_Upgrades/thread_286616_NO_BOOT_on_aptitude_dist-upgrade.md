---
title: "NO BOOT on aptitude dist-upgrade"
date: 2006-10-28
forum: Installation &amp; Upgrades
---

### Post by aaronbeekay on 2006-10-28
I've been holding out on upgrading to Edgy on my desktop machine until the final release just to be safe: didn't want any problems.

The night of the final release, I ssh'd in to the box, modified sources.list to change all "dapper"s to "edgy"s, and ran "sudo aptitude dist-upgrade" twice.

It still showed some errors after a bit, so I ran it a few more times to clear up whatever it could (mostly Python dependencies?) then had to go and forgot about it.

I came to see the machine in RL today and did a reboot. It hits the "Ubuntu" usplash progress bar but makes no progress. After sitting there for five minutes or so, it drops me into a Busybox shell (no apt!)

Trying to mount my hard drive "sudo mount -t ext3 /dev/hdd1 /media/HD" returns "mount: Mounting failed, invalid argument" (yes I did make /media/hd)

I'm stumped at this point, and since I have a lot of stuff on this machine I'd like to avoid a backup and reinstall however I can. Ideas, guys?

---

### Post by seaside on 2006-10-28
Sure hda1 is the data partition and not swap?

---

### Post by aaronbeekay on 2006-10-28
Found the problem, actually: my main partition had been reset to /dev/hdc instead of /dev/hdd, AND in GRUB all the references were to hda.

I've had this issue before, but the dapper boot screen showed the info I needed to fix it, while Edgy's just sat there.

Lesson: always try recovery/single-user mode, and always check drive letters.

---

