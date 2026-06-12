---
title: "Ubuntu 18.04 update resulted in 'emergency mode' - trying to find the cause"
date: 2021-09-14
forum: Installation &amp; Upgrades
---

### Post by rob190 on 2021-09-14
Hi,

A reboot as part of a nornal update on an 18.04 installation failed and Ubuntu went into 'emergency mode'. I was unable to get it to boot so I did a fresh install of 20.04 on a new disk. I'm now trying to figure out what went wrong so I can prevent it happening again.

I reset the BIOS, tried booting with only the system disk in place and tried moving it to other SATA ports. The BIOS was (and is) mostly in the default state. I disabled fast boot as that had caused a lot of problems when I first bought the PC.

As far as I can tell, all the hardware works. There is a new system disk but the original disk is still installed and a disk check didn't show any errors. The PC is running all the same applications it did before.

I think there was a message about SMART failure and maybe something about ACPI but I can't find anything obvious in any of the log files and the disks all check out fine. Maybe I'm looking at the wrong log files? Or misinterpreting something?

The update was on 10 September and IIRC included a kernel update. The hardware is old: a Skylake in a Asus Z87 motherboard. It has always run without any issues and only gets rebooted once every couple of months or so. It's mostly a file server but gets occasional use for compiling large projects, simulations and various other miscellaneous stuff. Never had it crash before.

As I said, I still have the original system disk, unmodified, since the failed reboot. I'd rather not try booting off it again as I need the PC to be running at the moment. 

Where should I start looking?

---

### Post by grahammechanical on 2021-09-14
There are always two Linux kernels present that we can boot into. If we get a kernel upgrade and the reboot fails to load to a working desktop then it is still possible to boot into the old but good kernel.

At the Grub boot menu select Advanced Options for Ubuntu. You will get a list of Linux kernels. The kernel at the top of the list will be the newly installed kernel. Next on the list will be the same kernel with recovery mode. Third will the old kernel and after that will be the old kernel with recovery mode.

It is always worth trying Advanced Options and the old kernel. If that gets you to a working system keep loading Ubuntu using Advanced Options. Another update may fix what is wrong with the new kernel. Update using the terminal and you will not lose the old but good kernel. Use Software and Updater and you will lose the old kernel because Software Updater runs the autoremove command. When you have two new but good kernels you can run apt autoremove.

Regards

---

### Post by rob190 on 2021-09-15
Thanks. That's useful info but I'm curious why you think I need to try booting from the disk again. I was assuming all the information about why the boot failed would be in the log files somewhere. Is that not true?

One thing I've found which is puzzling: There's a missing crontab file. The original installation had crontabs for two of the user accounts. One of them is there but there's no sign of the other. I checked the syslog and it was running the day before the update. So I'm thinking this might be a disk issue or possibly a virus. (The disk is a Samsung EVO and I had a case with an identical disk where a number of files suddenly disappeared but that was on a windows NTFS sytem and this is ext4.) What I need is a utlity to check the validaity of an installation. I don't suppose such a thing exists does it?

---

