---
title: "Uh-oh - GRUB didn't update, maybe?"
date: 2005-06-12
forum: Installation &amp; Upgrades
---

### Post by tmccartney on 2005-06-12
I've been using grub for a dual Warty/XP boot, with XP as the default OS.  I just updated from Warty to Hoary using the install CD from within Ubuntu (I used apt).  Was I supposed to do something in particular with grub before rebooting?  Here's why I ask:

When I start up, my grub boot menu looks like this:

Ubuntu, kernel 2.6.10-5-386
Ubuntu, kernel 2.6.10-5-386 (recovery mode)
Ubuntu, kernel 2.6.8.1-3-386
Ubuntu, kernel 2.6.8.1-3-386 (recovery mode)
Ubuntu, kernel memtest86+
Other operating systems:
Windows NT/2000/XP

I assume the top choice is my new Hoary installation, but no matter which ubuntu item I pick, I get the following message:

Root (HD0,1)
Filesystem type unknown, partition type 0x7
Kernal /boot/vmlinuz-2.6.10-5-386 root=/dev/hda 5 ro noscsi quiet splash

Error 17: Cannot mount selected partition

Press any key to continue

I have the live CD - can I use it to fix this?

Please type slowly - I'm a total newbie. :)


Thanks,

Tracey

---

### Post by alastair on 2005-06-12
You could boot into the LiveCD and look at the output of :

fdisk -l /dev/hda

for the partitions.

Your error message does show something odd though - perhaps a typo on your part :

```

Root (HD0,1)
Filesystem type unknown, partition type 0x7
Kernal /boot/vmlinuz-2.6.10-5-386 root=/dev/hda 5 ro noscsi quiet splash
```

"root=/dev/hda 5" should be "root=/dev/hda5"

That "Root (HD0,1)" is probably wrong (type 0x7 is an NTFS partition type).

(hd0,1) is hda2 - is this XP? It should be the Linux boot partition e.g. hda5 or (hd0,4) - MAYBE. I do not know know your partitioning.

You can "fix" this by editing the GRUB menu yourself at boot - and then making the change permanent by editing the /boot/grub/menu.lst file i.e.

ESC at boot
select kernel
"e" to edit
select line to edit "e" etc.
"b" to boot

---

### Post by tmccartney on 2005-06-12
That did it - thanks!



Tracey

---

