---
title: "dual boot - error 17 on install"
date: 2007-03-16
forum: Installation &amp; Upgrades
---

### Post by platinumpt on 2007-03-16
I've been having a little trouble getting dual booting working.

As it stands, I have a single 160gb hard drive in my desktop machine, I created a partition of 25gb and did a fresh install of windows Xp which works fine.

Popped in the ubuntu CD, and selected install, and let it resize my partitions automatically (use largest free space).

Upon re-boot it just gives me the error:

GRUB Loading stage1.5
GRUB Loading, please wait...
Error 17

I can get windows working by running fixmbr in the recovery console, but obviously that just gets it back to square one.

Did a bit of a search on error 17 issues, but they mostly seem to be on multi hard drive setups and grub not knowing which one to use...

Any help ? :)

---

### Post by scxtt on 2007-03-16
well, since you've got one HDD, it has to be (hd0,*), we just need to figure out what * should be ...

what's the output of "sudo fdisk -l"?

and if you can figure out what grub is currently trying to use that's giving you the Error 17, that would help ... (the grub loader can tell you) ...

---

### Post by platinumpt on 2007-03-16
thanks, alright fdisk -l returns:

/dev/hda1 - HPFS/NTFS
/dev/hda2 * - Linux
/dev/hda3 - Extended
/dev/hda4 - W95 FAT32
/dev/hda5 - Linux swap / Solaris

---

### Post by scxtt on 2007-03-16
it should be using (hd0,1) to boot "Linux" ... can you still get to a grub menu to see what it's using?

---

### Post by platinumpt on 2007-03-16
It doesnt really give me the grub menu at all - but heres the menu.lst file if that helps!

```

## ## End Default Options ##

title		Ubuntu, kernel 2.6.17-10-generic
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd2 ro quiet splash
initrd		/boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title		Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root		(hd0,1)
kernel		/boot/vmlinuz-2.6.17-10-generic root=/dev/hdd2 ro single
initrd		/boot/initrd.img-2.6.17-10-generic
boot

title		Ubuntu, memtest86+
root		(hd0,1)
kernel		/boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title		Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hdd1
title		Microsoft Windows XP Professional
root		(hd0,0)
savedefault
makeactive
chainloader	+1

```

cheers

---

### Post by scxtt on 2007-03-16
try  changing "root=/dev/hdd2" to "root=/dev/hda2" ...

---

### Post by platinumpt on 2007-03-16
I did think to try that just after I posted, and did - but same error 17 :(

---

### Post by platinumpt on 2007-03-19
Ah well, messed around for hours on the weekend trying to figure this out, ended up scrapping the idea and just heading back to XP - maybe next time!

---

