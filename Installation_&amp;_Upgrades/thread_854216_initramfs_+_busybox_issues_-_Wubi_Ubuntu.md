---
title: "initramfs + busybox issues - Wubi Ubuntu"
date: 2008-07-09
forum: Installation &amp; Upgrades
---

### Post by Saigon Saigon on 2008-07-09
Dear Friends,

For some reason I can no longer boot into Ubuntu 8.04 and all I get is initramfs + busybox and a warning message saying that it cannot locate root disk.

Wubi guide suggests to perform check disk errors by "Automatically fix file system errors" is checked and click Start in Windows" - my Windows does not allow this to "start" but require the disk check to be performed by restarting the system.

I have googled and tried most other options suggested but to no avail.

I now plan to do a reinstall but would like to seek advise on how I can access data that was on the Wubi/Ubuntu home folder as well e-mails etc.

Thank you for helping out.

---

### Post by g320907aa on 2008-07-09
see the contents of casper.log by typing
cat casper.log

if it doesnt in one screen then you can setup terminal emulation with different pc and supply console=ttyS0,115200 switch on boot options menu.

---

