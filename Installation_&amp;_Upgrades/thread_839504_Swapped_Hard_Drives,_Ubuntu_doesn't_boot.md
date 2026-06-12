---
title: "Swapped Hard Drives, Ubuntu doesn't boot"
date: 2008-06-24
forum: Installation &amp; Upgrades
---

### Post by CulleyS on 2008-06-24
Hi there,

Here is my situation.  My Ubuntu server failed due to a hardware issue.  I have an identical server to use in its place.  I swapped the harddrives (four in total) into the new, functional server.

When I boot up, GRUB either isn't found or is bypassed.  I am taken to what looks like an Ubuntu LIVE CD screen, where I can install Ubuntu, Rescue, Check CD, etc. etc.  There is no Live CD in the drive.

I go into Rescue mode and when I get a shell prompt, I can see my current filesystem on the hard drive.  All of my old files, mounts, etc.

My question is, how do I "rescue" my Ubuntu install? As I said, the old server is dead, so I can't put the drives back in there and get Ubuntu to load.  I can't even get a BIOS prompt on the old server.

I think it might be something as simple as reconfiguring GRUB on the new server, but I'm not sure where to get started.

I can provide more info if necessary.

Thanks,

Culley

---

### Post by timcredible on 2008-06-24
well, if you want to work on grub, super grub disk can do that, but i would look in the bios on the new server first and make sure that it knows you have different hard drives.  after all, grub moved with the drives, so unless the drives took damage, grub should be fine.  that's assuming all the drives are in the same order as in the old server?

---

### Post by CulleyS on 2008-06-24
Yeah, the drives were moved in the same order.  

Thanks, I'll take a look at the BIOS and make sure it recognizes the new hard drives.

---

