---
title: "boot loader getting clogged"
date: 2011-01-19
forum: Installation &amp; Upgrades
---

### Post by HappyLinux on 2011-01-19
[FONT="Arial"]OK, I don't know if this is something that happens by default, or there is a problem somewhere.

Here is the problem.

A couple of days ago, I set-up my new system with a dual-boot set-up; Win7 and Ubuntu 10.10 64bit.

Once I got everything up and running on both OS's (minus updates), everything was going smoothly. Well, most things were running smoothly on both OS's before and after updates.

Ubuntu happily installed a boot-loader which provided a slightly confusing list of options.

Here is the initial list and in this order;

[FONT="Times New Roman"]Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recover mode)
memory test (memtest86+)
memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)[/FONT]

Clicking on the sda2 option for Win7 happily boots into Win7. Clicking on the 2.6.35-22-generic option for Ubuntu loaded into Ubuntu without a hitch as well.

Now here is the fun part. Ubuntu did a big load of updates on the first day. One of them I think was a kernel update. Now there is an extra 2 options in the boot-manager.

The new list looks like this

[FONT="Times New Roman"]Ubuntu, with Linux 2.6.35-24-generic
Ubuntu, with Linux 2.6.35-24-generic (recover mode)
Ubuntu, with Linux 2.6.35-22-generic
Ubuntu, with Linux 2.6.35-22-generic (recover mode)
memory test (memtest86+)
memory test (memtest86+, serial console 115200)
Windows 7 (loader) (on /dev/sda1)
Windows 7 (loader) (on /dev/sda2)[/FONT]

Clicking on the new 24-generic options loads up fine. I don't know what would happen if I clicked on the old 22-generic option.

My questions are; what has happened? If there are any more updates like this will the boot-manager list keep expanding? Can older options be removed?[/FONT]

---

### Post by Rubi1200 on 2011-01-19
Whenever there is a kernel upgrade a new entry is added to the GRUB menu. This is quite normal.

It is also advisable to keep at least one spare entry for troubleshooting purposes in case an upgrade does not work and you need to boot an older kernel.

I believe the maximum number of entries that will be added is 7.

If you want to customize the GRUB screen and add/remove entries there are 2 options:

1. for command-line junkies:
[http://ubuntuforums.org/showthread.php?t=1287602](http://ubuntuforums.org/showthread.php?t=1287602)

2. a new GUI app for GRUB:
[http://ubuntuforums.org/showthread.php?p=10340183#post10340183](http://ubuntuforums.org/showthread.php?p=10340183#post10340183)

---

### Post by HappyLinux on 2011-01-19
Because I'm not versed in using Linux command line protocol yet, I'm trying to stick with GUI as best I can. I hope this program you mentioned works OK.

I can understand keeping options for older versions still there just in case. It's just that I don't want a huge lot. 7 is way too much for my tastes. I reckon 1 or 2 older versions that worked fine is more than enough.

---

### Post by HappyLinux on 2011-01-19
(deleted)

---

