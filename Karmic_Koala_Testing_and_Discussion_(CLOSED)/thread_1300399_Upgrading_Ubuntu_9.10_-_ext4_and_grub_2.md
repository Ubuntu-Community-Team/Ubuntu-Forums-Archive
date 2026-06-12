---
title: "Upgrading Ubuntu 9.10 - ext4 and grub 2"
date: 2009-10-24
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by SevinK on 2009-10-24
Hello,

I have 9.04 Jaunty installed and with the upcoming 9.10 due to release very soon, I will most likely upgrade to it. However, I have been reading that it will automatically upgrade to ext4 and grub2, which is good. However, I'm _hesitant_ to upgrade because I'm afraid it might mess up my grub configuration. I have grub legacy installed currently and I'm dual-booting with Windows XP. Will upgrading mess up my grub boot? My /boot is not on a separate partition.

Here is my menu.lst if it matters:
> ## ## End Default Options ##

title        Ubuntu 9.04, kernel 2.6.28-15-generic
uuid        c2352913-1222-4b11-884a-18bff475d157
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c2352913-1222-4b11-884a-18bff475d157 ro 
initrd        /boot/initrd.img-2.6.28-15-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-15-generic (recovery mode)
uuid        c2352913-1222-4b11-884a-18bff475d157
kernel        /boot/vmlinuz-2.6.28-15-generic root=UUID=c2352913-1222-4b11-884a-18bff475d157 ro  single
initrd        /boot/initrd.img-2.6.28-15-generic

title        Ubuntu 9.04, kernel 2.6.28-11-generic
uuid        c2352913-1222-4b11-884a-18bff475d157
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c2352913-1222-4b11-884a-18bff475d157 ro quiet splash 
initrd        /boot/initrd.img-2.6.28-11-generic
quiet

title        Ubuntu 9.04, kernel 2.6.28-11-generic (recovery mode)
uuid        c2352913-1222-4b11-884a-18bff475d157
kernel        /boot/vmlinuz-2.6.28-11-generic root=UUID=c2352913-1222-4b11-884a-18bff475d157 ro  single
initrd        /boot/initrd.img-2.6.28-11-generic

title        Ubuntu 9.04, memtest86+
uuid        c2352913-1222-4b11-884a-18bff475d157
kernel        /boot/memtest86+.bin
quiet

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title        Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/sda1
title        Windows XP Professional
rootnoverify    (hd0,0)
savedefault
chainloader    +1

---

### Post by rockstarrem on 2009-10-24
Well, if you *need* to upgrade, then I guess upgrade to GRUB2 now: [http://linuxhub.net/2009/07/install-grub-2-on-ubuntu-jaunty-jackalope/](http://linuxhub.net/2009/07/install-grub-2-on-ubuntu-jaunty-jackalope/)

Backup your menu.lst. Upgrading to ext4 can be done, but current files will not be updated until they are used. So, I highly suggest a clean install - I posted about it here: [http://www.digitalstance.com/?p=86](http://www.digitalstance.com/?p=86)

Anyway, here's the ext4 upgrade link, just remember what I said though: [http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21](http://maketecheasier.com/how-to-upgrade-from-ext3-to-ext4-without-formatting-the-hard-disk/2009/04/21)

---

### Post by SevinK on 2009-10-25
I just upgraded to GRUB 2. Now I'm wondering, is it really that worth it to upgrade to ext4? Are the differences that noticeable? I'm just using Ubuntu for productivity (laptop), not for any heavy computing.

---

### Post by sevenflo on 2009-10-25
weird....I've been reading that it WON'T upgrade to GRUB2 automatically as this is an 'inherently risky process'

Source: [http://www.ubuntu.com/getubuntu/releasenotes/910overview](http://www.ubuntu.com/getubuntu/releasenotes/910overview)

---

### Post by rockstarrem on 2009-10-25
You need to manually upgrade to GRUB2.

---

### Post by Mark Phelps on 2009-10-25
> **SevinK said:**
> ... However, I have been reading that it will automatically upgrade to ext4 and grub2 ...

Doing an in-place upgrade to 9.10 retains both the legacy GRUB and the existing filesystem (most probably, ext3).

Both GRUB2 and Ext4 are used by default in NEW installations.

---

### Post by SevinK on 2009-10-25
> **Mark Phelps said:**
> Doing an in-place upgrade to 9.10 retains both the legacy GRUB and the existing filesystem (most probably, ext3).

Both GRUB2 and Ext4 are used by default in NEW installations.
That's the answer I was looking for. An in-place upgrade will still retain my grub legacy and ext3 filesystem, even when Karmic becomes my default OS instead of Jaunty.

So, I already manually upgraded to GRUB2 w/o a problem. Should I just manually upgrade to ext4 now, and then when Karmic comes out, upgrade to that?

---

### Post by Mark Phelps on 2009-10-26
> **SevinK said:**
> So, I already manually upgraded to GRUB2 w/o a problem. Should I just manually upgrade to ext4 now, and then when Karmic comes out, upgrade to that?

I don't believe it provides an upgrade option to Ext4, so if you want that, then yes -- do the conversion now, prior to the upgrade.

---

