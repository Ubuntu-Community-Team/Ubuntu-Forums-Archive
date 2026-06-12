---
title: "Unable to get exclusive lock"
date: 2008-11-16
forum: Installation &amp; Upgrades
---

### Post by DazzledBear on 2008-11-16
I have a problem with this lock thing. I am using ubuntu 8.4 with KDE. When I want to upgrade to 8.10 using Adept Manager it says following:

Unable to get exclusive lock
This usually means that another package management application (like apt-get or aptitude) already running. Please close that application first.

There's no apt-get or aptitude running. 
When trying to do it with aptitude or apt-get it says it could not get lock. I found the 'lock' but I don't know what to do with it. It's only an empty document.

---

### Post by cariboo on 2008-11-16
The lock file is supposed to be deleted when the application using it is closed, it is OK to delete the lock file.

Jim

---

### Post by DazzledBear on 2008-11-16
I tryed to delete it but I couldn't. Not even as root. Is it possible that some aplication running as deamon is using it? How do I find what application then??

Barbora

---

### Post by DazzledBear on 2008-11-17
I solved my problem :) It was Adept Manager itself creating the lock and then it wanted it again. Well I tried to rm the lock as a root after launching the application and it worked out.
Jim, thank you for the advice about the lock.
Barbora

---

