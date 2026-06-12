---
title: "SU Password in 5.10"
date: 2005-12-03
forum: Installation &amp; Upgrades
---

### Post by kbarz on 2005-12-03
Just upgraded to 5.10.  I notice that the password I used in initially setting up the system works for the GUI to set up new users.  However, if I use SU through the terminal the same password doesn't work.  I wasn't prompted to set up any admin password just like in the previous Ubuntu, so I'm just wondering why SU isn't working.

---

### Post by 23meg on 2005-12-03
Because the root account is disabled by default. 

[http://wiki.ubuntu.com/RootSudo](http://wiki.ubuntu.com/RootSudo)

---

### Post by atoponce on 2005-12-03
The root account is disabled by default.  If you would like system administration privileges to the system, you need to invoke 'sudo' followed by the privileged command.  You will then be prompted for your password, not root's.  If you must have root enabled on your system, merely type:

```
sudo passwd root
```

This will activate the root account, and you will be prompted to setup a new password that, of course, you will be asked to confirm.

---

