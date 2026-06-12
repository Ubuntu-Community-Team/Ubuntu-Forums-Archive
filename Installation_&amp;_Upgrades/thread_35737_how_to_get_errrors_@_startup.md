---
title: "how to get errrors @ startup"
date: 2005-05-20
forum: Installation &amp; Upgrades
---

### Post by sutabi on 2005-05-20
I installed, but it hangs @ hotplug subsystem, I read past topicsand nothing much on out how find out the error.

---

### Post by bored2k on 2005-05-20
[QUOTE=sutabi]I installed, but it hangs @ hotplug subsystem, I read past topicsand nothing much on out how find out the error.[/QUOTE]
 You mean how to fix it right ?
Well, select Recovery mode on GRUB boot loader, then do this
chmod -x /etc/init.d/hotplug

Then reboot with the reboot command load up normally.

---

### Post by sutabi on 2005-05-20
same problem in recorvery mode. Also um... the installtion didn't compltete really, it just copied fromthe cd to HD and reboot and the rest is supoe to unpack and install, but it freezes at hotplug. I tried editing in grub, nothing seems to help, I cant even find out the real problem.

---

### Post by bored2k on 2005-05-20
Grub is not the problem. The problem is disabling hotplug execution. You achieve this through
chmod -x /etc/init.d/hotplug

Read ubuntuguide.org's how to gain root access with disc.

---

