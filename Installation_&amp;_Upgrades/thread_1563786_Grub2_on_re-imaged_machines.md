---
title: "Grub2 on re-imaged machines"
date: 2010-08-29
forum: Installation &amp; Upgrades
---

### Post by llarbkd on 2010-08-29
I just inherited a lab full of computers currently running XP and 9.10. They all worked when I last saw them. Recently, tech support re-imaged the XP partition and now I can't boot into Ubuntu. Obviously it overwrote the bootloader that was there, but I can't get it back.

The general setup is XP on /dev/sda1 and Ubuntu on /dev/sdb1 with swap on /dev/sdb5.

I've followed a bunch of instructions about reinstalling grub by chrooting into /dev/sdb1 (right? that's the one I should use), grub-install and update-grub all run without a hitch detect both Ubuntu kernels, memtest and the XP install as they were before the reimage. Exit and reboot, it still boots straight to Windows. If I move the boot flag from sda1 to sdb1, the computer hisses at me about not finding anything to boot.

I've gone nuclear on one computer and installed 10.04 on sdb1, but it still boots to Windows.

I feel like I need to do something to the MBR on the Windows drive but last time I did anything there I had to fix it with ms-sys.

Um, help, please. Of course if I left out anything wicked important, I'll get what info you need.

Oh and if upgrading to 10.04 in a trick fashion will help me, by all means suggest it, because once they get going I'm upgrading anyway.

---

### Post by gzarkadas on 2010-08-29
You must either switch the boot order of the disks from your BIOS, so that the disk in /dev/sdb boots first, or install grub at the MBR of the disk that is /dev/sda (and point it to load its files from /dev/sdb1). I recommend to first try the first option; it is easier.

---

### Post by llarbkd on 2010-08-29
Unfortunately the first option does not seem possible. They are Dell Optiplex 745, if anyone has that experience.

So how it the second option accomplished?

---

### Post by oldfred on 2010-08-29
Short version
[https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202]("https://help.ubuntu.com/community/Grub2#Reinstalling%20GRUB%202")
full chroot version:
[https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD](https://wiki.ubuntu.com/Grub2#Recover%20Grub%202%20via%20LiveCD)

Install MBR from LiveCD, Ubuntu install on sdb1 and want grub2 in drive sda's MBR:
Find linux partition, change sdb1 if not correct, and/or even sda if sdb wanted:
sudo fdisk -l
sudo mount /dev/sdb1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If that returns any errors run:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by gordintoronto on 2010-08-30
9.10 didn't use grub 2. Google "recoveringubuntuafterinstallingwindows" (that's all one
word), and the first result will point to the community documentation.

---

### Post by oldfred on 2010-08-30
It really depends on whether 9.10 is an upgrade from an older version - then it is grub legacy. If it is a new clean install it has grub2.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
[https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD](https://help.ubuntu.com/community/Grub2#Reinstalling%20from%20LiveCD)

---

