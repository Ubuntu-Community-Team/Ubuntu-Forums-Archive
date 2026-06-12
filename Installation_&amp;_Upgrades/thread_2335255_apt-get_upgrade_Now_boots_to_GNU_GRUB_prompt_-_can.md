---
title: "apt-get upgrade Now boots to GNU GRUB prompt - can't get past it"
date: 2016-08-26
forum: Installation &amp; Upgrades
---

### Post by mike_johnson2 on 2016-08-26
I've been using 14.04, and just used the upgrade command.

Things happened, it asked me if I wanted to keep my grub config file or use the new one.
I chose to use the new one. It sat for a while, then rebooted.

On reboot, it brings up a GNU GRUB version 2.02 beta2-9ubuntu1.12 label at the top, with a grub prompt.

Nothing works now.

Does anybody know how to get past this???

---

### Post by grahammechanical on 2016-08-26
What upgrade command? The usual apt-get update/apt-get upgrade pair of commands or some other command? Have you upgraded from 14.04 to 16.04? Please explain, "nothing works."

Several problems could be listed under "nothing works." They each have different solutions. For example, one solution to "nothing works" is re-install.

---

### Post by mike_johnson2 on 2016-08-27
Well, I probably was upgrading to 16.04 I figure. What ever it upgrades to when you use the upgrade command.
But I've never been in the grub screen before and I don't know how to get out.
I used apt-get upgrade, and I would love to get back to my user login prompt from the gnu grub screen.

---

### Post by Trogladyte on 2016-08-27
I am no expert, but when my upgrade from 14.04 to 15.10 failed and dumped me at tty1 on reboot, this is what got me my GUI back:

```
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade
sudo dpkg --configure -a
```

---

### Post by mike_johnson2 on 2016-08-28
Well, I believe the problem may have been that the upgrade was interrupted. So I did a full clean install.
I trust that more anyhow.
Thanks

---

