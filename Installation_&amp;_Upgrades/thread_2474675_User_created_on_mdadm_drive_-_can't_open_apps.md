---
title: "User created on mdadm drive - can't open apps"
date: 2022-05-05
forum: Installation &amp; Upgrades
---

### Post by ya-simply-better on 2022-05-05
Hey, 

I created a user with home directory that is on a different drive that is a in raid array using mdadm. When I go in under the new user it has the same GUI interface with apps but none of the apps work. 

Is there some configuration needed for new accounts that are in a different home directory?

---

### Post by TheFu on 2022-05-05
snaps only work when the HOME directory is under /home/{username}.  It is a flaw in snap confinement.

So 
/home/ya 
 will work but 
/other/home/ya 
 and 
/nfs/home/ya, /export/ya, /u/ya, /u/home/ya
will not work.

As for issues with mdadm, that could be a bug, assuming you remember to laydown a file system and set the owner and permissions correctly.

---

