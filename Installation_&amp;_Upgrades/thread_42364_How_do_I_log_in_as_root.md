---
title: "How do I log in as root"
date: 2005-06-17
forum: Installation &amp; Upgrades
---

### Post by terryw on 2005-06-17
I've installed 5.04 on my laptop and all is well.  During the install process I was not asked to set a password for root, only to create a user name for non-root logins.  How then can I log in as root when I need to make system changes.

Regards

Terry

---

### Post by tonym on 2005-06-17
You don't have to.  The Ubuntu way is to use sudo.  eg

sudo vi /etc/fstab

If you really want a root logon use sudu passwd to create a password for root that can then be used to logon.

---

### Post by Juergen on 2005-06-17
Look here:
[http://www.ubuntulinux.org/support/documentation/faq/root](http://www.ubuntulinux.org/support/documentation/faq/root) 
and:
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)

---

### Post by XDevHald on 2005-06-17
[QUOTE=terryw]I've installed 5.04 on my laptop and all is well.  During the install process I was not asked to set a password for root, only to create a user name for non-root logins.  How then can I log in as root when I need to make system changes.

Regards

Terry[/QUOTE]
 To learn more about the root password setting, visit   [http://www.ubuntulinux.org/wiki/RootSudo](http://www.ubuntulinux.org/wiki/RootSudo)

To learn more about Ubuntu in general, visit
[http://www.ubuntulinux.org/wiki](http://www.ubuntulinux.org/wiki)

---

### Post by terryw on 2005-06-18
Thanks to all, very helpful

Terry

---

