---
title: "Update Issues."
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by J216 on 2008-10-18
I'm having problems with the update manager. When it tries to download and install the updates, it tels me 

"E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 
E: _cache->open() failed, please report."

When I run "dpkg --configure -a" in the terminal it tells me 

"dpkg: requested operation requires superuser privilege"


How do I get the update or the privilege to manually update?

Thanks in advance for the help.

---

### Post by howefield on 2008-10-18
preface your command with sudo, eg

```
sudo dpkg --configure -a
```

It will ask for your password, and give you the rights to run the command.

---

### Post by J216 on 2008-10-18
Thanks Again. I knew it was probably just something simple that I was or wasn't doing. But, I'm new to ubuntu. So, I get frustrated pretty easily.

---

### Post by ucaru on 2008-10-24
> **howefield said:**
> preface your command with sudo, eg

```
sudo dpkg --configure -a
```

It will ask for your password, and give you the rights to run the command.

This helped me as well. Thanks.

---

