---
title: "(initramfs prompt) Upgraded to 10.04 from 9.10. Not booting :-("
date: 2010-05-18
forum: Installation &amp; Upgrades
---

### Post by aquanav on 2010-05-18
Hi there

I was using ubuntu 9.10 on my PC (I had only ubuntu and no other OS, and only a single installation of ubuntu). I recently upgraded to 10.04, and the installation/upgradation went on smoothly. After I completed upgrading and hit restart, this is what I get upon booting:

Gave up waiting for root device. Common problems
Gave up waiting for root device. Common problems:

-Boot args (cat /proc/cmdline)
-Check rootdelay= (did the system wait long enough?)
-Check root= (did the system wait for the right device?)
-Missing modules (cat /proc/modules; ls /dev)

ALERT! /dev/disk/by-uuid/34e5c1 blah blah does not exist blah

and then it says dropping to shell, something called BusyBox! and a prompt called initramfs appears.

I still have the live CD I used initially for installing 9.10. ANy idea how to work around this?


Thanks and regards,

-Navin

---

### Post by elanari on 2010-05-18
I have the very same problem. Except that I didn't make any updates or installs before rebooting my computer.
If someone has any ideas, it would be very welcome!

---

### Post by _Duhhh on 2010-05-21
I had the exact same problem. I edited the GRUB entry and turned off QUIET on the boot entry to see what was happening, and saw that it dropped into busybox a few seconds BEFORE finding the HD. I started adding rootdelay until it would boot reliably. I'm sitting at rootdelay=35 now, and it has booted a few times in a row (30 failed once).

Karmic didn't need any delay, and Lucid needs 35? OK, if that's what it takes. This is on a system with a Dell SAS IR controller.

---

