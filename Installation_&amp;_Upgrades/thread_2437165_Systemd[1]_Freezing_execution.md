---
title: "Systemd[1]: Freezing execution"
date: 2020-02-19
forum: Installation &amp; Upgrades
---

### Post by lucabecchetti on 2020-02-19
[COLOR=#242729][FONT=Arial]after a reboot, I have this screen on boot:[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial][[IMG]https://i.stack.imgur.com/q2NR4.jpg[/IMG]]("https://i.stack.imgur.com/q2NR4.jpg")[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I have a scsi disk, my root is /dev/md1[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]I started live distro on this machine, and I tried search for badblocks, but no error found, I tried to force fsck on reboot, ma nothing works.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Only way to make it bootable is to edit grub list pressing "e" during boot phase, and change line that starts with linux, from .... ro ... to ... rw .....[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]This change is not permanent, if I reboot it again, I have the same issue.[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]What can I do???? I Have ubuntu 18.04 server[/FONT][/COLOR]
[COLOR=#242729][FONT=Arial]Thanks![/FONT][/COLOR]

---

### Post by lucabecchetti on 2020-02-20
no one??

---

### Post by CelticWarrior on 2020-02-21
You need to run fsck.

The error indicates errors in the root partition but those can be and likely are just logical errors in which case searching for bad blocks isn't the way to go. The drive can be physically fine and still have logical error due to corrupt files.

---

### Post by lucabecchetti on 2020-02-27
i made fsck on root partition, but nothing works!

---

