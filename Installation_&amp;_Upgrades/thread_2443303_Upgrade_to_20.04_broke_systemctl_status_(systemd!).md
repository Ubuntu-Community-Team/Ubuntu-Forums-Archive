---
title: "Upgrade to 20.04 broke systemctl status (systemd!)"
date: 2020-05-13
forum: Installation &amp; Upgrades
---

### Post by scamiran on 2020-05-13
Hi all,

I have a very, very weird bug. Much Googling has revealed nothing.

I upgraded to 20.04 yesterday. It went mostly smoothly, given that I have a strange, multiheaded system (3 GPUs, 3 monitors, 3 keyboard, 3 mice).

Most everything is still working well. Except, systemctl status no longer works properly! (at least on services, it does give output on something like machine.slice, or other .slice units).

systemctl status [anything].service results in the following output, only:
"Failed to parse bus message: No such device or address"

Example:
root@samiran-desktop:/etc/systemd# systemctl status winbind.service
Failed to parse bus message: No such device or address

This occurs from a user account, root, and sudo.

Oddly enough, most (all) other functions seem to work properly. systemctl status properly lists all the units, status-failed works properly, enable, disable, etc . . . . journalctl can properly give me status on logs, too. It's just that systemctl status <unit.service> provides a very obtuse error message that I'm really not sure what to do with.

Anyone have any suggestions?

Thanks,

samiran

---

### Post by lchristopherson on 2020-11-05
Hi scamiran,

I'm running into the same issue and wanted to check if you ever found a resolution.

Thanks,
lchristopherson

---

