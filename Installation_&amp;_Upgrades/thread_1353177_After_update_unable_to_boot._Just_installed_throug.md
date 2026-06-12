---
title: "After update unable to boot. Just installed through wubi."
date: 2009-12-12
forum: Installation &amp; Upgrades
---

### Post by tech newbie on 2009-12-12
Total tech newbie here,
I installed ubuntu via wubi everything went fine until i updated using update manager (the first time i booted after install), when i was asked to restart ubuntu would not boot when chosen, All i get is a black screen with some text and i can type below. Reminds me of command prompt. The word grub comes up a few times.

---

### Post by tech newbie on 2009-12-12
> **tech newbie said:**
> Total tech newbie here,
I installed ubuntu via wubi everything went fine until i updated using update manager (the first time i booted after install), when i was asked to restart ubuntu would not boot when chosen, All i get is a black screen with some text and i can type below. Reminds me of command prompt. The word grub comes up a few times.

At the top of the black screen it says GNU GRUB version 1.97~beta4

---

### Post by darkod on 2009-12-12
Depending on which partition you installed wubi, you need to execute the following commands at the prompt, one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

You might need to replace /dev/sda1 depending where you installed wubi. sda is first hdd, sdb second hdd, etc, and the number is the number of the partition on the drive.
Usually C: would be /dev/sda1 (or /dev/sda2 if there is another "hidden" partition before it), D; would be /dev/sda2 (/dev/sda3), etc.

Once you get it right and you boot up wubi, open terminal (in Applications-Accessories) and execute:
sudo update-grub2

---

### Post by tehno 2 on 2010-03-14
> **darkod said:**
> Depending on which partition you installed wubi, you need to execute the following commands at the prompt, one by one:

sh:grub>set root=(loop0)
sh:grub>linux /boot/vmlinuz-2.6.31-14-generic root=/dev/sda1 loop=/ubuntu/disks/root.disk ro
sh:grub>initrd /boot/initrd.img-2.6.31-14-generic
sh:grub>boot

You might need to replace /dev/sda1 depending where you installed wubi. sda is first hdd, sdb second hdd, etc, and the number is the number of the partition on the drive.
Usually C: would be /dev/sda1 (or /dev/sda2 if there is another "hidden" partition before it), D; would be /dev/sda2 (/dev/sda3), etc.

Once you get it right and you boot up wubi, open terminal (in Applications-Accessories) and execute:
sudo update-grub2


Darkod,

great solution it worked for me and I got Ubuntu to boot. after the last command, I restarted my computer but booted back to the dark screen.
Would you kindly tell me how can I stop this from happening again.

Thanks in advance

---

