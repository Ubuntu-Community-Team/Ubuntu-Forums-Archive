---
title: "32 or 64 bit Ubuntu 9.10"
date: 2010-02-25
forum: Installation &amp; Upgrades
---

### Post by Advait on 2010-02-25
Hi All,

Just installed Karmic into a partition. How can I determine if I have 32 or 64 bit Ubuntu 9.10?

Thanks!

Tom the Uber Newbie

---

### Post by Advait on 2010-02-25
Hi All, 

I found the answer. Please disregard the post.

Cheers,

Tom the Uber Newbie

---

### Post by dabl on 2010-02-25
```
sudo lsb-release -a
```

```
uname -a

```

---

### Post by chuina on 2010-02-25
```
lsb-release -a
No command 'lsb-release' found, did you mean:
 Command 'lsb_release' from package 'lsb-release' (main)
lsb-release: command not found

```
But get the result when:
```
lsb_release -a
No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 9.10
Release:	9.10
Codename:	karmic

```

Thanks **dabl**, I only knew the **uname** command.

---

