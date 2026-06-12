---
title: "Black screen on installation"
date: 2008-10-14
forum: Installation &amp; Upgrades
---

### Post by BOMEz on 2008-10-14
I'm trying to get Ubuntu on an old laptop of mine, its 1.8GHz and has 512MB of Ram (32 set aside for video, so system only has 480). I get a screen with a bunch of text, and then the screen just goes black and doesn't respond.

Additionally if I restart the machine, it will just be another black screen...then I restart it again and I get my bios again.

Can someone offer suggestions on what to try to get ubuntu installed? (I'm using the latest release)

Here is the text I get from either choosing the option from running off CD, or installing right away:



> BusyBox v1.13(Debia 1:1.1.3-5ubuntu12) Built-in shell (ash)
Enter 'help' for a list of built-in commands

(initramfs) [ 184.386317] ata1.00: revalidation failed (errno=-5)
[ 219.499181] ata1.00: revalidation failed (errno=-5)
[ 226.296488] ata2.00 exception Emask 0x0 SAct 0x0 SErr 0x0 action 0x2 frozen
[ 226.296539] ata2.00: cmd a0/0:00:00:24:00/00:00:00:00/a0 tag 0 pio 36 in
[ 226.296585] ata2.00 status: {DRDY}
[ 256.716728] ata2.00: revalidation failed (errno=-5)
[ 302.141397] ata2.00: revalidation failed (errno=-5)
[ 347.566053] ata2.00: revalidation failed (errno=-5)

---

### Post by Partyboi2 on 2008-10-14
Try using some boot options. When you are at the main menu press F6 an add
```
noapic acpi=off
``` to the end of the line.
If this works you will need to make it permanent.

---

### Post by cariboo on 2008-10-14
Have a look at this link:

[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635/comments/18](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/206635/comments/18)

It gives instructions for a work around for your problem.

Jim

---

