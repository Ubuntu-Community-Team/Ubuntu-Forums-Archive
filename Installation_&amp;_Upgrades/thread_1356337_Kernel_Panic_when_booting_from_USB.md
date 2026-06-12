---
title: "Kernel Panic when booting from USB"
date: 2009-12-16
forum: Installation &amp; Upgrades
---

### Post by PoopyTheJ on 2009-12-16
Ok, so first I've purchased an Eee PC from newegg which came installed with XP. I want to install the netbook remix on it, and I've created the boot USB and whatnot. When booting from the USB drive it drops to a Busybox prompt, which I found is a known issue on some mobo's and I type exit and wait for it to continue booting. It goes through some things and gets to
 
```
run-init: overmounting root:Stale NFS file handle
[64.026893] Kernel Panic - not syncing: Attempting to kill init!
```

and the computer locks up dead. What's going on here and what do I need to do to fix this if I can. Thanks in advance for the help!

---

### Post by PoopyTheJ on 2009-12-24
Well I never found a solution for the 9.10 remix, I reverted to the 9.04 remix and it installs. I guess 9.10 just isn't going to work for me.

---

