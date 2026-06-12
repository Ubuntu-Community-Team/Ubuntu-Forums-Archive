---
title: "Setting up a software RAID 1"
date: 2007-06-21
forum: Installation &amp; Upgrades
---

### Post by Midahed on 2007-06-21
I've been using Ubuntu 7.04 Feisty 64-bit for a couple of weeks.  My Ubuntu PC is now in danger of becoming my main workhorse, so I'd like to build a raid to protect against drive failure.

I've read loads of threads on setting-up raids, but they all seem to start with a fresh install.  None answer the question of how to configure a raid based on an existing single-drive system.

It took me quite a time to get the system working (especially the 64-bit Firefox/lack of Flash Player problem, etc), so I'd prefer not to have to start an installation from scratch.

Are there any software raid programs for Ubuntu that allow a new blank disk to be installed and a raid built using that new disk and the existing Ubuntu system and data disk?

Thanks,

Mike

---

### Post by Midahed on 2007-07-19
Well, if it's OK with everyone, I'll answer my own post!

I now have my 7.04 Feisty Desktop system running software RAID1 and I **didn't** have to start with a clean re-install.  What's more, it's based on the default installation (that only has a root and swap partition), but it works fine like that.  I didn't have to set-up a separate non-RAIDed /boot partition.  It runs like a dream and boots off either disk.

For anyone else who, like me, is a relative newbie to the Linux environment, but wants to RAID an existing system without having to re-install, the full story is here [http://ubuntuforums.org/showthread.php?t=504463](http://ubuntuforums.org/showthread.php?t=504463)

Mike

---

