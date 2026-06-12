---
title: "Grub error 2 - no grub folder in /boot"
date: 2008-10-22
forum: Intrepid Ibex Testing and Discussion (CLOSED)
---

### Post by willc0de4food on 2008-10-22
Recently I did a partial upgrade on my hardy gone ibex installation, and for some reason or another the wifi quit working completely. Iwconfig saw my wireless card, lspci saw my wireless card, but Network Manager and ifconfig did not. So after some searching which resulted in nothing I decided to back up my home folder and give it it's own partition and reinstall. The installation was all find and dandy, but when I rebooted to get into the newly installed ibex, I was greeted with a grub error 2. When I looked in my /boot folder on the partition, there was no grub folder. It was also missing the initrd image. So I tried copying those items over manually off the cd as well as creating a menu.lst but that didn't help anything. So I booted back to the livecd, ensured the files were there including the stage1 file in the grub folder, and I opened a terminal and hopped into grub. I tried find /boot/grub/stage1 and it couldn't find anything. I tried doing root (hd0,4) and I believe it spit out error 21? Something about it wasn't a block device, etc, etc. but that is definitely the location of my installation. SO now I've run out of things that I can think of to do so if anyone has any suggestions I would greatly appreciate them.

Thanks

---

### Post by caljohnsmith on 2008-10-22
Can you simply do a reinstall, and then when you get to the final stage where you can click on the "advanced" button, make sure Grub gets installed to (hd0) or /dev/sda? You shouldn't have to manually install Grub with a new Ubuntu install. Is there something you did during the installation to tell it not to install Grub? If not, that sounds like it could be a bug.

---

### Post by willc0de4food on 2008-10-22
I could do a reinstall but I was trying to avoid that >.< oh well. The only thing I did during the installation was manually setting up my partitions. The rest I left default. I'll give another reinstall a try though and post the result.
Thanks

---

