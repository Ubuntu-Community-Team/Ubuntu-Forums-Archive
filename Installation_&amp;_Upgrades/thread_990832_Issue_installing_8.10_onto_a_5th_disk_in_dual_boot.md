---
title: "Issue installing 8.10 onto a 5th disk in dual boot"
date: 2008-11-23
forum: Installation &amp; Upgrades
---

### Post by Box293 on 2008-11-23
I already have 4 x HDD in my system. 2 x 150Gb in RAID1 and 2 x 300GB in RAID1. This is just the standard Intel ICH9R raid i've enabled in my bios. In the bios I sepecified raid - 4 ports, the remaining 2 ports have a DVD and a 160GB sata HDD.

I've tried installing Ubuntu 8.10 several times onto the 160GB HDD, completes OK but on reboot I only get Vista. I've tried EasyBCD in Vista but I just end up with grub at a console looking screen.

I've tried following the steps on how to setup fake raid [https://help.ubuntu.com/community/FakeRaidHowto]("https://help.ubuntu.com/community/FakeRaidHowto")

If I do the Alternate install (method 1) it asks me to search for SATA disks and if I say yes the next screen shows 2 x blank lines, a line saying write changes and continue. I do not see any HDD. If I try write and continue it tells me I need to setup partitions first!

If I do the alternate install and say no to scanning for sata then it does show all 5 HDDs and I can install to it HDD5 OK and then reboot but all I get is Vista.

If I try and install doing using the desktop CD all goes well, completes OK but I never can boot to it.

If I try the fakeraid method 2, I get to step 10 where it scans for paritions and I get the following error: 
Partman failed with exit code 10. Further information may be found in /var/log/syslog. Do you want to try running this step again before continuing? If you do not, your installation may fail entirely or may be broken.


EasyBCD. I've tried this a few times and from what people say I need to boot into ubuntu and get a copy of menu.lst first and then add it to the menu.lst on my C:\ vista drive. When I boot the Ubuntu desktop CD and browse the 160GB HDD which has the Ubuntu install there is no grub directory under boot, this is where I am getting stuck.



What do I want to achieve? I want to have Ubuntu installed on the 5th disk, have Ubuntu recognise the existing 2 x RAID1 sets (so I can look at stuff etc). I want to dual boot to Vista.

Just to make it clear, I want to install it on the 5th disk and use Vista as the boot menu selector. I don't want to install on one of the raid sets.

Also FYI I'm a noob to linux, Windows is not a problem. I have touched on linux cause I use ESX at work but thats about it.



Here is some fdisk -l information, I've read that this can help.

Disk /dev/sda: 150.0 GB, 150039945216 bytes
199 heads, 6 sectors/track, 245432 cylinders
Units = cylinders of 1194 * 512 = 611328 bytes
Disk identifier: 0x12e412e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           2      245426   146518016    7  HPFS/NTFS

Disk /dev/sdb: 150.0 GB, 150039945216 bytes
199 heads, 6 sectors/track, 245432 cylinders
Units = cylinders of 1194 * 512 = 611328 bytes
Disk identifier: 0x12e412e3

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *           2      245426   146518016    7  HPFS/NTFS

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c1b222e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sdd: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x3c1b222e

   Device Boot      Start         End      Blocks   Id  System
/dev/sdd1   *           1       38913   312568641    7  HPFS/NTFS

Disk /dev/sde: 160.0 GB, 160000000000 bytes
255 heads, 63 sectors/track, 19452 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x00000001

   Device Boot      Start         End      Blocks   Id  System
/dev/sde1               1       18657   149862321   83  Linux
/dev/sde2           18658       19452     6385837+   5  Extended
/dev/sde5           18658       19452     6385806   82  Linux swap / Solaris

---

### Post by razy60 on 2008-11-23
when you reboot your system do you get the option to go into system setup or system menu to choose your startup disc i.e ide hard drive or cd drive or similar, if you do, can you then choose your drive to boot from.
 is the drive you wish to boot 8.10 from on the first hdd ribbon or secondary.
