---
title: "snap_daemon user on login screen"
date: 2022-11-09
forum: Installation &amp; Upgrades
---

### Post by jarekgol on 2022-11-09
Hi! Recently 2 new users show on my login screen: snap_daemon and snapd-range-numbers-root 
I don't want them on this screen. I try to update via gui tool, it updated Firefox and few more things, but after restart users are still on screen.
What can I do? And do I have to worry?
My version is 18

---

### Post by MAFoElffen on 2022-11-13
Create two files in directory '/var/lib/AccountsService/users/' (named 'snap_daemon', and 'snapd-rang-numbers-root') containing two lines:
```

[User]
SystemAccount=true

```

---

