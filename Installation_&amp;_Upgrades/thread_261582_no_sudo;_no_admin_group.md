---
title: "no sudo; no admin group"
date: 2006-09-20
forum: Installation &amp; Upgrades
---

### Post by cotcot on 2006-09-20
I reinstalled dapper using an existing /home. 
I can not sudo as user. Trying to adjust this according to the ubuntu guide learned me that there is no admin group.
How to solve this ?

---

### Post by jpkotta on 2006-09-20
If there is not admin group at all, try reinstalling.  Add a user like you normally would.  It should not overwrite your $HOME.  If there is an admin group and you're just not in it, do
```
gpasswd -a cotcot admin
```
as root (you can boot into recovery mode and be root).

You may have trouble with permissions in $HOME if the UID and GID are different than before (these are numbers that are actually stored in the filesystem; your files are not owned by "cotcot", they are owned by UID 1000 or something like that).  So after you reinstall, you may have to do this:
```
sudo chown -R cotcot:cotcot ~cotcot
```

---

### Post by cotcot on 2006-09-20
Problem is solved.

I made a new group (groupadd admin)


added my user to the group (usermod -G admin user)

Then edited /etc/sudoers (as root : visudo and then added %admin  ALL=(ALL) ALL )

Sudo works now.

---

### Post by cotcot on 2006-09-20
Thanks for your reply jpkotta.
I tried to repair the problem without reinstall.
It was after a reinstall with overwriting an existing /home of the same user that i lost the admin group.
UID  1000 and user name were the same.

---