If its on the secondary have you tried it on the first.

Raz

---

### Post by caljohnsmith on 2008-11-23
If you want to use Vista as the boot menu on start up, then I would recommend that you install Grub to the boot sector of you sde1 partition so you can try and use EasyBCD to simply add that sde1 boot sector to the Vista boot menu via the following instructions:

[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

That method is unfortunately not foolproof though, depending on how you have your drives ordered in the BIOS boot order. To install Grub to the boot sector of sde1, from a terminal in your Live CD (Applications > Accessories > Terminal), you would do:
```
sudo grub
grub> root (hd4,0)
grub> setup (hd4,0)
grub> quit
```
If that method doesn't work, you can add Ubuntu to Vista's boot loader using NeoGrub (which is part of EasyBCD):

[http://neosmart.net/wiki/display/EBCD/NeoGrub](http://neosmart.net/wiki/display/EBCD/NeoGrub)

And that should work since you can specify which boot drive/partition (hdX,Y) to look on for Ubuntu. If you need some help with either option, let me know, otherwise let me know how it goes. :)

---

### Post by Box293 on 2008-11-23
Thanks for the tips caljohnsmith.

I was trying those links yesterday on EBCD but the website was down each time I tried.

I'm pretty sure the steps you provided on setting up grub are the key to my whole problem.

I assume in your example you've used (hd4,0) as 4 is the "5th" disk?

And thanks razy60 for your input. I've tried all sorts of options in the BIOS for boot order and also selecting that drive to boot to, but at the end of the day from what *think* I can see, grub is not installed on my linux disk, once I do this it should be OK.

Cheers Troy

---

### Post by caljohnsmith on 2008-11-23
> **Box293 said:**
> Thanks for the tips caljohnsmith.

I was trying those links yesterday on EBCD but the website was down each time I tried.

I'm pretty sure the steps you provided on setting up grub are the key to my whole problem.

I assume in your example you've used (hd4,0) as 4 is the "5th" disk?

And thanks razy60 for your input. I've tried all sorts of options in the BIOS for boot order and also selecting that drive to boot to, but at the end of the day from what *think* I can see, grub is not installed on my linux disk, once I do this it should be OK.

Cheers Troy
Yes, (hd4,0) is the 5th disk, or sde, since Grub's numbering begins with zero. Also, if you want to try and boot your Linux drive, part of your problem might be that none of the partitions on the Linux sde drive have the boot flag set; some BIOSes will refuse to boot a drive that doesn't have a partition with the boot flag set, because the BIOS assumes the drive is then a data drive. Also, if you want to install Grub to the MBR (Master Boot Record) of the linux sde drive so you can boot directly from it, just do these steps:
```
sudo grub
grub> root (hd4,0)
grub> setup (hd4)
grub> makeactive
grub> quit
```
Note that the "setup (hd4)" installs Grub to the MBR of the drive, whereas "setup (hd4,0)" installs Grub to the boot sector of the sde1 partition. And the "makeactive" command will set the boot flag on the sde1 partition. If you do all the above and set your BIOS to boot the sde drive, you should at least get a Grub menu on start up. I would recommend doing it that way, and then you can add Vista to your Grub menu and boot all your OSes from Grub. It's up to you though how you want to do it. :)

---

### Post by Box293 on 2008-11-24
caljohnsmith,
I followed the steps in your last post and all went OK. It said that the files already existed so I think the major step was the makeactive one I think.

Anyway on next reboot I chose from my Bios boot menu disk 5 and it all booted up ok, I'm writing this post from ubuntu as we speak ;o)

Thanks very much for your help, much appreciated.

Troy

---

### Post by caljohnsmith on 2008-11-24
That's great news, glad to hear it worked OK. If you need a hand adding Vista to your Grub menu, let me know, otherwise cheers and have fun with your OSes. :)

---

