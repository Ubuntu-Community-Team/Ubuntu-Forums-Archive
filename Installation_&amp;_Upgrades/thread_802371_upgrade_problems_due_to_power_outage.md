---
title: "upgrade problems due to power outage"
date: 2008-05-21
forum: Installation &amp; Upgrades
---

### Post by bpgraju on 2008-05-21
He all,
The problem: I have been upgrading from gutsy to hardy. things went on fine and while updating all the packages (almost 1029 in number and 6 hours to download) had been downloaded. When the installation was 10% through, we had a power outage. there afterwards after the system rebooted, after the login process i get a blank screen only the desktop wall paper is seen. No menus, no toolbars no nothing! What to to. I am not on a dual boot option. I am on a dedicated system running ubuntu. Please help. 
Thanks in advance

---

### Post by forestpixie on 2008-05-21
Try to boot recovery mode and run

```
dpkg --configure -a
```

---

