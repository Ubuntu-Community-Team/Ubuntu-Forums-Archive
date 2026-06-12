---
title: "Samba quit working"
date: 2008-06-28
forum: Installation &amp; Upgrades
---

### Post by Tteddo on 2008-06-28
After I installed an update this morning, Samba quit working.
In SWAT it says it is running, but no other machine can connect to the shares anymore. It was working perfectly up until today.
Anyone have any ideas what happened?

Just went through the log file, and it restated Samba fine at 5AM or so, but when I restarted it after that I get this:
> [2008/06/28 13:29:01, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/06/28 13:29:01, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users
[2008/06/28 13:29:01, 0] auth/auth_util.c:create_builtin_administrators(792)
  create_builtin_administrators: Failed to create Administrators
[2008/06/28 13:29:01, 0] auth/auth_util.c:create_builtin_users(758)
  create_builtin_users: Failed to create Users

---

