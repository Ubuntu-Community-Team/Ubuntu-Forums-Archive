---
title: "boot-repair on Ubuntu 12.10 (installed inside windows XP) failed"
date: 2017-07-10
forum: Installation &amp; Upgrades
---

### Post by Rahul_Raj on 2017-07-10
I attempted a boot-repair on Ubuntu 12.10 (installed inside Windows XP). Although, the boot-repair completed successfully, the reboot was unsuccessful.
The pastebin link is:
paste.ubuntu.com/25060820

Thanks in advance.

---

### Post by yancek on 2017-07-10
Your posted link is broken.  Both Ubuntu 12.10 and xp are very outdated and unsupported.  You do know that the wubi installer simply installs Ubuntu inside windows as a program and that it uses the windows bootloader to boot.  I don't think boot repair is going to fix that but maybe someone more familiar will have a suggestion.

---

### Post by Bucky Ball on 2017-07-10
Wubi is also unsupported. Wouldn't go there. You won't get much help with it.

---

### Post by ajgreeny on 2017-07-10
As those above have already said Ubuntu 12.10, wubi and Windows XP are all well beyond end-of-life and there is nothing anyone here in the forum can do to help you to recover that situation; certainly the boot repair pastebin you show is no help at all when dealing with wubi installs.

If you have files inside that wubi install that you need the best I can suggest is to recover them by mounting the root.disk file in the XP partition in a "real" Ubuntu hard disk installation or possibly in a live Ubuntu OS.
See [https://askubuntu.com/questions/243621/how-to-mount-root-disk-from-wubi-when-booted-from-dual-boot-install-of-ubuntu](https://askubuntu.com/questions/243621/how-to-mount-root-disk-from-wubi-when-booted-from-dual-boot-install-of-ubuntu) for information which may help.

---

### Post by ajgreeny on 2017-07-10
Query relates to end-of-life operating systems and installation mode.
If you need more help on recovery of files please start another thread with descriptive title.

Thread closed.

---

