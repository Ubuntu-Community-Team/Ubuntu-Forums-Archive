---
title: "install gave me root power"
date: 2008-07-20
forum: Installation &amp; Upgrades
---

### Post by yonnie on 2008-07-20
I just installed kubuntu 8.04.  During install it asked for user name and account password.  After install while installing other software I noticed that the owner is root, my password is also same as root but in user manager I'm listed as a user and root is another user. 

I've not encountered something like this before, any suggestions as to how to correct this without hosing the install?

---

### Post by n00bWillingToLearn on 2008-07-20
This is not a bug, you are not running with root privileges but rather running as a user with the privileges to run commands as root with sudo, it is a subtle but very important distinction, see:

 [https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

For a complete explanation.

---

### Post by yonnie on 2008-07-20
What a relief!  thanks!

---

