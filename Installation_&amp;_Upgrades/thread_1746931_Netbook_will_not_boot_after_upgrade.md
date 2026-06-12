---
title: "Netbook will not boot after upgrade"
date: 2011-05-02
forum: Installation &amp; Upgrades
---

### Post by jyossarian1 on 2011-05-02
I tried to upgrade to Natty last night and after attempting a restart, the netbook will not boot.

I've tried Linux 2.6.38-8-generic and get "Kernel panic - not syncing: VFS: unable to mount root fs on unknown -  block (0,0)....(there is more if it is important I will post).

I've tried 2.6.38-8-generic (recovery mode) and get more detail but the message ends the same and includes the "unable to mount fs" error.

I've tried 2.6.35-28-generic and get "the disk drive for / is not ready yet or not present."

I can continue and select M for manual recovery and get to root:~# but don't know where to go next.

Please help.  I need my Ubuntu back.

---

### Post by jyossarian1 on 2011-05-02
I went to root and tried:  [B]sudo apt-get update
[/B]The reply I got was "dpkg was interrupted, you must manually run 'sudo dpkg --configure -a to correct the problem.

which I tried and it returns, "dpkg: error: unable to access dpkg status area: Read-only file system"


???

---

