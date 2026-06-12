---
title: "Dual boot Ubuntu + Slackware"
date: 2005-04-14
forum: Installation &amp; Upgrades
---

### Post by robark on 2005-04-14
I have Slackware installed like this

/dev/hda1 mounted as /boot
/dev/hda2 as swap
/dev/hda3 as /

I installed Ubuntu 5.04 in expert mode to /dev/hda4 as /
and hda2 as swap

I did not install lilo or grub during the Ubuntu install.

Rebooted Slack and mounted /dev/hda4 as /mnt/ubuntu then edited
lilo.conf to include another stanza

image = /mnt/ubuntu/boot/vmlinuz-2.6.10-5-386
 root = /dev/hda4
 label = Ubuntu
 read-only

then #lilo

But when I reboot and choose Ubuntu I get the following kernel panic.

===
VFS: Cannot open root device "304" or unknown-block(3,4)
Please append a correct "ROOT= " boot option
Kernel panic -not syncing: vfs: unable to mount root fs on unknown-block(3,4)
===

I tried doing rdev /mnt/ubuntu/boot/vmlinuz-2.6.10-5-386 /dev/hda4
and then #lilo but it did not work.

I can still boot Slackware just fine.
Any help is much appreciated.

---

### Post by robark on 2005-04-14
I suspect it is because I chose reiserfs as the fs type. I'm assuming the Ubuntu kernel does not come with reiser support built in to the 2.6.10 kernel.

If this is the case, is there any way to build reiserfs support into kernel from the install cd shell or slackware?

I don't know how to use an initial ram disk to load the reiserfs module.

---

### Post by robark on 2005-04-14
Problem Solved:

I forgot to put the initial ram disk location in lilo. I was missing 

initrd = /mnt/ubuntu/boot/initrd.img-2.6.10-5-386

in the lilo Ubuntu stanza.

---

