---
title: "Unknown filesystem on reboot, fresh install"
date: 2011-09-23
forum: Installation &amp; Upgrades
---

### Post by uppsju on 2011-09-23
Hi,

I'm having a problem with Ubuntu 11.04 on a 60GB SSD in my HP Mini 5101 netbook.

I created a USB disk installer using the instructions from the Ubuntu download page. During installation I selected "Erase disk and install Ubuntu", and it appears successful as when I reboot and remove the USB disk Ubuntu loads from my ssd.

However, there are two problems. First, shutting down doesn't seem to work. It goes as far as the Ubuntu logo animation and stays like that forever. Second, after shutting down the netbook with the power button I then cannot boot into Ubuntu. It stops at a screen that looks like:

```
error: unknown filesystem.
grub rescue>
```

Only two commands seem to work: set and ls.

ls reveals:
```
(hd0) (hd0,msdos5) (hd0,msdos1)
```

Running the setup from the USB disk and now selecting "Something else" reveals

```
sda1 (unknown) sda5(linux-swap)
```

"Device for boot loader installation" shows the name of my hard drive listed under /dev/sda

I am at a loss as how to proceed :confused:

---

### Post by zvacet on 2011-09-24
If sda1 is partition on witch you want to install Ubuntu then boot Ubuntu again and when you come to the partitioning stage select sda1 and let mountpoint be /root and format partition as ext4.

---

### Post by uppsju on 2011-09-24
Thanks for the reply.

It looks like the problem is with the SSD itself. It loses the partition info, and randomly won't let me format/create new partitions.

The drive will be RMA'd.

---

### Post by varunendra on 2011-09-25
> **zvacet said:**
> ..let mountpoint be /root and format partition as ext4.
I think you mean '**/**' (root) instead of '**/root**'?


> **uppsju said:**
> The drive will be RMA'd.
Do it as fast as you can ;). At least we'll have one less possibility if it happens again.

---

### Post by uppsju on 2011-10-03
Indeed it was a faulty drive. Performance is snappy as ever now, and my netbook may push it yet another year :)

---

