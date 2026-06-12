---
title: "Kernel panic error"
date: 2005-04-18
forum: Installation &amp; Upgrades
---

### Post by Seiken on 2005-04-18
Background: I have a spare PC at work that I use to learn more about Linux. It has a 20 GB hard drive. 3 GB FAT32 partition for XP (hda1), 3 GB FAT32 for storage (hda2), 256 MB Linux swap (hda6) 4 GB ReiserFS for Slackware 10.1 (hda7), 4 GB ReiserFS for Ubuntu 5.04 (hda8), 4 GB ReiserFS for Gentoo 2005.0 (hda9), and 1.6 GB unused.

I installed XP first, then Slack, and they both worked. Then I installed Ubuntu, and everything (XP, Slack, Ubuntu) still worked. Then I installed Gentoo and started out by only writing Gentoo to Lilo (I don't use Grub). Gentoo booted, and I was able to add Slack to my /etc/lilo.conf, and then booted into Slack. From Slack, I edited my /etc/lilo.conf as follows (I left out comments to save space):
```
boot = /dev/hda
message = /boot/boot_message.txt
prompt
timeout = 100
change-rules
  reset
vga = normal

image = /boot/vmlinuz
  root = /dev/hda7
  label = Slackware
  read-only

image = /mnt/ubuntu/vmlinuz
  root = /dev/hda8
  label = Ubuntu
  read-only

image = /mnt/gentoo/boot/vmlinuz
  root = /dev/hda9
  label = Gentoo
  read-only

other = /dev/hda1
  label = Windows
  table = /dev/hda
```

After running /sbin/lilo, I got no errors or warnings. I then rebooted and tested it all. Everything boots except for Ubuntu. (ie: XP, Slack, and Gentoo all boot). When I try to boot Ubuntu, I get the following during startup:
```
VFS: Cannot open root device "308" or unknown-block(3,8)
Please append a correct "root=" boot option
Kernel panic - not syncing: VFS: Unable to mount root fs on unknown-block(3,8)
```
The folks on LinuxQuestions.org said that maybe Ubuntu needs something additional setup in Lilo... so that's why I'm here :) To ask you guys if Ubuntu requires anything further than what I have above when in this configuration.

Thanks,
Seiken

EDIT: That :cool: at the end of the VFS line (in the 2nd code block) is supposed to be an "8" and a ")"... so the end of the line should read "unknown-block ( 3 , 8 )" (without the spaces).

---

### Post by Seiken on 2005-04-19
Can anyone help me with this? If not, where else should I ask for help?

---

### Post by speedman on 2005-04-19
Ubuntu uses an initrd image for the kernel.  Try this:

image = /mnt/ubuntu/vmlinuz
  root = /dev/hda8
  initrd=/initrd.img
  label = Ubuntu
  read-only

If lilo doesn't want to follow the symlink /initrd.img substitute the full path instead:

  initrd=/boot/initrd.img-2.6.10-5-686 (or whatever your kernel version is)

ls -al /initrd.img will show you precisely what initrd image it is pointing at in /boot.


Regards,

SM

---

### Post by Seiken on 2005-04-21
Thanks! I'll try that at work tonight if I get a chance.

---

