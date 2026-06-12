---
title: "Ubuntu 10.10 amd64 upgrade frozen at grub header"
date: 2010-10-18
forum: Installation &amp; Upgrades
---

### Post by FooBar3 on 2010-10-18
Hi there. I'm currently upgrading from 10.04 to 10.10 and the screen is stuck at:

```

*** 00_header (Y/I/N/O/D/Z) [default=N] ? y
Installing new version of config file /etc/grub.d/00_header ...
Installing new version of config file /etc/grub.d/30_os-prober ...
Installing new version of config file /etc/grub.d/10_linux ...
Setting up grub-pc (1.98+20100804-5ubuntu3) ...
Installing new version of config file /etc/grub.d/05_debian_theme ...
Removing update-grub hooks from /etc/kernel-img.conf in favour of
/etc/kernel/ hooks.

```

Any ideas? I've tried Ctrl-C on the upgrade terminal, nothing happened. 0% CPU use for "Maverick" which I believe is the installer, so I'm pretty sure it isn't still working. Is it very dangerous to stop the installer? I hate to stop it on the grub stage since I'd very much like for the computer to boot.

---

### Post by FooBar3 on 2010-10-19
Figured it out. I killed (both) Maverick processes in Process Monitor. Then opened up the command line and typed these commands to finish the upgrade:

```

sudo dpkg --configure -a
sudo apt-get install -f
sudo apt-get autoremove

```

If it prompts you to change your grub file, just keep your old one. I stuck with all the defaults during the "dpkg --configure -a" command by the way. That seemed to work well for me. I did a restart and it booted fine. I'm not entirely sure but I think what caused it to crash was the grub upgrade wizard. After I killed the Maverick upgrade, a grub configuration wizard came up. Anyway, it all worked out in the end.

I really like the new look!

---

### Post by Cosworth32 on 2010-11-02
I had the same problem on a samsung NC10 netbook. You fixed helped me as well. Thanks

---

### Post by red03golf on 2012-03-01
Exact same thing just happened to me.

Hard shut down (hold power button for 5 seconds),
restart,
recovery mode,
repair broken packages,
keep existing grub,
restart,
recovery mode,
drop to root shell with networking,

(then same commands):
dpkg --configure -a,
apt-get install -f,
apt-get install autoremove,

all better.

---

