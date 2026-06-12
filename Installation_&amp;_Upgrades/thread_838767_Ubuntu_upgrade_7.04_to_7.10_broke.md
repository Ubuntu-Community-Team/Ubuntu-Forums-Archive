---
title: "Ubuntu upgrade 7.04 to 7.10 broke"
date: 2008-06-23
forum: Installation &amp; Upgrades
---

### Post by Mikebgr on 2008-06-23
As title suggests, my upgrade from 7.04 to 7.10 broke, after downloading packages and installing more than half of them. 
After that it just told me many applications had to close (even ones i did not have running - strange) and installation had to exit. 

Also it suggested i would do a dpkg --configure -a, but it doesnt show any problems. And no other problems came up.

So question is:

I try to upgrade again from 7.04 to 7.10 (fully this time)
or
I go for 7.10 -8.04 upgrade?

Any suggestions welcome!

---

### Post by Partyboi2 on 2008-06-23
What is the output to this command
```
lsb_release -d
```

---

### Post by Mikebgr on 2008-06-24
```
mike@ubuntu:~$ lsb_release -d
Description:    Ubuntu 7.10

```

---

### Post by Partyboi2 on 2008-06-24
Have a look through/var/log/dist-upgrade/main.log for any problems, if there isn't any problems I would go ahead and try upgrading to 8.04.

---

### Post by Mikebgr on 2008-06-24
Thanks for the attention, no problems in the log (really strange though). Anyway I upgraded to 8.04 and no problems so far!

---

