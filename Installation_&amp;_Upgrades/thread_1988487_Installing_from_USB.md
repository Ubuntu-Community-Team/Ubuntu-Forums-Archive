---
title: "Installing from USB"
date: 2012-05-27
forum: Installation &amp; Upgrades
---

### Post by agent154 on 2012-05-27
I'm trying to put Ubuntu 12.04 onto my UBCD bootable USB and I can't seem to figure out how to do it. Let me state for the record that I'm making guesses here as to how to do it, as I don't have any experience with syslinux or grub.

I've extracted all the files from the ISO to a folder on the root of the drive, "/Ubuntu1204", and have made an attempt to translate the GRUB boot loder loopback.cfg to syslinux.

I've added the following block of code to my custom.cfg file for UBCD:

```
LABEL -
MENU LABEL Ubuntu 12.04 x86
TEXT HELP
 Launch the Ubuntu 12.04 LiveCD
ENDTEXT
COM32 /Ubuntu1204/boot/syslinux/linux.c32
APPEND /Ubuntu1204/casper/vmlinuz  file=/Ubuntu1204/cdrom/preseed/ubuntu.seed boot=casper iso-scan/filename=/Ubuntu1204/casper/filesystem.squashfs initrd=/Ubuntu1204/casper/initrd.lz quiet splash
```

So far, it starts to boot up, but I've had numerous problems. I had to add in (and I don't even know if it's right to do so) **iso-scan/filename=/Ubuntu1204/casper/filesystem.squashfs** because it wouldn't boot with ${iso_path}. What is that doing in there anyhow? How can it reference an ISO that doesn't exist?

Now it's refusing to finish booting as it says:

BusyBox v1.18.5 (Ubuntu 1:1.18.5-1ubuntu4) built-in shell (ash)
Enter 'hel' for a list of built-in commands.

(initramfs) unable to open '/dev/sdc'
/init: line 7: can't open /dev/sdd: no medium found
losetup: could not find any free loop device

Any instructions on how I can get this to boot? Thanks.

---

### Post by wilee-nilee on 2012-05-27
If you are not adverse to using a app there are a number of which will do this for you, many of which can do multiple boots, and persistence as well.

There are a a lot of web hits for using grub 2 to do this as well.

---

