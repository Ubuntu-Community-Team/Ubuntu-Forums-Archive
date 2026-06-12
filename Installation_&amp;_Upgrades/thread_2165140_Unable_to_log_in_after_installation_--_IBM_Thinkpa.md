---
title: "Unable to log in after installation -- IBM Thinkpad R31, Lubuntu 13.04"
date: 2013-08-03
forum: Installation &amp; Upgrades
---

### Post by 4NzkFXP on 2013-08-03
Hey

I just installed Lubuntu on a Thinkpad R31. Now, however, it's refusing to let me in. When I boot it it never gets any further than a blue screen with the Lubuntu logo, the five "loading" dots (though here they're all white) and a blank, black field at the bottom. I suspect the latter is for typing in my password for the encrypted LVM filesystem/home folder/whatever (which I stupidly requested as I was setting the thing up -- I reckon I wouldn't be in this situation if I hadn't checked those boxes), but apparently my password is wrong. The field disappears and dots start "loading" momentarily, and then it returns. On my third attempt, the screen disappears and I get this initramfs prompt:

> 
Gave up waiting for root device. Common problems:
- Boot args (cat /proc/cmdline)
* Check rootdelay= (did the system wait long enough?)
* Check root= (did the system wait for the right device?)
- Missing modules (cat /proc/modules; ls /dev)
ALERT! /dev/mapper/lubuntu--vg-root does not exist. Dropping to a shell! [...]

cat /proc/cmdline yields the following:
> BOOT_IMAGE=/vmlinuz-3.8.0-19-generic root=/dev/mapper/lubuntu--vg-root ro quiet splash

In other circumstances I would just do a clean install and see if that would make the problem go away, but the situation is complicated by the R31's failure (possibly unrelated, although it started a couple of boot attempts after I installed Lubuntu) to boot to a CD -- it just goes directly to the GRUB menu no matter which medium I ask it to boot from. This is a hardware question so this might not be the place to ask, but I would of course be grateful if anyone knows how to fix this.

Thanks for your time!

EDIT: Assuming that I can't boot from a CD -- which seems to be the case -- I would ideally like to know if there's a way to use the initramfs or grub prompt to boot off the Lunbutu install CD or CrunchBang USB stick I have handy, but I'm not sure if that's possible. Maybe it would be possible to use dd to erase the filesystem and replace it with one of those? I don't know. Anyway...

EDIT: Yes, I have used F12 to specify that I would like to boot off a CD; I also tried to reset the BIOS to its default settings.

---

### Post by 4NzkFXP on 2013-08-03
Never mind, now it's working again! I'll do a clean install & let you know if that solves my initial problem. Sorry to bother you, haha.

---

