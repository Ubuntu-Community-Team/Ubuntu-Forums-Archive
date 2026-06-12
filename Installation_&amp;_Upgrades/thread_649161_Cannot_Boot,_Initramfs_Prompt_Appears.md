---
title: "Cannot Boot, Initramfs Prompt Appears"
date: 2007-12-24
forum: Installation &amp; Upgrades
---

### Post by robson9776 on 2007-12-24
Dear Friends,

I just bought a new laptop Acer Aspire 4520 (Turion 64 X2 1.9 Ghz, Nvidia GeForce 7000M, HDD 80 Gb) and I have Windows XP installed on /dev/sda1 and /dev/sda2.

After that I want to install Ubuntu Gusty 32bit and after the installation was completed the boot process was stuck and after waiting few minutes it gives me initramfs prompt. what the hell?

I tried to solve this problem using this method, but still failed :

#using live CD
#sudo mkdir /mnt/tmp
#sudo mount -t ext3 /dev/sda6 /mnt/tmp
#sudo chroot /mnt/tmp
#sudo update-initramfs -u -k 2.6.22-14-generic

I also tried to change BIOS setting of my harddisk into IDE mode and AHCI mode, also still failed...

friends, could you please kindly help me to solved this problem.... :(

---

### Post by Pumalite on 2007-12-24
What is the exact error message?

---

### Post by robson9776 on 2007-12-24
Hi,

I'm a linux newbie, could you tell me how to get the error message? because I didn't see any error message after usplash, except that initramfs prompt...

---

### Post by Pumalite on 2007-12-24
Do you have this:

/bin/sh:can't access tty;job control turned off
initramfs

---

### Post by robson9776 on 2007-12-24
Hi,

no, I don't have that error message. here's what I have :

BusyBox v.1.1.3 (Debian 1:1.1.3-5 ubuntu7) Build-in shell (ash)
Enter 'help' for a list of build-in commands
(initramfs)_

any idea what's going on?

---

### Post by robson9776 on 2007-12-24
Here's the error message when I enter using 'Recovery Mode' :

check root = bootarg cat /proc/cmdline
or missing modules, devices : cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/xxxx-xxx... does not exist.
Dropping in to a shell!

Is this because Ubuntu cannot read my SATA harddisk?

---

### Post by amitabhishek on 2007-12-25
same here. Post me if you have a solution:

[http://ubuntuforums.org/showthread.php?t=649135](http://ubuntuforums.org/showthread.php?t=649135)

---

### Post by robson9776 on 2007-12-25
Hi amitabhishek,

I've tried that solution before... but still failure.

Oh God... is there anyone out there has succeed solve this problem?

---

### Post by Pumalite on 2007-12-25
It's for the 5100, but it might help:
[http://ubuntuforums.org/showthread.php?t=595979](http://ubuntuforums.org/showthread.php?t=595979)

---

### Post by robson9776 on 2007-12-25
I've change the usplash resolution into 1280x800 and did exactly as mentioned. but keep failed...

I think the problem still the same, Ubuntu cannot recognized my root partition (see my error message), but I don't have any clue to solve it... :(

---

### Post by terminal on 2007-12-25
Do you know the partition number ? In grub try editing root=UUID=.................................... line with 
root=/dev/sda1

also try /dev/sda2,3,4,5,6,7, if u dont know ext3 partition number


Also when u drop in busybox type cat /proc/partitions to know partition numbers .

---

### Post by MeanStreak on 2007-12-25
Having exactly the same problem here - trying to install Ubuntu on a PIII laptop with an existing XP install. My plan is to overwrite XP totally with Ubuntu. Can anyone first explain what initramsfs is and what is its purpose? What commands can we enter to get through the busybox prompts to get into the live desktop?

---

### Post by Pumalite on 2007-12-25
256 MB of RAM or less>Xubuntu Alternate CD:
[http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/](http://cdimages.ubuntu.com/xubuntu/releases/feisty/release/)
[http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/](http://cdimage.ubuntu.com/xubuntu/releases/7.10/release/)
(Xubuntu Gutsy uses more memory)

---

### Post by robson9776 on 2007-12-26
> **terminal said:**
> Do you know the partition number ? In grub try editing root=UUID=.................................... line with 
root=/dev/sda1

also try /dev/sda2,3,4,5,6,7, if u dont know ext3 partition number


Also when u drop in busybox type cat /proc/partitions to know partition numbers .

Yes, I know my partition number. It's /dev/sda6.

It gives me same result after I tried to edit grub (as you said) and also I've tried to edit /etc/fstab.

Still.... Zero Result.... :(

---

### Post by Pumalite on 2007-12-26
[http://www.google.com/search?hl=en&q=ubuntu+and+Acer+Aspire+4520&btnG=Google+Search](http://www.google.com/search?hl=en&q=ubuntu+and+Acer+Aspire+4520&btnG=Google+Search)

---

### Post by ups on 2007-12-28
**This post could be related to an Ubuntu bug filed at**: [https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256](https://bugs.launchpad.net/ubuntu/+source/initramfs-tools/+bug/67256) [br].[/br] ---------------------------- [br].[/br] [br].[/br]
				This is bug 67256. I am, however, able to boot into the system most of the time - for me it happens only once in a while. It could be related to some initramfs commands i had tried earlier, I'll try finding them out and post them here later.

Meanwhile, I'd suggest you keep doing ctrl-alt-del when you see it is stuck at the splash screen and see if it allows you to boot sometimes.

---

