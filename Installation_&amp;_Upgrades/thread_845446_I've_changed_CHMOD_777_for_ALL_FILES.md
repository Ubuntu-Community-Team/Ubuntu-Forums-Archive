---
title: "I've changed CHMOD 777 for ALL FILES"
date: 2008-06-30
forum: Installation &amp; Upgrades
---

### Post by Pronigo on 2008-06-30
Hello,
yes, it's true :( I've just changed chmod to 777 for all files on my disk by simple command: sudo chmod 777 -R /

Now, server is down, everything is working bad. Please, it's very important for me, I'll have tommorow big troubles if I won't fix it quickly :(

---

### Post by markjensen on 2008-06-30
Since there is no "undo", I would give the same advice for someone who executed a **rm -rf**, and suggest you restore from backup.

---

### Post by Pronigo on 2008-06-30
But I don't have backup - I think so :( Can I reinstall system without delete home folders?

---

### Post by ilrudie on 2008-07-01
> **Pronigo said:**
> But I don't have backup - I think so :( Can I reinstall system without delete home folders?

In the future make the /home a separate partition and then saving home directories when reinstalling become easy (just don't reformat the partition).  It will take some work to fix the permissions on the home directories though even if you save them.  I think Ubuntu can "import" users it finds but its probably a better idea to get an external USB drive and backup the home directory.  Then wipe everything and install with a separate /home.

---

### Post by PmDematagoda on 2008-07-01
> **Pronigo said:**
> But I don't have backup - I think so :( Can I reinstall system without delete home folders?

Building on what ilrudie said, you most definitely should be able to use a Live CD to copy the stuff you need somewhere else before doing a reinstall. In this kind of a problem, the fastest and cleanest fix is to reinstall, trying to fix the troubles will mean a lot of time and would not be very likely to succeed.

---

### Post by ilrudie on 2008-07-01
> **PmDematagoda said:**
> Building on what ilrudie said, you most definitely should be able to use a Live CD to copy the stuff you need somewhere else before doing a reinstall. In this kind of a problem, the fastest and cleanest fix is to reinstall, trying to fix the troubles will mean a lot of time and would not be very likely to succeed.

Thanks for the additional info.  I havn't ever used the Ubuntu LiveCD for this but in Solaris it doesn't mount the partitions for you so you need to mount them yourself.  Its just a guess but I'd imagine he will need to do that before he can get his /home directory backed up.  

To the OP:
If you need help mounting the harddisk or fixing the /home permissions post your questions back here and I will try to check back a few times today and answer your questions.  You may also want to back up /etc/passwd and /etc/group which will be of much assistance when trying to fix home permissions and recreate user accounts.

---

