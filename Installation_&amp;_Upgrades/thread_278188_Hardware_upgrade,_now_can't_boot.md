---
title: "Hardware upgrade, now can't boot"
date: 2006-10-15
forum: Installation &amp; Upgrades
---

### Post by cnc333 on 2006-10-15
I had a mobo go out on me and decided it was a good time to upgrade hardware while I was buying new parts anyway. 

My old config was a MSI RS482M-IL mobo (754 socket), AMD Sempron 64 3400+ proc, 512 MB Kingston PC3200 RAM, an 80 GB HDD. My new specs are a ECS RS482-M (1.0A)(939 socket), AMD Athlon 64 3700+ San Diego 2.2 MHz (oc'd to 2.53), 2 GB Corsair XMS PC3200 RAM, and an additonal 320 GB HDD for storage. My 80 GB HDD was partitoned w/ about 55 GB for windows, 10 for fat32, and 15 for Ubuntu. My 320 has nothing to do w/ Ubuntu, just storage for music, pics, etc.

With this hardware change, I also upgraded my XP Home to PRO, so I had to do a reinstall.. I'll never do a MS upgrade on the fly. My system booted fine, but of course over wrote grub. So, I reinstalled grub, by following the how to in the ubuntuforums. Everything worked fine for booting into my windows partition, but when I try to boot into my linux partiton I get the following error: ```
root (hd0,2)
file system type unknown, partition type 0xf
Kernel/boot/vmlinuz-2.6.15-26-386 
root=/dev/sda3/roquiet splash
Error 17: Cannot mount selected partiton
```

I dont really know what the problem is, unless maybe the mobo has a different way of labeling the harddrives and the partitons. In my first setup, it was only a windows machine, then I added the linux partitons; on this setup, it was a dual boot from the start. This may not solve the problem, but what I think I need to know is: how can I relable the partitions to something that grub will recoginize or change grub to recognize the lables that the partitons already have?

Any help is greatly appreciated.

P.S. When I look at my HDD in windows, I have C: (windows), D: (fat32), and G: (storage). My opticals are E: and F:. Also, Partition Magic doesnt recognize the ubuntu partition as a valid file structure. I dont really have much info on the drive, but I would like to beat this w/o having to reinstall Ubuntu.

P.P.S I wasnt sure exactly what subject to post this thread under. If it goes somewhere else, or someone has found a similar thread, please let me know, and trust me, I have searched.

---

### Post by tommcd on 2006-10-16
Is the new motherboard the same chipset as the old one? If not,  that might be causing a problem (at least it would in windows anyway).
Also is (hd0,2) the partition ubuntu is on? Perhaps when you reinstalled grub it selected the wrong partition. Try following this guide to install grub from the live CD:
[http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD](http://users.bigpond.net.au/hermanzone/p15.htm#Re-install_Grub_with_Live_CD)
Or if you have the alternate CD:
[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28reinstall%29%7C%28grub%29](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows?highlight=%28reinstall%29%7C%28grub%29)

---

### Post by cnc333 on 2006-10-16
The new and old motherboard have the following chipsets: 
North Bridge 	ATI Radeon XPRESS 200
South Bridge 	ATI SB400

Yes, as far as i know, hd0,2 is the partition that ubuntu is installed on. In the list with the bootable OSs, its the first one. I can also choose something like a memtest and something else... its been a while since ive looked at the other choices and payed any attention to them. i do remember that they looked the same last time as they do this time.

The first link that you gave me is the link that i used to restore grub. Im still stuck, but feel that its gotta be something easy. I can post my grub/menu.lst file if it will help...

any help is appreciated

---

### Post by cnc333 on 2006-10-16
Ok, a new note. I am now in the LiveCD and going back through the steps to restore grub and have came across a strange problem. When I do ```
find /boot/grub/stage1
``` i get ```
(hd1,1)
``` ... this doesnt make sense, cuz i need grub on my first drive, thats my 320 GB storage drive. if i do ```
root (hd0,1)
``` i get ```
Error 22: No such partition
```
so now im confused ](*,)

---

### Post by benblout on 2006-10-16
Ok, I may have a hint for you.

I have been preparing to upgrade to Breezy, and reading about the problems I may encounter.  It sounds like you may have one of the common ones.  Take a peak at these links and see if it applies to your situation.

[Here]("http:////www.ubuntuforums.org/showthread.php?t=208207")
[and here.]("http://ubuntuforums.org/showthread.php?p=1257154")

I am not saying this is your problem - I don't know enough about this bug to fully understand all the ways it appears.  So take a look at the links and decide for yourself, or wait until someone more experienced comes along!

-Ben

---

### Post by cnc333 on 2006-10-16
OH WOW BEN, THANKS SO MUCH. I clicked on the first link and although it wasnt exactly my problem, I figured it out. I am actually in my ubuntu partition now. The only difference, I think, was that the problem in the link is due to a software change, and I'm 99% sure mine was hardware. My Grub was trying to boot (hd0,2) to root=/dev/sda3 and all that I did was change it to (hd0,1) and root=/dev/sda2 and it worked. I'm lucky someone was able to point me in the right direction quickly. Thanks again.\\:D/

---

