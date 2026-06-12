---
title: "Can't get mirror disk to fully boot up"
date: 2008-10-18
forum: Installation &amp; Upgrades
---

### Post by Widescreen on 2008-10-18
Although I've been a Solaris system administrator for over 15 years, I'm using Ubuntu to power a RAID-1 server for home.  I want this to be a fully bootable mirror.  The RAID is working fine, but I can't get Ubuntu to load up all the way if I disconnect the first drive.

For some background...

I used the alternate desktop, and created three RAID-1 partitions during the installation:
- one for /boot
- one for /
- one for file system to be shared out to the rest of the LAN

I added GRUB to both drives (grub-install /dev/sda1 and grub-install /dev/sda2).  At first, the mirror drive dropped me into initramfs.

So, I reattached hd0/sda1 then I modified menu.lst and copied 

[FONT="Courier New"]title           Ubuntu 8.04.1, kernel 2.6.24-21-generic 
root            (hd0,0) 
kernel          /vmlinuz-2.6.24-21-generic root=/dev/md1 ro quiet splash 
initrd          /initrd.img-2.6.24-21-generic 
quiet [/FONT]

into a new set of lines...

[FONT="Courier New"]title           Ubuntu 8.04.1, kernel 2.6.24-21-generic 
root            (hd1,0) 
kernel          /vmlinuz-2.6.24-21-generic root=/dev/md1 ro quiet splash 
initrd          /initrd.img-2.6.24-21-generic 
quiet [/FONT]

Now the server boots up to the Ubuntu logo, but it doesn't go anywhere else.  

So, obviously I am missing something but I'm not sure what.  mdadm shows that the mirror is up and running, and the fact that I can get to the Ubuntu logo shows that it is indeed booting from the secondary drive.  I'm guessing that it's bombing out when it attempts to mount root (/) from hd1 instead of hd0, but I don't know what to look at to determine where the problem is.

Can anyone give me a hint of what I must have missed?

Here are some other tidbits of information that might help.

[FONT="Courier New"]~$ **cat /boot/grub/device.map** 
(hd0)	/dev/sda 
(hd1)	/dev/sdb

~$ **cat /proc/mdstat** 
Personalities : [linear] [multipath] [raid0] [raid1] [raid6] [raid5] [raid4] [raid10] 
md2 : active raid1 sda4[0] sdb4[1] 
      604967616 blocks [2/2] [UU] 
      
md1 : active raid1 sda3[0] sdb3[1] 
      19534976 blocks [2/2] [UU] 
      
md0 : active raid1 sda1[0] sdb1[1] 
      128384 blocks [2/2] [UU] 
      
unused devices: <none> 

~$ **df -k | grep "/md"**
/dev/md1                   19380644     2334484   16069412   13% /
/dev/md0                     124323       24601      93303   21%  /boot
/dev/md2                  600201168      202296  569750492    %1 /home

[/FONT]

---

