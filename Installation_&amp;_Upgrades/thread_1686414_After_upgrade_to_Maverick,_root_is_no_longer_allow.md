---
title: "After upgrade to Maverick, root is no longer allowed to access user display"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by Holstener Liesel on 2011-02-12
Hi,

I recently upgraded from Lucid to Maverick. After the switch my backup script stopped working, which is run by udev and uses zenity via ```
export DISPLAY=:0.0
```So I looked at the output of **xhost** on clean Lucid and Maverick installs.

Lucid:
```
~$ xhost
access control enabled, only authorized clients can connect
SI:localuser:<current user>
SI:localuser:gdm
SI:localuser:root
```Maverick:
```
~$ xhost
access control enabled, only authorized clients can connect
SI:localuser:<current user>
```This new ACL setting seems to be what kept my script from working. After manually doing ```
xhost +si:localuser:root
``` I can get it to work.

So can anybody tell me what the reason for these new access controls might be and whether I'd be running a security risk by adding root to the list at every session start? Maybe there's another, better way to allow root to open the current user's display?

Thanks!

---

