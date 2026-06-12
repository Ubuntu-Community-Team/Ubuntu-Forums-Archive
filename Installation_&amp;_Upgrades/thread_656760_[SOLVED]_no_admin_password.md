---
title: "[SOLVED] no admin password ??"
date: 2008-01-02
forum: Installation &amp; Upgrades
---

### Post by randyp on 2008-01-02
I've been using Debian for about a year and just installed Kubuntu for the first time. During the install I wasn't asked to give an admin password and now I can't get root access in a terminal. Have I miss something? How do I create the admin account?
Thanks
Randy

---

### Post by scxtt on 2008-01-02
sudo $USER <command> or **sudo -s**

there isn't a "login-able" root account by default ... but the user created during install has system-wide sudo access ...

---

### Post by jken146 on 2008-01-02
Yup, Ubuntu uses sudo.  [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by randyp on 2008-01-02
I can deal with that! Thanks!

---

