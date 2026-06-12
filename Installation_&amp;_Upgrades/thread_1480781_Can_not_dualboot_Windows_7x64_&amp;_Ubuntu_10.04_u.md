---
title: "Can not dualboot Windows 7x64 &amp; Ubuntu 10.04 using Easy BCD"
date: 2010-05-11
forum: Installation &amp; Upgrades
---

### Post by anand00x on 2010-05-11
I have windows 7 x64 installed on my C partition and I have a separate partition that was unformatted. I installed Ubuntu 10.04 on this partition and put no bootloader on advanced options during installation. This is the third time I am installing Ubuntu. I keep having trouble with Grub it will work sometimes and then once in a while after my bios screen my computer will be stuck in an infinite loop it wont load into grub for me to choose my OS and I have to reinstall everything. Really gets annoying. So this time I just installed W7 x64 on my C drive and left my other partition unnamed without a drive letter. I installed Ubuntu 10.04 on the largest free space available without bootloader. I figured when I loaded into windows I could use Easy BCD to install a linux boot option into the Easy BCD menu. I did this and nothing works. I even tried this method from LIMNEOS: 

[I]Windows 7 after a clean install, it creates a small 200MB hidden partition to store the BCD store database. (similar files to boot.ini). This is where the bootloader is stored.
This partition is currently invisible to you, so even if you added a linux boot entry in EasyBCD, easybcd thinks that it has written the files to the partition where the bootloader is, but it actually can't write there cause it's hidden (no drive letter given). To fix that, open Disk Management, assign a drive letter to your hidden small partition (200MB of size must be), and then add a linux boot entry from EASYBCD again. This time it should work and you should be able to dual boot.[/I]

Still does not work. I can load into windows from the EASY BCD boot menu but I cant load into Ubuntu. It is installed but I can&#8217;t access it. Any tips?

[[IMG]http://img522.imageshack.us/img522/4844/photolua.jpg[/IMG]](http://img522.imageshack.us/i/photolua.jpg/)

---

### Post by lemming465 on 2010-05-14
EasyBDC can chain to an ubuntu boot loader such as LILO or GRUB, but the windows boot stuff doesn't know how to load Linux kernels, so you won't get anywhere.

On most of my systems I let Ubuntu control the MBR, and chain from the linux boot loader (grub, grub2) to the windows one.  If you prefer to have windows controlling the boot process, during an install when it gets to the bootloader stage click the "advanced ..." button and select the partition containing ubuntu as the bootloader location.  After the fact, you can boot a live CD, set up a chroot environment, and install the bootloader by hand.  Then go back to windows and easybcd.

The live CD -> chroot would look something like this (you may have to adjust the disk partition number to match your disk layout if your Linux partition isn't sda5):```

sudo -i
mount /dev/sda5 /mnt
cd /mnt
for f in proc sys dev; do mount -o bind /$f $f; done
chroot .
aptitude update
aptitude install grub-pc  # or "grub" if you dislike grub2
grub-install /dev/sda5 --force
update-grub
```

---

### Post by Mark Phelps on 2010-05-15
Most folks here (nearly everyone) use GRUB for booting, not EasyBCD.

You would do better posting your problem in the EasyBCD forums at NeoSmart Technologies.  They have forums and tutorials to help you solve your problems.

---

