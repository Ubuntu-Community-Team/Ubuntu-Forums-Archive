---
title: "Ubuntu 17.10 to 18.04 Server upgrade, failure on reboot"
date: 2018-05-17
forum: Installation &amp; Upgrades
---

### Post by lazr47 on 2018-05-17
I have an Ubuntu 17.10 server running on a VMWare guest that is having problems (not booting) when upgraded to 18.04. The upgrade seemed to go smoothly, I don't recall any problems that jumped out, after the upgrade I ended up with an apparently functional 18.04 system that suggested I reboot. However, once it reboots it goes right into initramfs with the message:

...
Begin: Mounting root file system ... Begin: Running /scripts/local-top ... WARNING: Failed to connect to lvmetad. Falling back to device scanning.
...
mount: mounting /dev/mapper/vg1-root on /root failed: No such device
...
initramfs prompt

I have a snapshot of 17.10 I can go back to, a snapshot of 18.04 right before I rebooted, and the initramfs prompt where the system is currently. So I can try any suggestions or collect information in any 3 of these states. Is this a problem with grub or something?

So far I've gone back to 17.10 and upgraded again just to try and notice anything odd (didn't note anything), I've also tried running update-grub/update-grub2 in 18.04 before the reboot & also tried going into all 4 environments listed in 'Advanced options for Ubuntu' (same result):
Ubuntu, with Linux 4.15.0-20-generic
Ubuntu, with Linux 4.15.0-20-generic (recovery mode)
Ubuntu, with Linux 4.13.0-39-generic
Ubuntu, with Linux 4.13.0-39-generic (recovery mode)

Any help is appreciated.

---

