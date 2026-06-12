---
title: "hotplug error"
date: 2005-05-08
forum: Installation &amp; Upgrades
---

### Post by deuce666 on 2005-05-08
I've read a lot of the posts on here about errors with hotplug that say to use various commands and stuff to get it to work, but i can't even get a command prompt, i just installed hoary successfully but it hangs at "Starting hotplug Subsystem...." on startup....

system specs-

Compaq 6450NX

NVIDIA FX5200 128MB (PCI)
Seagate 120GB HD
some onboard soundcard
Realtek OnBoard Ethernet
intel extreme graphics onboard video *i'm using the NVIDIA

edit:
I pressed Ctrl-C a bunch before it started loading hotplug and it looks like it's doing okay...but i'm not sure if this is just a temporary fix or not

---

### Post by alastair on 2005-05-08
If you can get some system logs, might help i.e.

/var/log/syslog

Could be an "acpi" issue perhaps - try booting with "acpi=off" i.e.

ESC at boot -> grub menu
"e" to edit kernel line
add "acpi=off" at end

---

### Post by deuce666 on 2005-05-08
k thanks, i'm into gnome now with the onboard video but i'm gonna try to set up my nvidia...so wish me luck haha

---

