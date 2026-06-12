---
title: "Live usb boot fails if the usb key is /dev/sdc?"
date: 2010-05-05
forum: Installation &amp; Upgrades
---

### Post by hugebrush on 2010-05-05
I created a Ubuntu live usb&#65292;it works fine on my notebook, but boots fail on my desktop pc. I found that /dev/sdb1 is always mounted to /cdrom when booting, but usb key is /dev/sdc on my desktop pc, it causes sequence booting process which depend upon files under /cdrom fails.

---

### Post by brc816 on 2010-05-05
I'm seeing a very similar problem on both of my LL 10.04 LTS installations.

One of them is a "real" installation to a 16GB Cruzer thumb drive. It can boot LL very nicely and works (albeit slowly), but it will NOT boot the Windows XP installation on the first hard drive nor the openSUSE 11.2 installation on the second hard drive. I have GRUB 0.97 installed on the MBR of the first hard drive and it permits me to boot either XP or openSUSE.

But, when I created the Cruzer installation, and then attempt to boot Windows XP, I get:

```
error: no such device: 0987ba11090e3069
error: invalid signature

Press any key to continue...

```

The results from attempting to boot the openSUSE installation are horrific, resulting eventually in it dying during system initialization and dumping me to a very ugly 320x200 text shell prompt.

I get a very similar result when I boot the other installation I made to a 1TB USB external hard drive, with a GPT and LVM. It will boot beautifully into the proper LVM partition for Lucid Lynx, but attempts to boot XP or openSUSE fail miserably because the information that the GRUB2 initial installation tools use is wrong, and the UUIDs don't match.

My suspicion is that GRUB2 is barking up the wrong tree when it's booting. I had the same problem under GRUB; I have another 250GB USB external hard drive from which I can boot into any of several different Linux installations (including Karmic) *BUT* I had to adjust my menu.lst to specify the correct spindle/partition for each installation so that it would work properly with GRUB's notion of what drive was where. I.e., the USB drive was 'sda' or (hd0) in GRUB parlance, XP was on (hd1) and openSUSE on (hd2). However, I don't see an easy way to work around this issue under GRUB2 since we're not supposed to directly edit /boot/grub/grub.cfg and adding custom entries doesn't solve the problem with the incorrect os_prober-generated entries. It would be nice if the UUID search algorithms would check other spindles to see if the desired UUID shows up *somewhere* and perhaps offer some temporary or permanent means of fixing the problem.

---

### Post by hugebrush on 2010-05-06
There's a floppy driver configed in my desktop pc's BIOS, but there isn't a floppy driver. It's the really cause of live usb boot fails, disable flopply driver in BIOS, live usb boot fine.

---

