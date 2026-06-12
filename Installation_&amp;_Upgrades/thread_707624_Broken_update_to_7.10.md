---
title: "Broken update to 7.10"
date: 2008-02-25
forum: Installation &amp; Upgrades
---

### Post by noontz on 2008-02-25
Hi I am completely new to Ubuntu, so I think this might be an easy one.

During update the system broke down.

Booting up again things seems OK but the X server will not start..

Since I have access to the command line is there an easy way to redo the update with a command?

Thanks in advice :)

---

### Post by Sam Lars on 2008-02-25
What does
```
cat /var/log/Xorg.0.log | grep EE
```
return?

---

### Post by noontz on 2008-02-28
Thx alot for your reply..

In the meanwhile I did a attempt with a complete reupdate following the help info & the system crashed again leading me to suspect some kind of bios error. Since I get the kernel panic error on rebooting now I´ll try installing on a different  harddisk and fetch my data this way....

---

### Post by Sam Lars on 2008-02-29
Okay.  You never want to have to, but sometimes you just have to start over.  Let us know how it goes.

---

