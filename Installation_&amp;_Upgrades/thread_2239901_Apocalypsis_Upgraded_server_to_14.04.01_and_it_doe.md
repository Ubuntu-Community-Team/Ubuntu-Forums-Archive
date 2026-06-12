---
title: "Apocalypsis: Upgraded server to 14.04.01 and it does not start"
date: 2014-08-16
forum: Installation &amp; Upgrades
---

### Post by mgriffa on 2014-08-16
Ping and ssh do not respond, it's a remote server so I don't get to see the boot screen.
Any idea on how to proceed?

---

### Post by JetStorm on 2014-08-16
It depends on the company providing your server but you'll definitely need to contact their support.
There might be an option for a free or paid remote console which will show you the boot screen or their support might take a look and give you more info but either way you'll have to talk to them.

---

### Post by mgriffa on 2014-08-16
They finally rescued it with rescue mode in CD, I wasn't aware of it.
I believe I've hit bug in the installation: apparently grub got confused because I removed old kernels to free space.
Initial install failed for missing space:I removed old kernels and run installer. everything went fine but grub never started.

---

