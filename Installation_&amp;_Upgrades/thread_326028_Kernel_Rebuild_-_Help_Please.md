---
title: "Kernel Rebuild - Help Please"
date: 2006-12-26
forum: Installation &amp; Upgrades
---

### Post by Thenotsowyzewun on 2006-12-26
Hello,

Long time no see, but the combination of Edgy Eft and Beryl has grabbed my full attention back to Linux - I'm back and lovin' it!
Anyway...

I have a Rio Karma (another reason I previously needed Windows installed; the Ethernet is rubbish) and the new kernel, which is included in EdgyEft (according to uname -a anyway) is recent enough that it includes the brand new USB Rio Karma support.
Unfortunately this does not seem to have been selected during configuration; it's not enabled by default.

I would like to change this without complete recompilation of the kernel; I tried following the Kernel Upgrade thread on the boards but with no success (I have the same seemingly as yet unresolved problem as a few others; after reboot the new Kernel refuses to boot.

So if there is a way of adding this feature to my existing Kernel, please explain.

Thank you kindly, your time and interest is very much appreciated!

Duncan

---

### Post by Shutdownrunner on 2006-12-27
This will require kernel rebuild but it won't be too painful.

[LIST]
You have to run make gconfig (or make xconfig -- for  kde, or make menuconfig -- in console using ncurses)[/LIST]

[LIST]Then load configuration file for your current kernel. It's in /boot/config-[your kernel version]. [/LIST]

[LIST]Enable all the drivers you need, and also compile into kernel a driver for your filesystem (otherwise you'll get kernel panic).[/LIST]

[LIST]Save configuation[/LIST]

[LIST]
make && make install && make modules-install
[/LIST]

On a fast computer you'll manage to do it in 10 minutes.

[LIST]
reboot and pray that you didn't blow anything.
[/LIST]

---

### Post by Thenotsowyzewun on 2006-12-29
Hi,

Thanks for your response, I followed the Kernel Master Thread's instructions and maybe I didn't select the correct driver for my HDD (TBH I'm not entirely sure whether it's IDE/SCSI/SATA etc, and going into System | Administration | Device Manager and poking around doesn't seem to reveal much either (most of the device's details are "Unknown"; although they are functioning (on the original Kernel, that is; see my post in the Master Kernel Thread).

---

