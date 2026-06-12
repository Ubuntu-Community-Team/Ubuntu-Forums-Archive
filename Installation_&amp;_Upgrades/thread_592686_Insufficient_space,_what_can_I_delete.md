---
title: "Insufficient space, what can I delete"
date: 2007-10-26
forum: Installation &amp; Upgrades
---

### Post by sumithar on 2007-10-26
While upgrading to 7.10 from 7.04 using the recommended approach, I ran into an issue where I got a popup window that said I had insufficient space on '/'.  It recommended that I empty the recycle bin and run some command to delete installed packages or something like that.  I did both but still don't have sufficient space.

I had originally partitioned my hard disk to provide 3GB for XP, 4GB for Linux and 13GB for a shared drive.  

I'd like to think that 4GB should be sufficient for Linux, right?  I keep all the user data like pictures and songs and so on on the shared drive anyway.

I would like to know how one goes about cleaning stuff up and deleting stuff on Linux.

Like on windows, one deletes temp folders and so on.  What is the equivalent in Linux?


Thanks

---

### Post by dabl on 2007-10-26
> **sumithar said:**
>   

I'd like to think that 4GB should be sufficient for Linux, right?



No.  I've seen my filesystem (not including /home) creep up over 4.5GB.  I use a 6GB partition for it.


:sad:

---

### Post by sumithar on 2007-10-29
> **dabl said:**
> No.  I've seen my filesystem (not including /home) creep up over 4.5GB.  I use a 6GB partition for it.


:sad:

Darn!  Will it help to delete the old versions of the kernel?  I see like half dozen entries in Grub when I boot up, and I always choose the first one.

---

### Post by lyndaj70 on 2007-10-29
Don't know if this will help sufficiently, but you can run Synaptic, view installed packages, and uninstall some to free some disk space.  

Hope it helps,
Lynda

---

### Post by lyndaj70 on 2007-10-29
I just checked my file system.... if you remove the home/ directory I'm still using 4.5 GB, but I have scads of games installed for the kid.....  As a temporary fix uninstalling some apps should get you down until you come up with a permanent solution....

Good luck!:)

---

### Post by Chris Sharman on 2007-10-29
I have the same problem.
Experimenting with the apt-get config file - I'm hoping I can have it use my vast home partition for workspace by adding

Dir::Cache::Archives "/home/Apt-Workspace";

to /etc/apt/apt.conf

(also created the folder, and partial under it)

Looking good so far ...

Chris

---

