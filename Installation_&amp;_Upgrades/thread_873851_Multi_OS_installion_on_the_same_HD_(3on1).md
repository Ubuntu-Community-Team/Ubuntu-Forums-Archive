---
title: "Multi OS installion on the same HD (3on1)"
date: 2008-07-29
forum: Installation &amp; Upgrades
---

### Post by CrAzYoNi on 2008-07-29
Hi all,
I've got some laptop I'm using as my lab-box.

I have there Intel T5600 (1.83 Ghz Core2Duo) CPU, 2GB of RAM 333Mhz & a hard drive (Fujitsu) 120Gb.

I partitioned it to 3 partitions (Each is 20Gb) - All the rest I left unpartitioned yet...

- On the 1st partition I installed XP sp2 64-bit.
- On the 2nd partition I installed ubuntu 8.4 64-bit.
- On the 3rd partition I hope to install Mac OSX....

After I installed Ubuntu I got an error that Grub wasn't installed.
I can't run my ubuntu :(

Is there any way to install manually (& hope simply) GRUB or LILO on my windows partition??

Thanks for the help in advantage!!

---

### Post by Potatoj316 on 2008-07-29
grub should have been installed when you installed ubuntu, but i guess it wasnt.  You didnt change anything after you installed ubuntu and you tested it did you?  If not search on google or the forum for "install grub".  All you need is a live CD and like 5 minutes.  Its really easy, ~5 commands

---

### Post by CrAzYoNi on 2008-07-29
Hey! Thanks for your fast reply!!
I didn't tested the Ubuntu.. I just did reboot after the Installion.

Should I create partition of boot? swap? all I did was the root partition 20 gb of size.

---

### Post by Potatoj316 on 2008-07-29
i mean tested as in try to run and get the error.  

heres a link that shows you how to install grub from a ubuntu live CD, it should work but you may have to manually add windows to the list, but I can help with that.
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

how did you do the partitions, did you tell it guided and use this partition, or did you manually create partitions?  You may have to create swap.  Your computer can run without swap but it is good to have, especially if you dont have a lot of RAM.  But you have a good amount.  If you create a swap partition put it in a logical partition, not a primary partition, this way it dosent count as a primary partition.

Not having swap should not cause this problem.

---

### Post by CrAzYoNi on 2008-07-29
Well, So far this is what I did:
- Enter to the liveCD system
- Open terminal
Typed:
- sudo mkdir /mnt/root
- sudo mount -t ext3 /dev/sda5 /mnt/root
- sudo mount -t proc none /mnt/root/proc
- sudo mount -o bind /dev /mnt/root/dev
- sudo chroot /mnt/root /bin/bash
- sudo grub
- find /boot/grub/stage1
- root (hd0,4)
- setup (hd0)
- I opened Gparted
- I unset the flags on my Windows partition.
- I set the flag on:ext3 /media/disk - as boot.

Now after I rebooted my system I got into the Grub shell but nothing happen.
so I did:
- Enter the liveCD system again
- Open Nautilus
- Searched for menu.lst in the /boot/grub

But nothing was found...

---

### Post by CrAzYoNi on 2008-07-29
Now I did:
- Enter the liveCD system
- Open terminal
Typed:
- sudo mkdir /mnt/root
- sudo mount -t ext3 /dev/sda5 /mnt/root
- sudo mount -t proc none /mnt/root/proc
- sudo mount -o bind /dev /mnt/root/dev
- sudo chroot /mnt/root /bin/bash
- update-grub
The proccess talled me that it does not found any menu.lst file & it ask me if I want to regenerate the menu.lst file (y/n question kind...) I answered "Yes" & the script searched for ubuntu copy, it found it.
After I rebooted the system Ubuntu 8.4 was running!! :)

Now I have another problem, something about the Nautilus & Bonobo-activation-serrver but I'll try to solve it by my self now.

Thanks for all of the help!! :)

After that I'll edit the menu.lst (I'll try by my self) for enabling boot windows as well... & wish for edit it to run Mac OSX as well & then I'll close this thread!

---

