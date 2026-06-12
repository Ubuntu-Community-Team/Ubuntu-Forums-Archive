---
title: "Blank screen on Toshiba Satellite A505-S6030 with NVIDIA GeForce 310M"
date: 2010-06-15
forum: Installation &amp; Upgrades
---

### Post by Hans G Ehrbar on 2010-06-15
I installed Ubuntu 10.4 only the basic ubuntu server, no X-windows.
When I boot the system I first see the dmesg messages and then the
screen goes blank, also no virtual terminals.  The only way I can
access the system is through ssh.  I am attaching /var/log/dmesg and
/var/log/syslog  (I had the same problem with the gnome desktop,
therefore I reinstalled without X-windows, but still no screen.)
SOLVED: In /etc/default/grub I had to add "noapic" to the line
GRUB_CMDLINE_LINUX_DEFAULT
Originally it said
GRUB_CMDLINE_LINUX_DEFAULT="splash quiet" 
but since I wanted to see the boot messages I had commented it out,
and now it says
GRUB_CMDLINE_LINUX_DEFAULT="noapic"
This did the trick for me.  Now I can at least log into it through the command line.
Therefore I removed the attachment again.

---

