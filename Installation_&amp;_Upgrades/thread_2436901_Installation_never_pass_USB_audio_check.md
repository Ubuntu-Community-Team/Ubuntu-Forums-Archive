---
title: "Installation never pass USB audio check"
date: 2020-02-15
forum: Installation &amp; Upgrades
---

### Post by igobor on 2020-02-15
Hi!
I'm trying to install Ubuntu(Ubuntu 18.04.4 LTS or 19.10) on new build and installation never pass this.
[ATTACH=CONFIG]285028[/ATTACH]

I found another post on web with  the same problem. Is there any way to solve it?
Thanks
build
ASRock TRX40 Creator
AMD Threadripper 3960x
RTX 2070

---

### Post by CatKiller on 2020-02-15
[https://www.phoronix.com/scan.php?page=article&item=amd-linux-3960x-3970x&num=2](https://www.phoronix.com/scan.php?page=article&item=amd-linux-3960x-3970x&num=2)

> Thankfully there is the "mce=off" kernel command line parameter to disable the MCE kernel code. So I tried that and sure enough the systems now booted without any problems!

---

### Post by domih2 on 2020-02-22
Rhaaaah, I went through the same exercise too, works OK but does not pass the after-installation sudo apt update && sudo apt upgrade -y + reboot.

1. Boot from 19.10 installer on USB stick
2. Freezes in the middle
3. Retry and boot installer with 'e' in GRUB to add the "mce=off" to the Linux cmd line then F10. Boots fine. Install on nvme goes OK.
4. Boot from nvme, works fine even without the "mce=off" (*&^%$#@!) Add it anyway to /etc/default/grub + update-grub.
5. sudo apt update && sudo apt upgrade -y. Check that /boot/grub/grub.cfg still has the "mce=off" in the 3 linux lines. Yep. Reboot.

==> Freezes in the middle again.

Tried the following variations:

in 4. Not adding the "mce=off"
in 4. sudo systemctl set-default multi-user.target to boot in console mode instead of graphical.

After the sudo apt update && sudo apt upgrade + reboot, it ends up with:

- BIOS logo appears with prompt to enter it or not
- Gray screen (Grub)
- Motherboard logo
- Black screen

==> The Linux console or the graphics login screen never appear.

What am I missing?

TIA!

Hardware: Asus Zenith II Extreme BIOS 807 + TR 3960X.

---

### Post by domih2 on 2020-02-26
> **domih2 said:**
> Rhaaaah, I went through the same exercise too, works OK but does not pass the after-installation sudo apt update && sudo apt upgrade -y + reboot.

I solved my problem by switching to Manjaro 19 (XFCE or Mate) which runs kernel 5.4.x and apparently supports the new ACPI and MCE thingies that come with the Threadripper 3000.

I'll switch back (or not) to Ubuntu (Mate) when their next LTS brings at least kernel 5.4.x.

---

### Post by domih2 on 2020-03-13
Ubuntu Mate 20.04 LTS pre-release (daily build) works fine too :-)

[http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/](http://cdimage.ubuntu.com/ubuntu-mate/daily-live/current/)

---

