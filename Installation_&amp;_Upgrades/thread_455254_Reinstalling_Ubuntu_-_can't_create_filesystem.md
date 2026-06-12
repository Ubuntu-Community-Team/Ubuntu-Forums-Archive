---
title: "Reinstalling Ubuntu - can't create filesystem"
date: 2007-05-26
forum: Installation &amp; Upgrades
---

### Post by lazyart on 2007-05-26
I've been running Ubuntu for a few months now, starting to the hang and feel of things.

I'm resurrecting a box here that I tried to set up as a Dapper server.  I'm actually going to give this machine to someone else but before doing so I'm installing Kubuntu (PIII 833, 320 mb ram).  I pop in the live CD and tell it to install.  I zip thru the dialogs and then I'm notified that it can't create exf3 file system on /media/sda1.

Hmm... Now I had looked around on the drive before I started installing and thought maybe I shouldn't have, so I rebooted and went directly into install.

Again, it said it couldn't create the filesystem.  So I put on my linux hat (only about 7 months old mind you) and started delving around.  I browse over to the mount point to see what's going on there.  I noticed the red icon telling me I didn't have write permissions in there.  It's belongs to root:root and I and ubuntu:ubuntu.  WIth nothing to lose, I drop down into the terminal shell and type```
sudo chown ubuntu:ubuntu /media/sda1
```

Well, it didn't even ask me for a password.  But it removed the x.  I repeated this stunt on /media/sda (i had two partitions there) and it did the same.  I went back to install and it worked.  Good thing I guessed right.  But what about our friends who get stuck at this point?

---

