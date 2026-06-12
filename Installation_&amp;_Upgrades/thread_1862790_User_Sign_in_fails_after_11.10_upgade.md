---
title: "User Sign in fails after 11.10 upgade"
date: 2011-10-17
forum: Installation &amp; Upgrades
---

### Post by mjrmua on 2011-10-17
Hi I just upgraded, 11.04 to 11.10,

On boot I get the welcome screen and can login with the guest account, but if I try with my user account I am immediately thrown back to the login screen with no error message.

I was using the gnome desktop before the upgrade, I suspect this might be part of the problem.

How do I go about debugging this?

---

### Post by mjrmua on 2011-10-17
Fixed by removing .Xauthority from user's home directory.

---

