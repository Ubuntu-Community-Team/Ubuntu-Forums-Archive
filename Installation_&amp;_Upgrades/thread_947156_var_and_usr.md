---
title: "/var and /usr"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by sulekha on 2008-10-14
Hi all,

Why is it said that /var should reside on a separate partition from /usr ?

---

### Post by iaculallad on 2008-10-14
> **sulekha said:**
> Hi all,

Why is it said that /var should reside on a separate partition from /usr ?

Because the /var sub-directory contain all variable files and temporary files created by the logged user. This files inlcudes temporary storage files downloaded from the Internet, log files, print spooling. While /usr sub-directory contains all user related libraries, applications. Such sub-directories cannot be interchanged.

---

