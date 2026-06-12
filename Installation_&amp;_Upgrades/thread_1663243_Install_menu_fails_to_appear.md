---
title: "Install menu fails to appear"
date: 2011-01-09
forum: Installation &amp; Upgrades
---

### Post by kaylatron on 2011-01-09
I'm trying to install ubuntu from a disc that I downloaded and burned. I'm currently using windows vista, which recently got a virus and had to be reinstalled, so I decided to try ubuntu instead. My problem is that when I reboot my computer with the disc in the drive, it appears to be starting to boot, but instead of a menu, a purple screen with a picture at the bottom appears. I'm not very good with computers, but a couple of years ago I tried booting an older version of ubuntu to test it, and that worked just fine. I'm not sure what the problem is and would appreciate some help.
Thank you.

Edit: I'm trying to install ubuntu 10.10, and I'm currently downloading ubuntu again to burn onto another CD, in case the CD is the problem.

---

### Post by kaylatron on 2011-01-09
I'm now having a slightly different problem: It gets past the loading screen, only to tell me that there's an error and it is unable to mount, or something along those lines.

Edit: "Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystems.squashfs"

---

### Post by dino99 on 2011-01-09
always burn with the slowest speed

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

### Post by kaylatron on 2011-01-09
So you think it's likely to be a problem with the CD because I didn't burn it slowly enough?

---

### Post by kansasnoob on 2011-01-09
Maybe this will help:

[https://help.ubuntu.com/community/BootFromCD](https://help.ubuntu.com/community/BootFromCD)

---

### Post by dino99 on 2011-01-09
> **kaylatron said:**
> So you think it's likely to be a problem with the CD because I didn't burn it slowly enough?

as i understand, its not a cd issue as you get "the purple screen with white dots" right ?

so try to boot without acpi:
 edit the boot line from grub menu (hold "shift" key down at end of bios process if you dont see the grub menu by default)

and choose the line ending with "quiet splash", remove these 2 params (quiet splash), and add: noacpi. If that fail again, instead of noacpi, try with nomodeset, then ctrl+x for booting

---

### Post by kaylatron on 2011-01-09
I've tried both of those with no luck, and the same error message as above:

"Can not mount /dev/loop0 (cdrom/casper/filesystem.squashfs) on //filesystems.squashfs"

---

### Post by dino99 on 2011-01-09
using squashfs is at your own risk

why not following the standard way ? (see post #3)

---

### Post by kaylatron on 2011-01-09
I'll have a go with parted magic, and get back to you on how it goes. Thanks for the help.

---

### Post by kaylatron on 2011-01-09
A couple of questions about partitioning. There are 3 partitions already there: System, Restore and Vista. I'm not sure quite what to do about those.
I'm also not entirely sure how to do anything other than make a partition in a particular format. Is there something extra I need to do to make it "bootable"?

---

