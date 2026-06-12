---
title: "Move Dapper Install to New Hardware"
date: 2006-06-20
forum: Installation &amp; Upgrades
---

### Post by markpalinux on 2006-06-20
Hello,

Can you tell me how I would move a Dapper install from one machine to another, with the plan to have both up and running long term.

Can I use Ghost or will there be plug-n-play issues, etc.

Both systems are i386 - 32 bit.

Thanks,
Mark

---

### Post by sgbeamer on 2006-06-20
Depends on what your objective is but Linux is fairly easy to move.  All your files, settings, etc specific to you live in /home and all your system settings live in /etc.  Your options are:

Put both drives in one machine and direct copy

Boot up the second machine on the same network in "rescue" mode and copy the first machine over using rsync

Install from CD on both machines and just copy over your "/home" directory (and keep it synced up with unison, rsync or another backup tool if you like).

Please say a little more about what your ultimate goal is if this doesn't help you get started.

---

