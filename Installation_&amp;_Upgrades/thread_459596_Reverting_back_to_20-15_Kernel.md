---
title: "Reverting back to 20-15 Kernel"
date: 2007-05-30
forum: Installation &amp; Upgrades
---

### Post by TheDoulos on 2007-05-30
No doubt you're aware of the difficulties folks are having with the 20-16 kernel.  I too had just a little bit of difficulty mostly related to the switch from /dev/sd* to /dev/hd*.  At any rate, I think I've reverted back to the 20-15 kernel, but I'd like to query the experts to be sure.

I use a grub boot floppy to bring up my system, and I have several distros on different partitions, so I can usually boot to something even if things get messed up somewhere.  When my Feisty 20-16 kernel upgrade wouldn't boot, I booted up an Edgy distro and edited the menu.lst file on my grub floppy and added a stanza that referenced the 20-15 kernel files in the /boot directory as opposed to the symbolic links in the root directory:
```
kernel /boot/vmlinuz-2.6.20-15-generic root=/dev/sdb5 ro
initrd /boot/initrd.img-2.6.20-15-generic
```Is this all that's required to essentially go back to the 20-15 kernel, or do I need to roll back the package manager upgrades such as the linux headers and restricted modules?

---

### Post by ccfiel on 2007-05-30
What i did to revert back to 20-15. i just press escape 'ESC' key when grub start. and it allows me to select 20-15 and 20-16 kernel so i just select the 20-15. no need to recovery disk. then i just remove the entry of 20-16 in my grub. so im now back with my 20-15 kernel. :) hope this helps.

---

### Post by TheDoulos on 2007-05-31
Thanks for the reply.  That's essentially what I've done in that my grub stanza specifically references the 20-15 kernel files.

What I'm still curious about is if there are any residual files from the "upgrade" that need to be rolled back, or is simply booting with the 20-15 kernel files sufficient?

Also, I know that some folks have needed to do such things as:

a) edit initramfs-tools/conf.d/resume
b) edit uswsusp.conf
c) sudo update-initramfs -u
d) sudo dpkg-reconfigure uswsusp

but I don't think I need to do any of these things because:

a) my initramfs-tools/conf.d/resume file points to my swap partition by it's /dev/sd identifier, and 20-15 recognizes my pata drives as /dev/sd
b) I don't have uswsusp installed
c) I don't see anything that would warrant a change to my initramfs
d) Again, I don't have uswsusp

---

### Post by DizzyTech on 2007-05-31
What about me?  I use vmware-server and its kernel modules.  I broke the package by forcing it to the .20-15 version.

---

