---
title: "cdrom mount point"
date: 2011-10-14
forum: Installation &amp; Upgrades
---

### Post by BobvanderPoel on 2011-10-14
Not sure where this should be posted ... but installation/upgrades probably makes as much sense as anything....

Here's the problem: I insert a CD in the drive. It's a 11.10 upgrade disk. The system finds it and mounts it as /media/Ubuntu 11.10 i386

Now, the update manager launches ... and it's expecting a CD at /media/cdrom.

So, it craps out with a message about no internet :)

I can work around this by manually mounting the cd:

    sudo mount /dev/cdrom /media/cdrom

and then restarting the update manager.

Do I have something set up wrong? I've noticed this behaviour when I was trying to do some updates from a DVD using synaptic. Never did figure it out.

---

