---
title: "No display, unresponsive mouse and keyboard after upgrade to 2.6.17-10"
date: 2006-12-14
forum: Installation &amp; Upgrades
---

### Post by Roobert on 2006-12-14
After Edgy's self-upgrade to 2.6.17-10 today, I rebooted into a black screen; no mouse, and unresponsive keyboard. Ctrl+Alt+F1 to F12 does nothing. I can't get to a command line to troubleshoot this problem. I was forced into doing a hard reboot and selecting the previous kernel version in the grub boot list. What's going on? Any ideas?

---

### Post by bapoumba on 2006-12-15
Hi,
[http://ubuntuforums.org/showthread.php?t=318206]("http://ubuntuforums.org/showthread.php?t=318206")
Does this help ?

---

### Post by Roobert on 2006-12-15
No, it turns out the issue wasn't about nvidia drivers - I fixed the problem by editing my /boot/grub/menu.lst file and removing the 'savedefault' line from the boot options for kernel 2.6.17-10. Now Ubuntu boots normally.

---

