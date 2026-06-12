---
title: "Ubuntu 12.04 Upgrade Error"
date: 2012-09-08
forum: Installation &amp; Upgrades
---

### Post by juacali on 2012-09-08
Hi
I have been running an amd 64 machine on Ubuntu 10.04 for a while.With the release of 12.04 i attempted to upgrade through the update manager.The upgrading ran successfully up to when i was prompted to restart and got errors attached,please help.

---

### Post by dgharmon on 2012-09-08
> **juacali said:**
> The upgrading ran successfully up to when i was prompted to restart and got errors attached,please help.

What is most probably means is there's some software that is missing or disable. That's a config file, I've seen those in relation to USB modems, I figure you can safely remove it.

---

### Post by juacali on 2012-09-08
I dual boot Ubuntu with Windows 7 using grub 1.5.How can i access the config file you are referring to..

---

### Post by dgharmon on 2012-09-17
> **juacali said:**
> I dual boot Ubuntu with Windows 7 using grub 1.5.How can i access the config file you are referring to..

Press <ctrl><alt><f2> and login, then type 'rm /etc/udev/rules.d/85-brltty.rules' <enter>. Then reboot by typing shutdown -r 0 now <enter>

---

