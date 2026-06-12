---
title: "ubuntu wont boot"
date: 2006-07-18
forum: Installation &amp; Upgrades
---

### Post by josh on 2006-07-18
hi guys!

i recently installed ubuntu on my SATA disc (112GB) that has windows on it.
the install went fine and when it asked me to restart, i did and it went straight to windows. it did not show the grub menu for me to choose which os to load. i recall before, when i still had my other hard disk, i have installed windows on my sata and ubuntu on my ide and everytime i boot up, i gave me the grub menu. now that i installed windows and ubuntu on the same SATA disc, it doesnt give me the grub menu and just proceeds loading windows. is it something to do with my SATA disc because its 112GB? if so how do i fix it without damaging the windows partition? i also remember before when i used redhat that i made a floppy startup disk for me to load redhat. there was and option in redhat that if you dont want to install grub/lilo in your harddisk you can make a startup disk and that would boot redhat from the floppy you created. is it also possible in ubuntu? thanks in advance guys!

windows partition:
windows = 68GB ntfs

ubuntu partitions:
/ = 38GB ext3
swap = 1GB swap
/media/storage = 4.3GB (logical)fat32

---

### Post by mzoller on 2006-07-19
> **josh said:**
> 

windows partition:
windows = 68GB ntfs

ubuntu partitions:
/ = 38GB ext3
swap = 1GB swap
/media/storage = 4.3GB (logical)fat32

I would say boot floppies have definately gone out of style!

Looks like you are going to have to install grub manually:
:

1.) boot from livecd
2.) mount the partition with linux on it (can't tell from above info) on /mnt/
3.) become root: sudo su
4.) chroot /mnt/
5.) grub-install /dev/sda (assuming that is the harddrive you installed win/linux on)
6.) possibly change grub entries in /boot/grub/menu.lst
7.) reboot
8,) google(groups) is your friend.

---

### Post by Hedzu on 2006-07-19
I have the same problem, and another one.

After I mount and chrooted the sata disk where i've installed ubuntu(sdb2) they don't exist on the ubuntu installed disk partition. 
The devices /dev/sd*** just don't exist at all.
How do I create them?

Thank you.

The motherboard is nforce4x and i'm using the ubuntu 6.06 64bit version

---

