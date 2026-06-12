---
title: "Help Urgent..&quot;INvalid username and pass&quot;"
date: 2007-07-30
forum: Installation &amp; Upgrades
---

### Post by hadimhd on 2007-07-30
i tried to install ubuntu 7.04 on my 32 intel PC.. i tried twice..but same error "invalid user name and pass"

tried root : root and user : pass

Thanks

---

### Post by roachk71 on 2007-07-30
Try booting into single-user mode by pressing the Escape key to get the GRUB boot benu at startup, and selecting one of the recovery boots.

Then, you should be able to use
```
passwd *username*
```to change or assign a password.

By default, the root password is undefined, since *sudo* is used under your normal user account.

If, however, you have assigned a root password already, you might have to bypass it under your user account with
```
sudo passwd *username*
```

---

