---
title: "Not Enough Disk Space Resulting In Corrupted dpkg"
date: 2008-10-06
forum: Installation &amp; Upgrades
---

### Post by rykel on 2008-10-06
Hi,

I was trying to install Ubuntu Desktop (sudo apt-get install ubuntu-desktop) but ran out of hard disk space and it resulted in some error messages.

Now I am having this error:

[INDENT][B]$ sudo apt-get autoremove
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

$ sudo dpkg --configure -a
dpkg: parse error, in file `/var/lib/dpkg/updates/0241' near line 1:
 newline in field name `#padding'[/B][/INDENT]

Can you please help?

---

### Post by rykel on 2008-10-07
Anyone?   :confused:

---

### Post by iaculallad on 2008-10-07
On your terminal:

```
sudo rm /var/lib/dpkg/updates/0241
sudo apt-get update
sudo apt-get upgrade
```

---

