---
title: "Feisty not installing boot track"
date: 2007-04-17
forum: Installation &amp; Upgrades
---

### Post by awilcox on 2007-04-17
Hello,
I got an ISO of 7.04 last week, and it loaded perfectly as a virtual machine under VMware. I'm using it now in fact.

Made a CD today, booted a spare PC (Athlon 850, 512GB RAM, 80GB IDE), and got to the desktop. I selected the "install" icon on the desktop and went through the steps. Chose to **install boot to hd0** at the last step. Perfect. Files copied. Desktop again for a reboot when ready.

Rebooted, but "no operating system" found on the disk. Ooops! (Repeated, but still no OS.)

I rebooted with CD, became root, did** fdisk -l** to find where to  cd for the proper first partition where I installed Feisty. 
Then I invoked grub. Did **root (hd0)** and then **setup (hd0,0)** but grub didn't find the files.

Looked in the first partition. Couldn't find /boot/grub/menu.lst or /etc/grub.conf ... Where are they supposed to be?

What to do? 

Thanks,
Alan
-------------------------------
Console text just as we leave the BIOS:
[B]Searching for Boot Record from IDE-0..OK
Missing Operating System[/B]
  <and that's where it stops>

---

