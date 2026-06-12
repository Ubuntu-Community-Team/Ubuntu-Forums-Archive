---
title: "password help.."
date: 2007-01-30
forum: Installation &amp; Upgrades
---

### Post by thewhiteguy1 on 2007-01-30
ok so im new.. i just installed ubuntu on an older toshiba laptop..and it all works, and then i start it up for the first time and it askes for a username and password..i remeber a password but not a username..should i just install the whole thing again...is there a work around..something?? anyone?

---

### Post by auroraborealis on 2007-01-30
You can boot to a LiveCD, mount the harddrive that your system was installed in (or do LiveCDs do it automatically these days?)

Anyway, once up and running (assuming your mount point is /mnt/mysystem), typing "cat /mnt/mysystem/etc/passwd | grep 1000" should give you the username.

---

### Post by taurus on 2007-01-30
Sounds to me like you installed using the alternate CD.  Try **oem** as your username and the password that you've created during the installing process.  Then, run this command to create an actual account for you to use from now on.

```
sudo oem-config-prepare
```

---

### Post by thewhiteguy1 on 2007-01-31
thanks alot man i appreciate it...

---

