---
title: "The disk drive for / is not ready yet or not present"
date: 2011-08-22
forum: Installation &amp; Upgrades
---

### Post by SMBulls9 on 2011-08-22
I got this message when my computer crashed during an important update. I think it was an HDD access timeout because it just shut off and the power button started blinking. I'm aware that this has been posted a million times but I havn't seen something with these results. I chose to do a manual recovery but an attempted 'mount -o, rw /' but it said it could not find special device 'rw'. I tried FSCK but had no luck. I might not be using the shell properly because I'm a complete noob. I cant just reinstall Ubuntu because I have important stuff saved. Also, I have a dual-boot setup with WinXP. Any suggestions?

---

### Post by whiskers751 on 2012-03-21
Wrong command! :)
Use
```
mount -o remount,rw /
```
Edit: To fix the update, which you need to do, run
```
dpkg --configure -a
And then, to reboot
halt

```
:)

---

### Post by Elfy on 2012-03-21
Old thread closed.

---

