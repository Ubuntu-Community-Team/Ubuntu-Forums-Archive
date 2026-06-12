---
title: "help me restore backup on a new system"
date: 2014-06-07
forum: Installation &amp; Upgrades
---

### Post by rompstar2 on 2014-06-07
ok, so I want to change servers, I have a much nicer machine now and it is super quiet compared to the one I have now...

So on the existing system I backed-up using tar to a back.file... this system is setup using LVM for the disk managment.

On my new system I just did a plain install, no LVM, so of course after I restore the backup.file at boot I get a:

error: no such devide: lettersxnumbers
error: disk 'lvmid ****' not found
loading initial ramdisk

So I guess I need to change this label so that it is not looking for the old disk ID, how do I do this ?

:-)

---

### Post by rompstar2 on 2014-06-07
never mind, I solved this using a Google search, thanks!

---

### Post by gdesilva on 2014-06-08
It would help many others if you were able to post the solution - thanks

---

