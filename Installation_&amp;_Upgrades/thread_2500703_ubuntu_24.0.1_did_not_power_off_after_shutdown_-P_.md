---
title: "ubuntu 24.0.1 did not power off after shutdown -P now or halt -p command."
date: 2024-09-09
forum: Installation &amp; Upgrades
---

### Post by fire-fly2 on 2024-09-09
Hi
ubuntu 24.0.1 did not power off after shutdown -P now or halt -p command.
Try using systemctl poweroff and systemctrl  halt.
The results were the same. The video was off but the hard disk still spinning.
update on 2024-09-23
The shutdown was trying to stop the following but was unable to. Causing the stopping loop
  /usr/bin/systemctl stop fwupd-refresh.timer
   /usr/bin/systemctl stop fwupd
   /usr/bin/systemctl stop NetworkManager.service
   /usr/bin/systemctl stop systemd-networkd.socket
   /usr/bin/systemctl stop systemd-networkd.service
   /usr/bin/systemctl stop polkit.service


Please help.

---

### Post by ActionParsnip on 2024-09-09
Does the system have a make and model?

---

### Post by fire-fly2 on 2024-09-10
It is an assembled desktop the motherboard info below. Thanks
[IMG]https://i.postimg.cc/gkb6ZvB8/Screenshot-from-2024-09-10-20-17-15.png[/IMG]

---

### Post by him610 on 2024-09-10
Try it without *-P* as that is the default, and it is unnecessary.
```
sudo shutdown now
```

---

### Post by fire-fly2 on 2024-09-10
nope, not working too.
I even try systemctl poweroff but result was negative

---

