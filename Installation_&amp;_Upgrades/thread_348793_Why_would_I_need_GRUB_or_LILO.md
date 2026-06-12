---
title: "Why would I need GRUB or LILO?"
date: 2007-01-29
forum: Installation &amp; Upgrades
---

### Post by ashwin_murali on 2007-01-29
Hi all,

I'm trying to install Ubuntu 6.06 LTS on my USB HDD.  I'm not a heavy Linux User.... just the basics... and have been working on it for the last couple of months.   I'm using an Asus A8Jc for this.

My external HDD is: Seagate 40GB.  I want to know if it's mandatory to install GRUB on the USB HDD during installation of Ubuntu...  From my understanding of GRUB, it's a boot-loader...   which means that it'll pop up a menu that shows which OS i want to boot into...

Now, I want to boot into windows normally, so I dont pop in a CD or plug in the USB drive... And it must boot into windows coz, it cant find a HDD or a CD.

If i want to boot into linux, I just plug in the USB HDD during boot and then,, it boots into Ubuntu...

Is my understanding of this issue right???  Kindly clarify me on this...

Thanx...

---

### Post by Pobega on 2007-01-29
From my understanding GRUB is mainly used for drives dual booting between Linux and Windows. It has other uses, of course, which I don't know about because I've never toyed around with GRUB before.

---

### Post by Aurdal on 2007-01-29
If you don't install a boot loader you won't be able to boot linux at all, (as far as I know) so it'd probably not be a bad idea to install grub or lilo on your USB disk.

---

### Post by ashwin_murali on 2007-01-29
I understand that friend... But, is the GRUB that I install on the USB disk gonna tamper with the MBR on my internal drive??? Can I boot windows if i dont plug in the USB drive during boot???  This is a serious issue!!!

---

### Post by jgcamp99 on 2007-01-29
And if Linux ever goes awry, it's so much easier on you to get to recovery mode from the boot loader without having to research how to on-line.

---

### Post by ashwin_murali on 2007-01-30
I understand your replies, but I kinda still havent got the idea right...  My questions are:

1.  Can I have ubuntu boot if i plug in the USB and windows boot if i dont plug in the USB.  The plugging in of the USB is when i switch on my laptop.
2.  If I need to install GRUB, I would definitely install it only on the USB disk.  Now, will this grub installation affect the MBR on my internal hard drive in any manner???

Kindly help me out...

---

### Post by louieb on 2007-01-30
In order to boot most if not all Linux distributions GRUB or LILO is necessary. Or you could try a boot loader called GAG. This is true even if you just have one Linux distribution on the PC. (no windows, no BSD, not even a second Linux distribution). You still need a boot loader.  

Yes you can install it in the USB drives MBR or the boot sector of the Linux partition.
After that you can change your BIOS  to boot to USB or modify the window boot loader to load GRUB from the USB drive.

Werther or not you can  choose which operating system to boot to depending on if the USB drive is plug in depends: Does the BIOS support booting to a USB drive?
 
If your BIOS supports booting  a USB drive. Then make the USB drive the first boot device. and install GRUB in the MBR of the USB drive. Then you should be able to boot Linux or Windows depending on if the USB drive is plugged in or not at boot time. And this will leave the internal drive untouched.

If your BIOS can not boot the USB drive then  you have some research to do on how to make a floppy or CD with a boot loader that can boot a USB drive.

Check out the Dual Boot link in my signature. Herman has put together a very nice site devoted to dual booting Ubuntu and windows.    Also check out the GAG section of this forum.

---

