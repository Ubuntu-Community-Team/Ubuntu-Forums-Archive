---
title: "Incomplete Edgy upgrade hangs at boot"
date: 2006-11-16
forum: Installation &amp; Upgrades
---

### Post by DFLiddle on 2006-11-16
The computer in question is a Dell Latitude C400 notebook, which has the option of booting (via GRUB) to Windows XP, Suse 10.1, and Edubuntu 6.06. I'm really a newbie experimenting with Linux so that a) I put away my ignorance, and b) I develop some proficiency.

The upgrade process from Dapper to Edgy initially failed because of a broken Samba symlink, which I repaired thanks to [a post from Carmelo]("http://ubuntuforums.org/showthread.php?t=214848").

My upgrade seemed to be going smoothly after that, but I left it to go to a seminar and came back to a blank screen. When Edubuntu boots now, it reports on the splash screen that the loading of hardware drivers "failed". Then it enters text mode and stops with the line,

* Running local boot scripts (/etc/rc.local)     [ ok ]

There's no response after that.

It will do a normal termination and reboot when I press Ctrl+Alt+Del. I am able to boot into Recovery Mode, so the command line is available to me. The only issue I had with the original installation was making sure that I was in VGA mode so that the display didn't die in the middle of the process.

P.S. This is the only OS my 6-year old son uses right now, so I know he'd appreciate it if you could help his dad get it working again!

---

### Post by DFLiddle on 2006-11-16
Well, I suppose that I should have thought of this earlier ...

It occurred to me that maybe, just MAYBE, I should reconfigure GRUB to boot to the new Ubuntu kernel. So I booted into Suse, asked YAST to propose a new configuration, wrote down the new kernel version, and then edited menu.lst manually. Edubuntu then booted normally, and I can now finish the distribution upgrade process.

---

