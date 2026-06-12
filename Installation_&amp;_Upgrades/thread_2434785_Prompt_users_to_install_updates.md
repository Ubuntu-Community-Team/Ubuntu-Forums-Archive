---
title: "Prompt users to install updates"
date: 2020-01-10
forum: Installation &amp; Upgrades
---

### Post by timomak on 2020-01-10
I have set as admin (xubuntu 18.04,) to display updates when available, then i can check and install them.
But i also have another account as user and there is one more user(total 3 with the admin).
Now, i need to have updates displayed the same way as in admin account and so each user can install them when appeared. Does this happens automatically or i have to change any setting for than ?

---

### Post by deadflowr on 2020-01-10
Only admins can install updates.

---

### Post by timomak on 2020-01-12
Thanks for your answer.
What about set for users to get update messages from the software updater ?:confused:

---

### Post by CatKiller on 2020-01-12
> **timomak said:**
> Now, i need to have updates displayed the same way as in admin account and so each user can install them when appeared. Does this happens automatically or i have to change any setting for than ?

I don't have a machine with non-admin users to check, but my understanding is that all users will be able to see that there are updates even though only admin users can install the updates; so that those non-admin users can let the admin know, and so that the admin user can authenticate to elevate privileges without having to log that non-admin out.

These settings are [configurable](http://www.admin-magazine.com/Articles/Assigning-Privileges-with-sudo-and-PolicyKit), but the defaults are good for most purposes. Modifying those settings can go very wrong very quickly: it's possible to inadvertently make it so that *no one* can elevate their privileges, or so that malware can, so extreme care must be taken.

---

### Post by timomak on 2020-01-14
Thank you for your answer.
I prefer work as user and only when i need to do or change something i enter as admin. So i will do as you described and will not change update settings.:)

---

