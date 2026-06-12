---
title: "Installing from USB: &quot;Can not mount /dev/loop0...&quot;"
date: 2011-01-18
forum: Installation &amp; Upgrades
---

### Post by maggirl93 on 2011-01-18
Hi, so, I had UNR on my netbook, and it stopped working, and I'm just getting around to trying to re-install it. I went through all the steps of putting it on the USB flash drive. I plugged it into my computer and turned it on and got the following message:

BusyBox v1.15.3 (Ubuntu 1:1.15.3-1ubuntu5) built-in shell (ash)
Enter 'help' for a list of built-in commands.

(initramfs) mount: mounting /dev/loop/0 on //filesystem.suqashfs failed: Invalid argument
Can not mount /dev/loop0 (/dcrom/casper/filesystem/squashfs) on //filesystem.squashfs

How do I fix this?!

---

### Post by mlduncan96 on 2011-01-18
I am having a similar problem. I have a netbook with Ubututu Netbook 10.10 on for a few months. Recently, it has been acting up a bit, but this morning no boot with a message: **Target Filesystem doesn't have /sbin/init **. I found this error reference [here]("http://wwww.ubuntuforums.org/showthread.php?t=1167710&page=2"). but my attempts to use the CD I used for installation is hanging as it starts with squashfs errors about I/O buffer and a couple other errors. I looked them up and typed them out once and my post failed so I'm not going through it all again. I have done a memory test and HD test and both test okay. I'm at a loss and stuck. I have a USB stick at home with desktop 9.04 (I think) I may try when I get back home.

---

### Post by mlduncan96 on 2011-01-18
I tried the advice in the link with my USB stick at home that had 10.04 on it. At first I got the same message as the guy who thought his HD was dead. I opened the HD in the folders and it listed it as healthy. I tried the command a second time and it worked. Fixed several errors and after a reboot, it is working perfectly. Good luck.

---

### Post by jdieter on 2011-01-19
Tore my hair out on this one. My fix was to use the alternate install CD. Worked like a champ.

---

