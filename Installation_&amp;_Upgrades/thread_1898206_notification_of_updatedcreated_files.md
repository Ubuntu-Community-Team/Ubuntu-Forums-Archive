---
title: "notification of updated/created files"
date: 2011-12-20
forum: Installation &amp; Upgrades
---

### Post by mooreaa on 2011-12-20
Hi guys,

I'm trying to figure out a way to run a script when files are modified/updated in my /var/www/ directory.

I am running a server at RackSpace with Ubuntu 11.10 with inotify using incrontab, but I can't figure out a way to recursively search the folder tree.

My goals is to be notified when any chance are made within that directory or its subdirectories so that I can check the file permissions and update them as necessary. 

But, it seems like icrontab only works on a structured folder approach rather then recursively going though folders. This is a problem when new directories are created since i will not get a notification.

Any ideas?

---

