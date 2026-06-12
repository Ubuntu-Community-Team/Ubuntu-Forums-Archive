---
title: "Triple boot &quot;how to&quot; needed: XP, 9.10 and Win7"
date: 2009-12-21
forum: Installation &amp; Upgrades
---

### Post by Udibuntu on 2009-12-21
Hi All,

I have XP and 9.10 on my Acer 751.

After much tweaking I have decent performance with XP and 9.10, but I think the AAO 751 will perform best on Win7 (mainly because of its GMA500 GPU).

I have found some tutorials on installing triple boot systems, but all entail installing the MS OS's first and only then Ubuntu - I wish to keep XP and Ubuntu as I had a pretty hard time tweaking them.

Is there an idiot proof way to add Win7 to my machine (assuming I have a bootable flash Win7)?

BTW, the 160G HDD gives XP 30G while 9.10 has a home partition of about 100G, formatted as ext4.

Thank you!

---

### Post by jerrrys on 2009-12-21
i don't do windows, but thought this may help

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+windows+7+to+ubuntu+boot&as_qdr=all&sa=Google+Search&lang=en#1061](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+windows+7+to+ubuntu+boot&as_qdr=all&sa=Google+Search&lang=en#1061)

---

### Post by Udibuntu on 2009-12-21
> **jerrrys said:**
> i don't do windows, but thought this may help

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+windows+7+to+ubuntu+boot&as_qdr=all&sa=Google+Search&lang=en#1061](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=add+windows+7+to+ubuntu+boot&as_qdr=all&sa=Google+Search&lang=en#1061)

Thanks Jerrrys, please let me rephrase my question - how do I add Windows 7 to a machine with Ubuntu and XP?

I know how to install the three from scratch, but I wandered on how to do it with XP preloaded and Ubuntu already installed.

Cheers

---

### Post by oldfred on 2009-12-21
It depends on whether you want one grub entry to boot to a windows menu  or two separate grub entries that boot directly to each windows install. If two drives I would also try to keep different boot loaders in each drive although you should use grub to boot.

To get each MS to have its own boot loader make a partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

Vista copies boot manager to one 
[http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing](http://members.iinet.net/~herman546/p15.html#BOOTMGR_is_missing)
Moral of the story - look on other NTFS partitions for the missing bootmgr and Boot directory.

---

### Post by Udibuntu on 2009-12-22
> It depends on whether you want one grub entry to boot to a windows menu  or two separate grub entries that boot directly to each windows install. If two drives I would also try to keep different boot loaders in each drive although you should use grub to boot.

Thanks oldfred.

What I hope for is a menu that let's me pick one of the three. If that is not possible than I will gladly live with a 2 step boot - one for Ubuntu/Windows choice and then XP/Win7 choice.

Again - If I can, I'd prefer to keep my current setup of XP and 9.10, and add to it Win7, all on a single physical HDD.

---

