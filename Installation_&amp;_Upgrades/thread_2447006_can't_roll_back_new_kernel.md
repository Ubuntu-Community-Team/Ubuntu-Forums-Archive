---
title: "can't roll back new kernel"
date: 2020-07-10
forum: Installation &amp; Upgrades
---

### Post by bitter_mike on 2020-07-10
Hi all,

I recently did a fresh install of 20.04, which went ok. The initially installed kernel was 5.4.0-26-generic, but I immediately updated to 5.4.0-40-generic. That hosed it completely: it hangs on the splash screen. I can still boot with the old kernel and I want to stick with it, so I went to try and uninstall the new kernel, but the package manager will only remove it if it can install the 5.4.0-40-unsigned package. If I try to uninstall that, it makes me install the original generic kernel. 

How do I actually fully remove this thing and get it out of the GRUB menu so I can let my computer boot up normally?

Thanks for any help.

Mike

---

### Post by kc1di on 2020-07-12
I use[ timeshift]("https://linuxconfig.org/ubuntu-20-04-system-backup-and-restore") to get a snapshot of the system before a kernel upgrade that way you can rollback to the previous system if need be. Good luck.
Also by accessing the Grub menu at boot.  by either hitting the esc key (uefi) or tab key (bios) you can boot to the former kernel and then remove the troublesome one. Note you can not remove a kernel that is in use.

---

### Post by mastablasta on 2020-07-13
try in terminal: [https://askubuntu.com/questions/621701/how-to-remove-a-newer-kernel-while-booted-with-the-older-kernel](https://askubuntu.com/questions/621701/how-to-remove-a-newer-kernel-while-booted-with-the-older-kernel)

-40 is only a security patch/bugfix, so i wonder what got hosed. what hardware do you have? do you use any additional drivers?

i suggest you boot with text mode (not quiet) or press escape on splash screen to see where the loading get's stuck.

---

