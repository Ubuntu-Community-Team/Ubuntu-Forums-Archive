---
title: "Cannot Boot Into Ubuntu..."
date: 2008-01-10
forum: Installation &amp; Upgrades
---

### Post by 4real*leb on 2008-01-10
Hello, I have Windows Vista, Windows XP, and Ubuntu in a triple bot environment.
Vista and XP are installed on the same harddrive, except different partitions. Ubuntu, however, is installed on a separate drive. The drive Ubuntu is installed to is connected to my computer through[ this]("http://www.ncix.com/products/index.php?sku=20136&vpn=NG-SATAIDE-PCI&manufacture=nGear%20Technologies%20Inc."). Now the problem is that I can boot into XP and Vista now problem, but if I try to boot into Ubuntu I am presented with a Disk Read Error, I am guessing this is because the drive is not being read. Is there any way to fix this?

---

### Post by icheyne on 2008-01-10
If you boot into Windows, can you see the other drive?
Did the drive suddently stop working?

---

### Post by 4real*leb on 2008-01-10
Thank you for the reply.

When I boot into Windows I can see the drive everywhere (Device Manager, RAID tool etc.) except for My Computer.

The drive did not stop working as far as I know, when using EasyBCD it picks up the drive just fine.

---

### Post by 4real*leb on 2008-01-10
Ok, the main cause is 100% the fact that my hard drive is attached to that SATA card. I booted into Super Grub and it couldn't detect my drive. The hard drive is in a fine condition as I was able to install Ubuntu to the drive, I just need to get it read...

---

### Post by manimal347 on 2008-01-10
You might want to post your grub file, as the problem most-likely lies there.

You can probably get to it by using an Ubuntu CD (all flavors, live or non-live) in recovery mode. It should mount your Linux partition (if not, we can tell you how).

I searched my Gutsy Gibbon setup:
#this searches the whole computer for files named "menu.lst")

(anon@ubuntu):/usr/share/doc/eterm$ sudo find / -name menu.lst 
/usr/share/doc/grub/examples/menu.lst
/boot/grub/menu.lst

The first file has documentation on how to use grub, and the second file is your actual configuration file that sets up how the operating systems share your hard disks. These search results were consistent with what Googling told me, and /boot/grub/menu.lst is the general place for a Linux distro to put that file. Your mileage may vary so if you cannot find it, run a similiar search on your computer. The file can be opened with nano, a CLI text editor. You won't be able to print, so write things down or take a picture.

Also, be sure to read "man grub" (manual page on Grub), and [http://wiki.archlinux.org/index.php/Grub_configure_examples](http://wiki.archlinux.org/index.php/Grub_configure_examples) ,
[http://ubuntuforums.org/archive/index.php/t-61720.html](http://ubuntuforums.org/archive/index.php/t-61720.html)

In addition, try running "grub-install:",  "man grub-install" and the above pages, plus Google, for more info on this.

CAUTION:
Please back up grub.lst before editing it.
"sudo cp /boot/grub/menu.lst /boot/grub/menu.bak" 
You can restore with "sudo cp /boot/grub/menu.bak /boot/grub/menu.lst"

-------------------------------
I'm assuming you didn't use LILO, as few do (it's basically obsolete), and I'm not sure if Ubuntu even offers it outside of an expert install with the CLI install CD. If you did do an expert install, that opens a BILLION cans of worms as to why it won't boot, such as writing Grub to the wrong partition or not loading essential device drivers.

---

### Post by 4real*leb on 2008-01-11
I decided to do a test, I hooked up my drive to the main IDE channel as hd(0,0) (and in turn disconnected all drives except the cd). When I initially tried GRUB tried to boot from hd(1,0). I had to hit e to edit and change the boot device to hd(0,0). Once I did this it booted fine, so is it just a matter of the sata card not being detected?
I will try doing the same test tomorrow with the same harddrive connected to the sata card, any suggestions until then are welcome.

---

