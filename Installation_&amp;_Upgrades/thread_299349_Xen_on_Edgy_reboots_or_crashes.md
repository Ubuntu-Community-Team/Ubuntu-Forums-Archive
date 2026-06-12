---
title: "Xen on Edgy reboots or crashes"
date: 2006-11-14
forum: Installation &amp; Upgrades
---

### Post by xurizaemon on 2006-11-14
I followed this HOWTO on my just-upgraded-from-Dapper Ubuntu:

[https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy](https://help.ubuntu.com/community/XenVirtualMachine/XenOnUbuntuEdgy)

The resulting system worked but crashed (rebooted) unexpectedly, especially when I launched FireFox (running X11 on the dom0 machine - is this not advised?). I didn't really try many other apps at that point to be honest (except terminal nonsense while moving HD contents around prepping for a Xen install).

Later I found another howto which advised installing a few more packages, including xen-tools and libc6-xen. Installing these seems to have resolved this for me.

I believe this command has resolved my issue (perhaps it was just libc6-xen?):
```

sudo apt-get install libc6-xen lvm-common lvm2 xen-tools

```

---

