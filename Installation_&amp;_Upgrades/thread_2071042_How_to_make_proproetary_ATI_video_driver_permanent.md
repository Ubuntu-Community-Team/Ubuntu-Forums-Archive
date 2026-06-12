---
title: "How to make proproetary ATI video driver permanent"
date: 2012-10-14
forum: Installation &amp; Upgrades
---

### Post by jim_deadlock on 2012-10-14
My dad is running Ubuntu 12.04-64 and has an AMD/ATI graphics card which requires a proprietary driver otherwise it fails to load the desktop environment. This in itself is fine, however, it breaks every time there's a kernel upgrade and it's tedious having to reinstall the driver all the time. Is there any way to make the driver permanent through kernel upgrades?

---

### Post by jim_deadlock on 2012-10-16
Anyone?

---

### Post by qamelian on 2012-10-16
This will happen if you install the drivers from the AMD website. If you install the proprietary FGLRX drivers through Software Center / Synaptic / Additional Drivers, the necessary kernel modules will be rebuilt automatically whenever there is a kernel update. This doesn't happen if you are using the version downloaded from the AMD site.

---

### Post by jim_deadlock on 2012-10-16
Unfortunately I could never manage to get the fglrx driver working despite much effort. At least now I know the answer to my question so thanks.

---

