---
title: "Gutsy Installation on SanDisk Cruiser Mini 1.0 GB"
date: 2007-11-24
forum: Installation &amp; Upgrades
---

### Post by rfrey74 on 2007-11-24
So. I thought I would install a "command line system" on to my flash drive.  Everything went well during the install.  When asked about where I wanted to install the GRUB loader, I chose /dev/sda.  My ancient computer still uses IDE, so the flash drive is the first sd device.  On boot up, I got the GRUB menu and chose to boot into the normal Gutsy image.  I got Error 17:  Could not mount file system.  So I changed the root (hd1, 0) to root (hd1, 1).  After the change, it seemed to boot just fine, sort of.  It ran through all the boot procedures, but after running local boot scripts, it did not give me a login prompt.  It seemed to just hang.

I went through the same procedure with the recovery image and it booted fine.  I got a command prompt after the boot sequence.  While I was there I did an apt-get update && apt-get dist-upgrade.  Once that finished, I rebooted into the normal image.  No change, it still hangs right before it should give me a login prompt.

Going through the same process with Memtest86+ works just fine, so I can boot in all images with the caveat that I do not get a login prompt after the boot sequence for the normal 7.10 image.

I would really like to log in to my new flash drive installation, so if anyone knows what the problem is, I will much appreciate the info.

Thanks.

---

### Post by rfrey74 on 2007-11-24
UPDATE:  Once the boot sequence stops at "running local boot scripts," I can type Ctrl+Alt+F1 and get a login prompt.  I am still interested in learning how to get the boot sequence to end in a login prompt.  If anyone has any ideas, feel free to reply to this post.

---

### Post by kelvin spratt on 2007-11-24
[http://www.pendrivelinux.com/](http://www.pendrivelinux.com/) might be of help

---

### Post by rfrey74 on 2007-11-24
That's a cool link.  It shows you how to put the live CD on a pen drive and allow you to save and reload your settings.  Not quite what I'm trying to do, but its still some really nice info.

Anyway, I fixed the problem I was having by removing "splash" from the kernel parameters in the GRUB loader.

Thanks for your help.

---

