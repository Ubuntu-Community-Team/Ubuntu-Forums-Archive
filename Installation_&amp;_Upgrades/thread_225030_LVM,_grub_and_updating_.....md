---
title: "LVM, grub and updating ...."
date: 2006-07-28
forum: Installation &amp; Upgrades
---

### Post by lonewolf on 2006-07-28
Hi,

I am hoping someone can give me a hand with a problem that I have run into since updating from Ubunto 5.10 to 6.06. As part of the upgrade a new kernel image 2.6.15 was downloaded and I can see the appropriate files in the /boot area. For some reason my system is still running the old 2.6.12 kernel and not seeing the newly downloaded kernel images.

I am running LVM and I suspect that I need to modify the GRUB configuration so it sees the location of the new kernel images (or copy them to an area that grub can see).

I have tried to run: sudo grub-install /dev/sda but I get an error saying: 

/dev/mapper/Ubuntu-root does not have any corresponding BIOS drive.

Cheers

---

### Post by Herman on 2006-07-28
I don't know very much at all about LVM and its affects on Grub and booting.
It might help though, I hope, if you try using Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli")
and use the 'find' command ('find /vmlinuz) as explained in the link, to discover your new kernels and how to address them. If you can boot them from Grub's [Command Line Interface]("http://users.bigpond.net.au/hermanzone/p15.htm#cli") you should be able to insert the same commands into your /boot/grub/menu.lst to have them added to your Grub menu.
This works for plain ordinary (non-LVM) installs, but again, I'm not sure how LVM affects booting.
Good Luck, From Herman :D

---

### Post by peabody on 2006-07-30
methinks '$ sudo update-grub' will do the trick.

---

### Post by lonewolf on 2006-07-30
Thanks to all those that responded. If anyone is interested here is a summary of what I eventually worked out.

I took Herman's suggestion of using the grub shell and the find command to explore what was on my boot partition. I the realised what the problem was - I had decided to be tricky and create a separate boot partition and not mount this partition after the system was up and running. 

This meant that when I did a system update another '/boot' partition was created - this partition contained the updated kernel I was after. 

The solution to my problem was to edit /etc/fstab and mount my /boot partition which was on /dev/sda1. After editing the mount points I rebooted the system - could have done a 'mount -a' apparently but a reboot worked. When I logged in again /boot contained the kernel images grub was presenting on boot. I then used synaptic to reinstall the latest kernel image and grub for good measure. System now all up-to-date. I have commented out mounting /boot again - hopefully I will remember to remount it next time I update the kernel :)

Cheers,

Kieran

---

### Post by Herman on 2006-07-30
:D Excellent, and well done! Regards, Herman :D

---

