---
title: "what do i backup to move to 9.10"
date: 2009-12-01
forum: Installation &amp; Upgrades
---

### Post by jessiebrownjr on 2009-12-01
I have my NFS server/client setup with my laptop and desktop, both are running 9.04. Is the hosts.allow/deny fstab and etcetera all the same to set up again, or will I run into problems? I'm not looking to upgrade both to 9.10 at the same time. I'd like to backup as many settings as I can onto an extra partition.

This will be a fresh install, not an upgrade. 

For instance, is there a way to backup all my shortcuts I have on my firefox? Hehe, that one isn't that big of a deal but mainly I'd like to keep my NFS working. Thanks guys!

---

### Post by whoop on 2009-12-01
Copy the entire /home dir containing all users with all settings... should be enough (usually) for a desktop...

For the server it really depends on what you installed and how you configured it...

---

### Post by jessiebrownjr on 2009-12-01
I just went through the home directory and it looks like it would work for sure as long as the newer versions of various things supported it, however the only thing I think im really worried about now that I think about it is NFS, which shouldn't be to hard to set up I guess :-)

As long as they didn't change greatly of course!

---

### Post by whoop on 2009-12-01
> **jessiebrownjr said:**
> I just went through the home directory and it looks like it would work for sure as long as the newer versions of various things supported it, however the only thing I think im really worried about now that I think about it is NFS, which shouldn't be to hard to set up I guess :-)

As long as they didn't change greatly of course!

Now that you backed up, why not just upgrade (without doing a fresh install)? I've been doing it for years and years :D

---

### Post by jessiebrownjr on 2009-12-01
I like to clean the pipes every few months and do fresh installs. Ubuntu 9.04 was my first linux install in MANY years and I have no idea what I have possibly boogered up. I tried to upgrade to 9.10 and it bugged out(i think I know why now though) but still-- I want to start a new install, immedietly set up firewall among other things, and not be "naked" to attacks like I was for a few months. I'm also toying with the idea of going to KDE, but I'm not sure yet.

---

