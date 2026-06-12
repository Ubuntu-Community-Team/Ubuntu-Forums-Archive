---
title: "grub woes after removing windows etc"
date: 2010-03-15
forum: Installation &amp; Upgrades
---

### Post by Leighman on 2010-03-15
Hi guys, having a massive fail with Grub.  Any help would be appreciated.
I have Karmic installed, but still using old grub from Jaunty.
I decided to get rid of my Vista dual boot so I used gparted, deleted the partitions and moved and enlarged my Ubuntu ones.
Grub then didn't work, presumably because I deleted the MBR.
I then installed Opensuse 11.2, which I assume still uses old grub too.  This gave an Opensuse option which worked, and a Karmic option which took me to the Karmic bootloader, but Karmic did not load.
I then tried some instructions to repair grub using the Ubuntu installer, installing grub to my extended partition.  This tells me there is no operating system found.
I then tried following the instructions at [https://wiki.ubuntu.com/Grub2#Err15](https://wiki.ubuntu.com/Grub2#Err15) which did not help.

My fdisk -l looks like:
dev/sda4 * Extended partition
dev/sda5 Ubuntu /
dev/sda6 Ubuntu /home
dev/sda7 Swap
dev/sda8 OpenSuse /
dev/sda9 Opensuse /home

---

### Post by phillw on 2010-03-15
Hi, I'd suggest following this HowTo to get a kernel installed and get grub to update itself.

[http://forum.phillw.net/viewtopic.php?f=4&t=35&](http://forum.phillw.net/viewtopic.php?f=4&t=35&)

From the look of your posting, You're going to be using sda5 to put the kernel on. But, the full fdisk -l in that topic will confirm that for you.

Regards,

Phill.

---

### Post by presence1960 on 2010-03-15
Before making any suggestions I would like more info on your setup & boot process. Also if you just deleted partitions you didn't touch the MBR. 

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by Leighman on 2010-03-15
Thanks for your reply.
I've managed to fix it by reinstalling Karmic =D

---

