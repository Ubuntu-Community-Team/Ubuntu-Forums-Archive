---
title: "MBR IProblem"
date: 2012-02-06
forum: Installation &amp; Upgrades
---

### Post by Papi47 on 2012-02-06
I have had 11.10 running with no real issues for about a month now.  Last week there was an update that installed a pae kernel.  When I rebooted all I got was a flashing cursor/blank screen.  The only thing that gets me to the grub menu is to ctrl/alt/del out of the blank screen and then F12 on the Dell boot screen.  Selecting boot from 1st drive brings up grub menu and all is well again.  I have reloaded several times, tried the chroot method and load grub & nada.  Installed Boot Repair, had it repair the MBR & reinstalled.  Nothing changed.  Below is link to the boot info script.  Any Ideas will be greatly appreciated.

[http://paste.ubuntu.com/832165/]("http://paste.ubuntu.com/832165/")

I figured out the problem.  My 8gb memory card had a an empty boot sector on it and Bios set to usb/cd/hd.  Popped out the card and booted fine.

---

