---
title: "Using loop-aes in edgy?"
date: 2006-10-27
forum: Installation &amp; Upgrades
---

### Post by moxie0 on 2006-10-27
I just upgraded to edgy and am having problems with my loop-aes partitions.  First, I notice that the fstab format changed with edgy.  My non-loop-aes partitions were marked as "converted" by edgy and have the UUID stuff.  My loop-aes partitions, however, were not converted.

Second, it seems like edgy is using a different init system?  With the old init system, the boot process would move through the init files until it got to the place where non-root partitions were to be mounted.  There, the mount command would prompt for my keystore password, I'd enter it, and things would continue on.

Now, my password is never prompted for. I don't see any attempt to mount those partitions, and daemons that require access to my encrypted /var partition start failing because it doesn't exist yet.  Of course, this prevents GDM from starting.

So is the problem that my fstab wasn't fully converted and init's new mount scripts aren't seeing these partitions?  Or something else?  Has anyone successfully gotten loop-aes running smoothly with edgy?

---

### Post by moxie0 on 2006-10-27
I'm going to answer my own question.  Here's what I did to make things work:

Edit /etc/init.d/mountall.sh and replace every instance of 'mount ...' with: 

/usr/bin/openvt -f -c `fgconsole` -w <mount> <existing args>

---

