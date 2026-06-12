---
title: "Backup Question before Server Dist Upgrade"
date: 2017-12-28
forum: Installation &amp; Upgrades
---

### Post by Altin on 2017-12-28
I am upgrading my server from Ubuntu 14.04 to 16.04 and am in the process of backing everything up beforehand. I am going with a fresh install of 16.04 as I want to enable software RAID1. I will be backing up .tgz files of my home directories, web directories, samba directories, modified config files, virtual machines, SQL databases, etc, etc, and moving them onto external storage. Nothing is being encrypted, just rolled up into tgz files.

I want to preserve the metadata of the files (permissions, timestamps, etc) and so my plan was to format the external storage as ext4, similar to the fs the server uses. The only concern I had was whether there would be a permissions issue once I restored the files to the new server once it is on 16.04. If I back up /home/caldera to a tgz, then create a user caldera on the new server, and go to restore the tgz to the new /home/caldera, will the OS 'see' that the files are not from the same user 'caldera'? Is there some unique user ID which would be different even if the usernames are the same, and if so will this cause any problems during restore or use of the files?

I will have sudo privileges on the new machine, so what if anything will I need to do to the restored files to ensure they 'belong' to the new users. It is users like www-data, samba and root that I am thinking of also.

---

### Post by TheFu on 2017-12-29
I wouldn't use tar for a backup method.  It was designed for 250MB of data, not 5GB or more. Using a modern backup tool would be more efficient, both in storage and network transfer and it would include versioning.  A versioned backup solved 1001 problems.  A single point-in-time backup solves about 10, though those 10 ARE extremely important.

I sorta wonder why they still teach tar, since the only people who use it seem to have taken 1 Linux admin class and stopped.

Ok ... onto the username vs uid mapping. Different backup tools will handle this differently.  Even different versions of tar will handle them differently, so you'll need to see if you are using tar, gnutar, star, or one of the 10 other variants and check the specific options around those mappings.  I believe that most will do the username mapping, but definitely check that on your systems (they could be different).

BTW, many backup tools don't capture ACLs by default, so if you are using any, then you'll want to ensure ACLs are included in the backups.

I wouldn't have a web server running on the same machine where samba runs. Security risks.  Have you considered using a read-only NFS mount for the web server?

During the restore, you'll absolutely need to use sudo. Without it, all the restored files would be owned by the userid performing the restore.

I would plan for a few failed attempts.  Be prepared to test any restores a few times.  Whenever I migrate a server, I plan 2-7 days of effort.  Of course, I hope for the best - single restore and all is perfect - but that seldom happens. ;)  Be prepared to wipe the new OS and start over, a few times.

---

