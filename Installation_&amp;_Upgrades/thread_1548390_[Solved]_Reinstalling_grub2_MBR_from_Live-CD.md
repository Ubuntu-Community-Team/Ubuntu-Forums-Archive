---
title: "[Solved] Reinstalling grub2 MBR from Live-CD"
date: 2010-08-08
forum: Installation &amp; Upgrades
---

### Post by udippel on 2010-08-08
:DGot a nice little netbook, Samsung N150, alas with W7 taking all four primary partitions, removed the fourth without a hitch, made an extended one, and put UNR 10.04 into it after shrinking the 3rd.
Ask me if you need details.

After reboot, I get the Ubuntu menu entries in grub, as well as two W7 (Vista, héhé!) loaders. After some days, I made a mistake, and instead of the one with the real W7, I started the one with the W7 recovery. No way to stop it at loading, so I waited for the welcome screen, where I clicked "no, I don't want to recover W7". Nevermind. Windows is Windows and overwrote the MBR. So at reboot, just a blinking cursor. 

Question: How to write the MBR back? Without reinstalling?
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)
isn't a bad start, but my partitioning is more complex: 
sda5 is boot
sda6 is swap
sda7 is root
sda8 is home
I am not sure I can do what is written there, since the mount will not mount boot and root. And if I mount both, oh well, maybe it works? I am not confident.

So what I did, I booted to the UNR thumb drive (Live-CD), and opened a console.
$ cd /mnt
sudo mkdir oldroot
sudo mkdir oldboot
sudo mount /dev/sda7 oldroot
sudo mount /dev/sda5 oldboot
(ls -l oldroot and ls -l oldboot showed I mounted the right partitions)
sudo -o bind oldboot oldroot/boot
(ls -l oldroot/boot showed the correct vmlinuz, initrd, etc.)
sudo chroot oldroot
I might need these:
# mount proc
# mount dev
# grub-install /dev/sda
(no error shown)
# exit
$ exit
Shutdown and rebooted, and everything was working again.

I really, really, don't know why the UNR Live-CD doesn't contain a recovery for grub. I wonder, if it was written cleverly enough, to just put back the MBR if I selected the correct partitions during an install, without formatting them? I don't think so. 
Maybe I should file this as a RFE, that after partitioning, the user has a choice to just write back the MBR?

Thanks for a really great Lucid Lynx for netbooks (if you never tried, you wouldn't notice how much faster Ubuntu boots and reacts, compared to the included W7 home edition!)

Uwe

---

### Post by RamsesII on 2010-08-09
Hello udippel,

Thank you for sharing this in the forum. I was looking how to fix the same issue for someone I know. I'll give a try to your way and let you know.

RamsesII

---

### Post by EricBaenen on 2011-03-02
I have a similar problem.

Samsung N110 with 

recovery partition on sda1
WinXP on sda2
extended partition on sda3
Ubuntu 10.04 netbook remix on sda5 (ext4)
swap on sda6
/home on sda7 (ext4)

Somehow the mbr or grub has gotten corrupted (possibly a winxp update).

I've tried all the methods for redoing the mbr and grub2 but nothing has worked.  

When booting from a usb stick with the ubuntu netbook remix - the chroot process fails when trying to run chroot

"chroot: cannot run command 'bin/bash': No such file or directory"  

In searching the net it would seem the problem might be that the usb stick is formatted fat32 and not ext2, 3, or 4.  But I don't know how to make a usb stick bootable when formatted ext2, 3, or 4.

Any thoughts?

---

### Post by udippel on 2011-03-02
> **EricBaenen said:**
> I have a similar problem.

Samsung N110 with 

When booting from a usb stick with the ubuntu netbook remix - the chroot process fails when trying to run chroot

"chroot: cannot run command 'bin/bash': No such file or directory" 





Nothing to do with file systems. Your stick isn't okay. Try to recreate your USB-stick with the "Startup Disk Creator".

Good luck!

---

### Post by EricBaenen on 2011-03-02
Have recreated the usb stick with two different sticks, three different times - same result every time.

---

### Post by udippel on 2011-03-02
Never mind how often you did it. Something seems missing.
Take one of your sticks, open a terminal (console), and give us the output of items like:

which bash

ls -l /bin/b*

ls -l /

---

