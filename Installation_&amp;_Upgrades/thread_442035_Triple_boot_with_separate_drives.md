---
title: "Triple boot with separate drives"
date: 2007-05-13
forum: Installation &amp; Upgrades
---

### Post by Ixolite on 2007-05-13
I couldn't find any solution close enough to my situation...

OK, let's start from the beginning - I'm a linux noob so I was looking for some easy solutions for my problem. What I want is being able to triple boot Vista, XP and Ubuntu 7.04 from a single boot menu or if it is not possible, allow GRUB to boot Ubuntu and Vista bootloader in chain.

Problem is I have quite a mess here, so I'll have to describe it from the very begining.

First I had XP installed on a SATA drive and that was it. Then I decided to try out Vista - as I didn't want to screw my XP installation I got second SATA drive and installed Vista with XP drive plugged out. This way I had two windows installations on two separate drives and I was able to boot to each one by changing the drives boot order in BIOS.

When I decided that Vista isn't going to eat my brains out I thought it would be nice if I could have both systems booted from a single boot menu. I copied Vista bootmanager to XP drive and now boot both XP and Vista from Vista bootmanager but from XP drive (it's set as first in disk boot order in BIOS)

So I have both Vista and XP booted from XP drive via Vista bootmanager and it is working.

I had old IDE drive from my previous computer lying around so I decided I could use it for Linux. I plugged out both SATA drives, plugged IDE drive in and installed Ubuntu on it. 

So now I have three operating systems: Vista, XP and Ubuntu, each on it's own drive and I want to find a way to boot to Ubuntu without having to change disc boot order in BIOS.

I tried to add linux boot entry to Vista bootloader with EasyBCD1.6 but no luck there and I'm not familiar with GRUB enough to fiddle with it.

I am also not really sure how my drives are seen by bootloaders and operating systems.

IDE is on primary master, both SATA drives are SATA1 and SATA2 masters. When I ran Ubuntu Live CD drives were signed as: hdc, sda, sdb. EasyBCD, when trying to add linux boot entry, sees IDE drive as hd0 but messes with SATA drives - both of them have three partitions but EasyBCD sees 5 partitions on first SATA drive and two partitions on second SATA drive. The boot order set in BIOS is SATA1, SATA2 and IDE in last position. XP disk management describes drives as: IDE as hd0, SATA1 as hd1 and SATA2 as hd2.

So it's different in every tool I use and I got completly confused with that...

Oh, each drive was partitioned during installation of each OS by the installer integrated partitioners.

Any ideas?

---

### Post by Herman on 2007-05-13
>  I am also not really sure how my drives are seen by bootloaders and operating systems. Hello Ixolite,
Try booting up with  [Grub's Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") and use Grub to investigate your computer and take notes as to how Grub sees your hard disks and partitions. Then add operating system entries to the bottom of your Grub menu for booting Windows XP and Vista. If you have your Vista bootloader in Windows XP I think you just need to boot Windows XP then Vista should boot Via Windows XP.  You may need to use a pair of 'map' commands if XP is on a non-first hard disk. The way to use those are shown in that link.
I hope that will help.
Regards, Herman :)

---

### Post by Ixolite on 2007-05-13
Thanks but that is still a bit too complicated for me :(

I'll have to fiddle around with linux a bit, understand how things work a little better and I might try that then. Right now I'll just settle with booting via BIOS.

---

### Post by Herman on 2007-05-14
You want something easier eh? How about ****[GAG Boot Manager]("http://gag.sourceforge.net/") then. Why not give that a try, you can install it to floppy disk first untill you learn how to use it and see if you like it. You can make a CD out of it if you have no floppy drive, and I'm not sure about USB.   Then if you want you can install GAG to MBR when you are ready.
It's nice and simple to configure (had a graphical interface), and is free and only a small download. 
The only thing is, it boots OSes by chainloading their bootloaders via the bootsectors. That's fine for Windows, because it always installs the bootsector by default. For Linux you need to do that yourself. You can install either grub or Lilo to the first sector of your Ubuntu partition. 
There are how-tos in my sig links all about that, they are step by step and well explained. They should be easy to follow, they are even illustrated. Any problems let me know, I'll help you.

Regards, Herman :)

---

### Post by Ixolite on 2007-05-14
Oh, that looks interesting, thanks :)

---

### Post by confused57 on 2007-05-14
> **Ixolite said:**
> Thanks but that is still a bit too complicated for me :(

I'll have to fiddle around with linux a bit, understand how things work a little better and I might try that then. Right now I'll just settle with booting via BIOS.
Ixolite,  when you tried to add Linux to Vista's bootloader, did you happen to use the guide in this thread?:
[http://ubuntuforums.org/showpost.php?p=2644308&postcount=7](http://ubuntuforums.org/showpost.php?p=2644308&postcount=7)
if you didn't, it might help you if you decide to use Vista's bootloader to boot your Ubuntu drive.

By the way, you're in the best hands with Herman...see the first link in my signature for his website.

Herman, hope you don't mind me interjecting here..good to see you.

---

### Post by Computer Guru on 2007-05-14
Yeah, when Herman advises, everyone takes their notebooks out and starts scribbling furiously. :D

---

