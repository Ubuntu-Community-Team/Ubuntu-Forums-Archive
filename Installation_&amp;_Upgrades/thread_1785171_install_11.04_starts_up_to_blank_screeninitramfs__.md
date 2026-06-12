---
title: "install 11.04 starts up to blank screen/initramfs  prompt"
date: 2011-06-17
forum: Installation &amp; Upgrades
---

### Post by DoubleSheds on 2011-06-17
I'm new to Umbuntu. I installed Umbuntu (MythBuntu 11.04 as backend system) and initially when starting it just went to a blank screen (no prompt, nothing). After going through safe mode I was able to get to a prompt and into the UI in low graphic mode.

After updating the graphic drivers (nvidea) to the latest and changing some grub options (GRUB_CMDLINE_LINUX_DEFAULT="acpi=off splash") when I restarted it went to the busybox initramfs prompt. I typed "exit" and the UI started up normally.

The next time I restarted it went through to a blank screen. I typed "exit" again and enter and the UI started up normally again (even though I couldn't see what I was typing at the time).

While I was going through the recovery mode I do remember some messages about disk not found/mounted, when I googled it I found stuff about entering rootdelay=90 in menu.lst which doesn't exist anymore. Is there a similar option I can enter somewhere in 11.04?

Also I'm new to Ubuntu (in fact any Linux distro as an admin), where would I find any log files that may help with finding the problem.

thanks.

---

### Post by YesWeCan on 2011-06-18
try 'dmesg | more' or for convenience 'dmesg > temp' and use gedit to browse temp.

---

### Post by DoubleSheds on 2011-06-19
Thanks. Using that I did find the error and it was disk not found. Adding "rootdelay=90" to the end of my GRUB_CMDLINE_LINUX_DEFAULT line in /etc/default/grub has done the trick.

:)

---

