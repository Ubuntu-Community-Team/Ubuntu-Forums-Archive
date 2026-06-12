---
title: "Unable to boot after motherboard replacement"
date: 2012-02-29
forum: Installation &amp; Upgrades
---

### Post by zepheir on 2012-02-29
Hello,

I recently swapped out the motherboard in one of my machines due to some hardware failure. The hardware and other parts of the machine have remained the same.

Currently, when I try to boot up, the machine fails with a message that it waited too long for the root device, which is set to /dev/mapper/leah-root in grub. At the command prompt, I've checked /dev and there is only /dev/mapper/nvidia-bhiagfdh which is a symlink to /dev/dm-0.

Previously, I was using LVM and a little bit of Internet research seems to show that it should be a /dev/dm-0 device. I tried editing grub to point to that device but it fails with an 'invalid arguments' message.

I found a thread that discussed loading a Live CD and running some commands to mount the LVM, but running vgscan on my machine only returns 'No volume groups found.'

Does anyone have any advice on trying to restore the system?

Thank you

---

### Post by zepheir on 2012-03-01
I seem to have solved my own problem. Changing the SATA port, which the drive was connected to, from 1 to 3 resolved the issue.

---

