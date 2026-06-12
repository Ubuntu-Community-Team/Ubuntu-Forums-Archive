---
title: "Grub2 Killed - Command Line Restarts On Any Command"
date: 2012-08-10
forum: Installation &amp; Upgrades
---

### Post by MarcF on 2012-08-10
I've been attempting to configure a software raid1 using a pre existing Ubuntu 12.04 install by following the guide [http://feeding.cloud.geek.nz/2011/03/setting-up-raid-on-existing.html](http://feeding.cloud.geek.nz/2011/03/setting-up-raid-on-existing.html). I successfully completed step 4 but then couldn't get Ubuntu to boot into the degraded raid device. I read somewhere that you need to run the following command

dpkg-reconfigure grub-pc

from within the raid config, so as root, after step 4 I ran the following commands:

mkdir /tmp/mntroot
mount /dev/md0 /tmp/mntroot
chroot /tmp/mntroot
dpkg-reconfigure grub-pc

this appeared to correctly update the grub.conf to the new raid setup.

On boot I can bring up the grub boot list and by pressing 'e' I can see the correct commands. The kernel I'm trying to boot into now also gives the correct UUID for the raid drive 'md0'.

Unfortunately if I try to go any further the system restarts.

I have tried going to the grub command line by pressing 'c' at the grub menu. This succesfully brings up the command line:

grub>

Unfortunately if I type ANY command, including 'help' and press enter the system restarts.

If anyone could help shed any light on this that would be greatly appreciated.

Marc

---

### Post by oldfred on 2012-08-11
I do not know RAID. But many systems also need help with video modes. I have to use nomodeset for my nVidia card.

From the grub menu, e for edit remove quiet splash & add nomodeset.

Sometimes other boot parameters may be required.

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
[http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt](http://www.mjmwired.net/kernel/Documentation/kernel-parameters.txt)
noapic nolapic noapci noirqpoll nosmp irqpoll

---

