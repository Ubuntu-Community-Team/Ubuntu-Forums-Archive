---
title: "Ubuntu Won't Boot"
date: 2007-04-28
forum: Installation &amp; Upgrades
---

### Post by Joe Hammon on 2007-04-28
Hello,

I just completed my first ever installation of Ubuntu (Server 6.06.1) on an AMD PC with a Mylex DAC960 RAID controller. The install seemed to go OK but when the computer rebooted Ubuntu failed to load.  I see the following as it tries to boot:

GRUB loading
root
kernel /vmlinux
initrd /initrd
savedefault
boot

and then the screen goes black and the PC reboots in an endless loop.
Any ideas why this is happening?
I previously had Fedora Core 2 running on this PC and had no problems. I thought rather than upgrade to the newest Fedora Core I would try Ububtu. Maybe this wasn't such a good idea :(

Thanks for any help.

Joe

---

### Post by spd106 on 2007-04-29
There are two main ways to troubleshoot this depending on how confident you are feeling.

The uber-hacker way would be to switch to the grub command line and examine the boot partition, looking for the kernel and initrd image. Unless you know what you are doing this will be time consuming and rather tricky, but an opportunity to learn.

The other way that is far easier would be to boot then desktop cd and examine the filesystem from there. You will first have to mount the root partition. I suggest that you check the /boot/grub/menu.lst and /boot/grub/device.map files. Post them here if you are unsure, along with a more detailed description of your hardware and partitioning setup.

Good luck

---

