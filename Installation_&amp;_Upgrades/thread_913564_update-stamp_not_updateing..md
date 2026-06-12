---
title: "update-stamp not updateing."
date: 2008-09-07
forum: Installation &amp; Upgrades
---

### Post by solitaire on 2008-09-07
Annoying issue that i've had for a while.
running "apt-get update" or "Software Sources" or "Update manager" manually does not update or touch the following files:
```

/var/lib/apt/periodic/update-stamp
/var/lib/apt/periodic/update-success-stamp

```So every 7 or 8 days i get a warning that I've not updated (I manually run the update daily)
I have to run: 
```

sudo touch /var/lib/apt/periodic/update-stamp
sudo touch /var/lib/apt/periodic/update-success-stamp

```every time to reset the counter.
in case it's a permission issue here is an output of: ls -all
```

sol@Callisto:/var/lib/apt/periodic$ ls -all
total 8
drwxr-xr-x 2 root root 4096 2008-07-29 00:43 .
drwxr-xr-x 6 root root 4096 2008-09-07 21:10 ..
-rw-r--r-- 1 root root    0 2008-09-04 05:01 update-stamp
-rw-r--r-- 1 root root    0 2008-09-04 05:01 update-success-stamp

```Has anyone else has this issue?
or know how to sort it?

---

### Post by solitaire on 2008-09-09
*Bump*

Any suggestions??

---

