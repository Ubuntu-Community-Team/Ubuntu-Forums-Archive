---
title: "Reboot doesn't reboot"
date: 2009-03-13
forum: Jaunty Jackalope Testing and Discussion (CLOSED)
---

### Post by MacUntu on 2009-03-13
This happens on two up-to-date systems now. Rebooting the system via "System > Shut Down... > Restart" or "reboot now" results in a "soft reboot" - no BIOS POST, no GRUB, the system just restarts with the running GRUB entry.

Any idea what could be wrong?

---

### Post by forumache on 2009-03-13
Strange. The item System|Shutdown was removed one month ago in Jaunty...
but you still have it.

This soft reboot is implemented by kexec (package kexec-tools) but, as far as I know, Ubuntu did not implement it in the default instalation.

---

### Post by MacUntu on 2009-03-13
Hm... time to test a Live-CD then. Thanks for the info.

---

### Post by MacUntu on 2009-03-13
For the "System > Shut down..."-dialog: I don't use the user switch applet so that's ok.

kexec-tools seems to be the culprit of the reboot thing. Purging it gave me back the old behaviour. Seems I installed it with makedumpfile for kernel compiling.

Edit: Seems to be a regression: [https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/251242](https://bugs.launchpad.net/ubuntu/+source/kexec-tools/+bug/251242)

---

