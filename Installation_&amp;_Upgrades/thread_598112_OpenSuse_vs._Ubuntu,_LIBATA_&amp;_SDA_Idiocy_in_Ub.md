---
title: "OpenSuse vs. Ubuntu, LIBATA &amp; SDA Idiocy in Ubuntu!"
date: 2007-10-31
forum: Installation &amp; Upgrades
---

### Post by plamen_todoroff on 2007-10-31
Taken from the OpenSUSE 10.3 Release Notes: "libata powers now your IDE devices:Libata uses /dev/sda for the first harddisk, instead of /dev/hda. If you have a disk with more than 15 partitions, they will not be handled automatically at this moment. You can disable libata support by booting the kernel with the following parameter:
hwprobe=-modules.pata

After this, you will see all your 15+ partitions."

Nice and simple, and working.

I really like Ubuntu and I don't want to separate with it, but for the last two months I've been searching this forum and the wikis for the problem I have: I'M HAVING MORE THAN 15 PARTITIONS AND OBVIOUSLY IT'S A PROBLEM IF YOU'RE USING UBUNTU! And I have found nothing that could help me use all my partitions with Gutsy Gibbon. Even worst, I haven't met a single thread that focuses on this driving-multidistro-users-crazy problem! Yes, it's a problem! The way the new libata subsystem is imposed on us is just ridiculous! I've posted some threads in different categories in this "so tight and centralized community forum" and never gotten a single answer how this "everything is SCSI" standard could be walked around. Disk are 1 TB big now fellas! Instead of increasing the number of available partitions from 63 (PATA) your implementation of the libata subsystem (NO MORE THAN 15 PARTITIONS)  is a regression in it's pure form.

When will, if not will ever, Ubuntu is going to do something about this, similar to the way the OpenSUSE developers have handled the issue?

I desperately want to install Gutsy, but OMG, it has to be installed on partition number 17 and 18, and OMG, THEY ARE NOT HANDLED RIGHT NOW!

---

### Post by nocturn on 2007-10-31
I'm sorry to hear about your problems, but have you taken the trouble to file a bugreport?

That will be the only way to actually reach the developers themselves.

---

### Post by plamen_todoroff on 2007-10-31
Please, there must be somebody that is aware of what's going on with the kernel and libata in particular. I've read so many threads that people complain about same problems (like hda/sda transition after update, and so on) and all of this is connected to this libata-pata drivers, but nobody sheds a light on this in ubuntu community.

---

