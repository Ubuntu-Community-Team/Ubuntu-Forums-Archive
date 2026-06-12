---
title: "How to install quantal using the hd-media images?"
date: 2012-10-22
forum: Installation &amp; Upgrades
---

### Post by jamadagni on 2012-10-22
Over the past years, I have always installed new releases of *buntu directly from my HDD using the hd-media vmlinuz and initrd images available from http://archive.ubuntu.com/ubuntu/dists/<version>/main/installer-<arch>/current/images/hd-media/ and booting via GRUB using the entries:

```

        linux   /hdinst-vmlinuz ramdisk_size=14972 root=/dev/rd/0 rw --
        initrd  /hdinst-initrd

```

However, now that with Quantal the ISO is no longer a valid CD image, I am getting an error of "cannot load CD image" when I point the installer to the appropriate partition having the ISO in its root (which is detected BTW).

Can anyone help me in this regard? Thanks!

---

### Post by oldfred on 2012-10-23
If using the desktop version you can directly boot the ISO with grub2 loop mount. You do not have to extract kernel. Loopmount does not work on server version.

This will boot an ISO from a hard drive.
ISO Booting with Grub 2 from Hard drive - drs305
[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)
Examples - you may copy & edit for your path & ISO version
[https://help.ubuntu.com/community/Grub2/ISOBoot/Examples](https://help.ubuntu.com/community/Grub2/ISOBoot/Examples)
[http://ubuntuforums.org/showthread.php?t=1549847](http://ubuntuforums.org/showthread.php?t=1549847)
Boot ISO from harddrive. To install it would have to be different partition
[SOLVED] Using grub 2 to boot an iso off hard drive old examples
[http://ubuntuforums.org/showthread.php?t=1535864](http://ubuntuforums.org/showthread.php?t=1535864)

---

