---
title: "I think I hosed myself with usermod"
date: 2007-03-01
forum: Installation &amp; Upgrades
---

### Post by asheville on 2007-03-01
while trying to add myself to a group I typed 
sudo usermod -G groupname me
not realizing that I was removing all the other groups that I belong to.  Now I realize I should have used the -a option but it's too late.  I can't even use the sudo command to add myself back to the groups or do anything priviledged for that matter.  I never did set the root password so I can't login with it.
Is there any way out of this mess I've created for myself?

Thanks

---

### Post by taurus on 2007-03-01
Boot into recovery mode from GRUB menu and add yourself, your username, to groups adm and admin in /etc/group.

```
nano -B /etc/group
```
Save it with <Ctrl>x, Y for the question and Return.  Reboot and see if you can run sudo again.

```
shutdown -r now
```

---

### Post by asheville on 2007-03-01
That worked.  Thank you so much.  I was afraid I wasn't going to be able to dig myself out of that.

---

