---
title: "Grub Error"
date: 2007-02-27
forum: Installation &amp; Upgrades
---

### Post by qwerkus on 2007-02-27
After having spent a long time with FreeBSD, I finally decided to try out Xubuntu :). So I got the LiveCd, and performed an installation on the second partition of the only hard drive from my laptop. After Rebooting, grub started as expected, but I m simply unable to load anything else than then the single-user recovery mode, getting a "Error 1: Filename must be either an absolute pathname or blocklist"

One must know that I'm running it from a hacked Windows-loader, which starts first, and points to a self-made linux boot-sector (with dd) and to a self-made bsd boot-sector. As grub loads after selection, i don't think the problem is a due to a wrong boot sector file, but i can be wrong about this....

Anyway: here's my fdisk -l

 ```

Disk /dev/hda: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

Device Boot      Start         End      Blocks   Id  System
/dev/hda1               1        1274    10233373+  a5  FreeBSD
/dev/hda2            1275        2448     9430155   83  Linux
/dev/hda3   *        2449        3753    10482412+   7  HPFS/NTFS
/dev/hda4            3754        7296    28459147+   f  W95 Ext'd (LBA)
/dev/hda5            3754        7230    27928971    b  W95 FAT32
/dev/hda6            7231        7296      530113+  82  Linux swap / Solaris

```

and the end of the /boot/grub/menu.lst file:

```

## ## End Default Options ##

title           Ubuntu, kernel 2.6.17-11-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-11-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-11-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-11-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-11-generic
boot

title           Ubuntu, kernel 2.6.17-10-generic
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro quiet splash
initrd          /boot/initrd.img-2.6.17-10-generic
quiet
savedefault
boot

title           Ubuntu, kernel 2.6.17-10-generic (recovery mode)
root            (hd0,1)
kernel          /boot/vmlinuz-2.6.17-10-generic root=/dev/hda2 ro single
initrd          /boot/initrd.img-2.6.17-10-generic
boot

title           Ubuntu, memtest86+
root            (hd0,1)
kernel          /boot/memtest86+.bin
quiet
boot

### END DEBIAN AUTOMAGIC KERNELS LIST

# This is a divider, added to separate the menu items below from the Debian
# ones.
title           Other operating systems:
root


# This entry automatically added by the Debian installer for a non-linux OS
# on /dev/hda3
title           FreeBSD
root            (hd0,2)
savedefault
chainloader     +1


```

Again: it only boots in safe-mode.

Thanks for your time,

qwerkus

---

### Post by mikewhatever on 2007-02-27
"Error 1...." that's helpful indeed. The partition for Ubuntu seem to match (hd0,1), but it looks like the one for BSD should be (hd0,0) according to the fdisk.

---

### Post by qwerkus on 2007-02-27
I've just updated the post, with the complete error message.
You're right about the BSD partition, but it doesn't really matter, since I'm starting it from the Windows Nt boot loader.
Here's the full boot process of my Xubuntu:

1. Computer starts, mbr is loaded
2. It points to the windows partition (hda3), which contains the Nt-bootloader
3. The Nt-bootloader has 3 options: Windows, FreeBSd and Linux
4. If "Linux" is chosen, the Nt-loader points to the address of the Grub-loader, on (hda2)
5. Grub starts, with the different Ubuntu kernels:
-in recovery mode, it boots fine
-in normal mode, it gives: "Error 1: Filename must be either an absolute pathname or blocklist"

So maybe the kernel-loading lines form the menu-lst file are wrong ?
How to correct them ?

Thank you,

qwerkus

PS: If you wonder why the complicated boot process; it's just because I was tired of having my mbr messed up at each new windows re-installation...

---

### Post by qwerkus on 2007-02-27
After digging seriously into GRUB documentation, i finally found out that the "savedefault" command from the menu.lst file sometimes cause troubles: so i removed it... ans now it works !

---

