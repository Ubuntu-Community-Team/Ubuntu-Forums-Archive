---
title: "Certain tasks fail in preseed/autoinstall late-commands but work post-install"
date: 2021-08-03
forum: Installation &amp; Upgrades
---

### Post by brsolomon on 2021-08-03
How does the target environment at the time of ```
preseed/late_command
``` (Bionic) or ```
late-commands
``` (Focal) differ from the environment in the target after the install has completed and the target has rebooted to a console login?


I've found that certain commands and services break or are not available when run as late-commands.


For instance:


- [rsyslog.service not found by Ansible during preseed late_command]("https://askubuntu.com/q/1354620/919528")
- [Certain commands (e.g. modprobe or usermod) fail as late-commands in Ubuntu autoinstall]("https://askubuntu.com/q/1346355/919528")
- /bin/bash also seems to be unavailable (only /bin/sh is)


What I'm trying to better understand is how the target environment, during the late-command(s) phase, differs from the environment after the install has completed fully and a user has logged in through the console.

---

### Post by brsolomon on 2021-08-04
This question was answered here: [https://askubuntu.com/a/1355846/919528](https://askubuntu.com/a/1355846/919528)

One main factor influencing the difference in behavior is that `curtin in-target` is effectively a chroot call. systemctl (and possibly other commands) simply don't work in a chroot environment.

Another item to be aware of is that the kernel updates during the install process. Prior to a reboot, things such as `/usr/sbin/modprobe` may behave weirdly due to them looking for an outdated kernel version.

---

### Post by MAFoElffen on 2021-08-04
Thank you for sharing that. It was of interest to me.

---

