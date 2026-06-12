---
title: "[SOLVED] Firefox Works As Root But Not User"
date: 2008-04-02
forum: Installation &amp; Upgrades
---

### Post by jmg498 on 2008-04-02
I recently tried to do a complete removal of Firefox and reinstall due to some problems I was having with it.  Now, when I run Firefox from the shell as root, it comes up and works fine.  But if I run it as the regular user, it errors out with a segmentation fault.  Any suggestions?  Thanks!

josh@ubuntu:~$ firefox
write cache: No such file or directory
Segmentation fault

---

### Post by ridgeland on 2008-04-02
I would create a new user (or use a different one)
Log in as the new user and open and verify Firefox works.
then in the terminal
$ sudo nautilus
In Nautilus as root turn on see hidden files
copy the directory from the new user to your old user
/home/newguy/.mozilla/firefox
copy to
/home/olduser/.mozilla/firefox 
replace existing directory that doesn't work
Close nautilus
Still  in terminal
$ sudo  chown -R olduser  /home/olduser/.mozilla
then logout as new user and log back in as old user
Worth a try.

---

### Post by jmg498 on 2008-04-03
Thanks!   That helped me diagnose the problem.  I think it may be a disk space issue.  I am running Ubuntu via Wubi and only allocated a small portion of the drive to Linux.  When I created the new user like you suggested I tried to login on that name, and X crashed and came up with an error saying I may be out of disk space.  

I cleared some files then logged back in as the original user and firefox worked fine.  What I don't understand is why it worked as root even if the disk was full but not as user.  Regardless, it seems to be fixed now.  I guess I should see about moving my loopback partition to a regular partition using LUBI or something to avoid this again in the future.

---

### Post by ridgeland on 2008-04-03
When you set up a partition part of the space is reserved for the system administrator (like 3-5%).  So root was not out of space yet, just the users.  When you create a fresh partition you'll see that only 95-98% of the space shows as available some shows as used even before you put anything in it.

If this is solved you should mark it so.  Go to the #1 post at the top and find the menu [Thread Tools v] and hit [Mark as Solved].  Also if you want to thank someone click on the little gold star on their post.

Have fun in Ubuntu!

---

