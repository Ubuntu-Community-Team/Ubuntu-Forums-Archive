---
title: "Migrate Users from previous Ubuntu version"
date: 2009-10-10
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by Onesimus on 2009-10-10
I am the administrator for 5 desktops/laptops that are currently running either Ubuntu 8.10 or 9.04.  I am intending to do a fresh install of Karmic Koala on each of the PCs.  As each PC has a number of users I am keen to migrate the user accounts (+ settings) across to the newly installed systems.

I am keen to use the ext4 file system so I am planning to format the /home partitions on each PC.

Is there any simple method to migrating the system settings across to the newly formatted /home partition ?  Currently, I am envisaging creating new user accounts on all the PCs after installation has been completed, then copying across each individual user from an external hard disk - but surely there must be a better way and perhaps even more user friendly ?!?

I am aware of the existence of Migration Assistant, but unsure of whether it is capable of doing what I would like.

---

### Post by Joe_Bishop on 2009-10-10
[http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/](http://www.cyberciti.biz/faq/howto-move-migrate-user-accounts-old-to-new-server/)

---

### Post by Onesimus on 2009-10-10
Thanks Joe_Bishop for your link.

It looks reasonably straightforward, and I will probably write a script from the commands that were given in the link.  

Though, I am surprised that something hasn't yet been done to make it easier for those unfamiliar with the command line.

---

### Post by slakkie on 2009-10-10
Those unfamiliar with the command line will probably never be responsible for such a task :)

---

### Post by Onesimus on 2009-10-11
> **slakkie said:**
> Those unfamiliar with the command line will probably never be responsible for such a task :)

But what about a person fairly new to linux/Ubuntu who wants to move from  an older version of Ubuntu to the latest version (installing rather than upgrading) and wants to ensure they keep all their settings.  How would they go about doing it ?

---

### Post by Lorag on 2009-10-11
You just copy your /home/you to a backup drive. Install latest Ubuntu and copy the backed up files to /home/new_you.

If you want to keep it really simple, you always put your /home to a separate partition or drive. That way you can choose the your old /home during install. (You should back up your files nonetheless. ;))

---

### Post by sdowney717 on 2009-10-11
[http://ubuntuforums.org/showthread.php?t=964988&highlight=chown](http://ubuntuforums.org/showthread.php?t=964988&highlight=chown)

i have done this here with good results.
using the chown command and copying the user folder.

---

### Post by slakkie on 2009-10-11
> **Onesimus said:**
> But what about a person fairly new to linux/Ubuntu who wants to move from  an older version of Ubuntu to the latest version (installing rather than upgrading) and wants to ensure they keep all their settings.  How would they go about doing it ?

They would come to the forums, pop the question and get an answer.. Like in this thread, or others, ala [http://ubuntuforums.org/showthread.php?t=1276451](http://ubuntuforums.org/showthread.php?t=1276451)

---

