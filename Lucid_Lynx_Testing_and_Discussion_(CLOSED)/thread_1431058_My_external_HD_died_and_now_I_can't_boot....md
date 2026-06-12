---
title: "My external HD died and now I can't boot..."
date: 2010-03-16
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by ljrmorgan on 2010-03-16
So this morning I booted into Lucid, got as far as the ubuntu logo, and then "Waiting for /dev/sdb" appeared, and gdm never started. I discovered to my horror that my external hard drive was dead (then discovered, to my relief, that actually only the power supply was dead). I've ordered a new power supply from ebay, but I can't get into lucid (dual booting with XP).

My external drive only has one partition on it, and it's FAT32 (or maybe NTFS, can't actually remember). I haven't done anything crazy like installed grub on it, but it is set to be automatically mounted. Recovery mode doesn't seem to work at all (just get a black screen), and I can't get a login prompt on the vitual terminals.

Any suggestions on what I can do until my new power brick arrives??

Thanks for any help!

---

### Post by zika on 2010-03-16
Boot from LiveCD, edit /etc/fstab to # line that mounts Your external drive and reboot back in Ubuntu. Of course, this would work only if You use Grub...

---

### Post by ljrmorgan on 2010-03-16
> **zika said:**
> Boot from LiveCD, edit /etc/fstab to # line that mounts Your external drive and reboot back in Ubuntu. Of course, this would work only if You use Grub...
Thanks, I'll give that a shot when I get home. I was just wondering if there was something I can press to get it to skip looking for the external hard drive, given that it isn't needed by the system in any way.

---

### Post by ndefontenay on 2010-03-16
In your BIOS, remove the option of booting from USB.
You can set up USB boot to be tested after internal HD.

---

### Post by ljrmorgan on 2010-03-17
> **ndefontenay said:**
> In your BIOS, remove the option of booting from USB.
You can set up USB boot to be tested after internal HD.

Thanks, the problem wasn't grub - my external hard drive wasn't bootable, but it does get mounted automatically at boot. Since it wasn't working it held up the whole system, I was just wondering if there was a way of getting ubuntu to skip mounting it. It only has tv shows and things like that on it, not anything the system needs to function. It probably only happened because I set up my fstab badly in the first place.

Anyway, I took zika's advice, booted using a thumbdrive and commented out the crucial line in fstab. Thanks for your help!

---

