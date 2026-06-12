---
title: "GRUB Error 15"
date: 2008-04-05
forum: Installation &amp; Upgrades
---

### Post by QenBirQeni on 2008-04-05
I have a machine that's got the following partitions 1 NTFS partition, 2 FAT32 partitions, 1 SWAP, 1 root, 1 EXT3. I had installed Xubuntu initially on the root partition, but I decided to install Kubuntu. After the installation (made no changes to GRUB) I started to download the updates. Problem is, when I restarted the system, I got a lovely Error 15 - File not found message. I did enter GRUB, and tried to change the partition it was supposed to boot from, but to no avail:

[INDENT]grub> root (hd0,0) # Here I tried hda1-9, but no go
grub> setup (hd0)
grub> quit
[/INDENT]

I also tried it through he GRUB menu (using the "c" option), and failed again.

I'm certain that my installation was fine, and Kubuntu is in there, I just can't seem to boot into it. GRUB is kind enough to let me boot into Windows. Please help, I'm running out of ideas.

---

### Post by zvacet on 2008-04-05
[Here](http://users.bigpond.net.au/hermanzone/p15.htm#15)

---

### Post by QenBirQeni on 2008-04-07
Thanks you for the link. As far as I could tell, all my problems were caused by a failed upgrade. I just replaced the initrd file with the backup one. Completed full upgrade later. I was almost ready to reinstall - phew!

---

