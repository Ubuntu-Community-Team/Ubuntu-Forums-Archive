---
title: "Corrupted boot Ubuntu 16.4 full disc encryption"
date: 2016-11-18
forum: Installation &amp; Upgrades
---

### Post by luca1729+ on 2016-11-18
I have been using Ubuntu 16.4 with full disc encryption for about a month, installed using default installer for 64 bit desktop.

This morning it hangs with a slightly purple screen between GRUB and password request. I have run boot-repair and now it goes a little further and shows and drops to busybox. If I boot from USB I can mount the encrypted partition.

The menu scrolls through cannot process volume group ubuntu-vg many times and then exits to BusyBox with
/dev/mapper/ubuntu--vg-root does not exist.


This is the second time this has happened. About 6 weeks ago something similar happened, but I put it down to faulty hardware, replaced most of it and re-installed. I'd rather not re-install again. What am I doing wrong - shutdown last time seemed clean. I have been using disc encryption for 4 years (since 12.4) without any problems.

---

### Post by luca1729+ on 2016-11-19
I have reinstalled Ubuntu 16.04 onto a new hard drive. I still don't understand what went wrong and why it happened twice. It may have been that I installed the nvidia driver.

I tried many things before I re-installed, but couldn't get the combination of UEFI, luks and LVM working.

---

### Post by luca1729+ on 2016-11-20
It was the nVidia driver (sort of). I installed the binary driver on my new install and I had a similar experience, but it is a display/keyboard issue with grub/plymouth. I have reverted to Nouveau and everything is back to normal (except for damage I did when trying to fix the boot sequence). I need to find out what is going wrong with my video card settings (almost exactly the same setup on a laptop with binary driver and no problems).

---

