---
title: "Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)"
date: 2019-04-19
forum: Installation &amp; Upgrades
---

### Post by cesera on 2019-04-19
I upgraded my son's computer from lubuntu 16.04 (32 bit) to lubuntu 18.04 (64 bit) (formatted /, preserved /home). The initial install went fine, and I could boot into the new system. I then ran an update overnight: ```
sudo apt-get dist-upgrade
``` This seemed to have gone fine, but when I rebooted the machine this morning I got a kernel panic:

> Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(0,0)

I then rebooted into the live CD, installed boot-repair and ran the recommended repair (the paste bin is here: [http://paste.ubuntu.com/p/xkTbjmKFFx/](http://paste.ubuntu.com/p/xkTbjmKFFx/)), this did however not solve the problem.

Any ideas what I can do about this?

Thank you for your help,
Kees

---

