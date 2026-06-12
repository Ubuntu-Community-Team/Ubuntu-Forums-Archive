---
title: "password"
date: 2007-05-20
forum: Installation &amp; Upgrades
---

### Post by bounderkirk77 on 2007-05-20
Most fundamental goof:  installed 6.06 flawlessly on my desktop three weeks ago before leaving for Singapore; returned (to Seattle) today; forgot the password.

How to:

[a]   Uninstall/re-install 6.06, or

[b]   Gain access as another user, then change my original (root) password?

Many thanks.

---

### Post by taurus on 2007-05-20
Boot into recovery mode from GRUB menu and change your password to something you can remember.  _Assuming_ your login name is **john**, do

```
passwd **john**
shutdown -r now
```

---

