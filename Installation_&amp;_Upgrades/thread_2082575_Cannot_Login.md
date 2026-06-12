---
title: "Cannot Login"
date: 2012-11-09
forum: Installation &amp; Upgrades
---

### Post by wagb278 on 2012-11-09
New install of 12.04.1 and the user established during install cannot login.

I was able to create an new user by entering the system as guest.  Ubuntu accepted the sudo password of the first user to establish the new user; but I cannot login as the user established during install.  The newly created user does have admin permission and I can login using that user and do sudo stuff. 

What happens when I try to login as the user established during install is some text flashes on the screen so fast I cannot read it and then I'm returned to the login screen. 

I am dual booting with Ubuntu 10.04 LTS and 12.04 LTS. Both of those share the same /home mount point and the user established in 12.04 has th esame credentials as a user on 10.04 - which works fine.

Any ideas?

Thanks, 
Jim

---

### Post by cjhabs on 2012-11-09
If the user name is the same as a user in 10.04, my guess is that some gnome files are conflicting - I suggest creating a clean home folder for the user

---

### Post by wagb278 on 2012-11-10
Thanks,  I suspect you are right. I've been doing some reading and have convinced my self that sharing /home between versions of Ubuntu was not a good idea. 

I think I will reinstall 12.04.1 and keep the /home directory in the Ubuntu install partition.  I will report back with results. 

Jim

---

### Post by grahammechanical on 2012-11-10
By the way, you should know that 10.04 is built on Gnome 2 and 12.04 is built on Gnome 3. So there would be conflicts between the different configuration files of both 10.04 and 12.04.

Regards.

---

### Post by wagb278 on 2012-11-10
Well re-installing 12.04.1 LTS and not trying to use the same /home partition used by 10.04 resolved the login problem. 

I now need to decide how I want to establish a location for user account data files; probalby a user partition with symbolic links in each user's home directory.  I have small partitons for Ubuntu versions, inadequate to hold user data files. 

Thanks, I will mark the original post solved.
Jim

---

