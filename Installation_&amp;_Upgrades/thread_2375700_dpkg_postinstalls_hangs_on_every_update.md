---
title: "dpkg postinstalls hangs on every update"
date: 2017-10-26
forum: Installation &amp; Upgrades
---

### Post by nachokb2 on 2017-10-26
I installed 17.10 since beta and been having some issues when updating the system.

Apt hangs on some packages postinst scripts.

First it was `console-setup` if I remember correctly. Later dkms modules started showing the same symptom (e.g. Virtualbox's).

Now I can't update the kernel.

It just hangs there for hours and I end up having to kill the postinst scripts. Otherwise it just hangs (left it for 12+ hours twice, nothing happens).

```
run-parts: executing /etc/kernel/header_postinst.d/dkms 4.13.0-16-generic /boot/vmlinuz-4.13.0-16-generic
dpkg: error processing package linux-headers-4.13.0-16-generic (--configure):
 subprocess installed post-installation script was killed by signal (Terminated)
Setting up virtualbox (5.1.30-dfsg-1) ...
dpkg: error processing package virtualbox (--configure):
 subprocess installed post-installation script was killed by signal (Terminated)
dpkg: dependency problems prevent configuration of linux-signed-image-4.13.0-16-generic:
 linux-signed-image-4.13.0-16-generic depends on linux-image-4.13.0-16-generic (= 4.13.0-16.19); however:
  Package linux-image-4.13.0-16-generic is not configured yet.
```

This is getting obnoxious.

-- nachokb

---

### Post by Bashing-om on 2017-10-26
nachokb2; Hello;

What results:
```

dpkg-reconfigure -a # This may take a long time, wait it out

```

See what the package manager fixes/advises - see where we go.

[INDENT]just a good place to start
[/INDENT]

---

### Post by nachokb2 on 2017-10-27
Yes, I did try reconfigure before. Left it for 12 or 13 hours. Nothing was happening.

This time somehow the grub entry was created so next reboot tried to boot the newer kernel (4.13-16) and it failed with a blank screen. So I rebooted with the older kernel, and manually uninstalled the newer version using synaptic. This was scary because I was also removing linux-generic and other generically-named packages. Then reinstalled it. Everything went smoothly. So now I'm on an updated krnel and apt does not complain anymore. Sounds like heaven right?

I'll tag this as solved.

TLDR: uninstall and reinstall latest kernel package

Thanks!

-- nachokb

---

### Post by e0012 on 2017-11-04
Hi @nachokb2,
Semi-noob here (experienced software developer but mostly new to Linux). I'm encountering probably the same thing -- I'm inclined to blame Virtualbox, since it had already been giving me dkms-related errors before I started the upgrade. Would you mind posting exactly what you did to uninstall the newer kernel?

Hoping your solution will work for me as well.
Thanks!

---

### Post by AbtZ on 2018-01-12
> **e0012 said:**
> Hi @nachokb2,
Semi-noob here (experienced software developer but mostly new to Linux). I'm encountering probably the same thing -- I'm inclined to blame Virtualbox, since it had already been giving me dkms-related errors before I started the upgrade. Would you mind posting exactly what you did to uninstall the newer kernel?

Hoping your solution will work for me as well.
Thanks!

In my case the proprietary NVIDIA driver was the culprit.

I solved it by doing the following:

1. Reboot
2. Choose Advanced -> Recovery mode in Grub
3. Select "dpkg" in the recovery mode list

It will ask you some questions in dpkg-recovery mode, just answering yes to all of them should be fine.

An [alternative solution]("https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1686107/comments/11") I read about, but haven't tried, is running "dpkg --configure -a" in a tty. On newer iterations of Ubuntu you will have to [enable ttys first]("https://askubuntu.com/questions/911560/enable-ctrlaltf1-virtual-consoles-in-ubuntu-gnome").

---

### Post by e0012 on 2018-01-12
Thanks, @AbtZ, I appreciate it!

---

