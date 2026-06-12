---
title: "Can't boot after kernel updates"
date: 2014-05-06
forum: Installation &amp; Upgrades
---

### Post by xenogere on 2014-05-06
I admit I've had a plethora of problems since upgrading to 14.04 from  13.10.  For example, my wi-fi connection now fails regularly and  requires a reboot to fix.  And my laptop can no longer suspend on its  own (always reporting a 'Power Manager: Not authorized' error).  Or having i8kmon fail to control the laptop fan, instead having it spin up then slow down, spin up then slow down, and spin up then slow down, all while the CPU and HD temperatures continue to rise.  But I'm  OK with this litany of problems simply because I can work around them.

Only now I can't boot without manual intervention.

This morning I was prompted to install several upgrades:
```
gettext:i386 (0.18.3.1-1ubuntu2, 0.18.3.1-1ubuntu3)
libgettextpo0:i386 (0.18.3.1-1ubuntu2, 0.18.3.1-1ubuntu3)
linux-image-extra-3.13.0-24-generic:i386 (3.13.0-24.46, 3.13.0-24.47)
libgettextpo-dev:i386 (0.18.3.1-1ubuntu2, 0.18.3.1-1ubuntu3)
openssl:i386 (1.0.1f-1ubuntu2, 1.0.1f-1ubuntu2.1)
linux-libc-dev:i386 (3.13.0-24.46, 3.13.0-24.47)
linux-headers-3.13.0-24:i386 (3.13.0-24.46, 3.13.0-24.47)
gettext-base:i386 (0.18.3.1-1ubuntu2, 0.18.3.1-1ubuntu3)
libasprintf-dev:i386 (0.18.3.1-1ubuntu2, 0.18.3.1-1ubuntu3)
libasprintf0c2:i386 (0.18.3.1-1ubuntu2, 0.18.3.1-1ubuntu3)
linux-headers-3.13.0-24-generic:i386 (3.13.0-24.46, 3.13.0-24.47)
linux-image-3.13.0-24-generic:i386 (3.13.0-24.46, 3.13.0-24.47)
libssl1.0.0:i386 (1.0.1f-1ubuntu2, 1.0.1f-1ubuntu2.1)
```

So  I installed these updates.  I was then told I needed to reboot.  So I  did.  And now GRUB fails to boot Xubuntu.  I get dropped to a grub>  prompt.

Here's what I've tried.

```
sudo update-grub
```

That  resulted in a new menu entry pointing to Ubuntu 14.04 LTS, which also  fails to boot.  And the other menu entries now fail to boot.

When at the grub> prompt:

```
set root=hd0,msdos5
set prefix=(hd0,msdos5)/boot/grub
configfile /boot/grub/grub.cfg
```

That resulted in a return to the grub> prompt.

So when at the grub> prompt again:

```
set root=hd0,msdos5
set prefix=(hd0,msdos5)/boot/grub
linux /boot/vmlinuz-3.13.0-24-generic root=/dev/sda5 ro
initrd /boot/initrd.img-3.13.0-24-generic
boot
```

Immediately  after entering the initrd command, I get this: "error: attempt to write  outside of disk 'hd0'."  Despite that, I can boot into Xubuntu with the  boot command.

Attempting to use any of the grub menu options  results in a crash where all sorts of lights start flashing and I have  to hard-reboot the computer.

Obviously I'm not a technical idiot,  though I'm not a Linux guru either.  I'll admit that.  Though I'll  stress that I know what I'm doing.

So, where does this leave me?   Having to manually boot the computer each time it restarts.  The other  14.04 issues I've had are easy to work around.  This one, however, irks  me beyond my tolerance.

Any suggestions, recommendations or guidance would be greatly appreciated.

Cheers!

---

