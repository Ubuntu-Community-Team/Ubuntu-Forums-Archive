---
title: "Grub problem after double feisty and gutsy installation"
date: 2007-08-24
forum: Installation &amp; Upgrades
---

### Post by amonsul on 2007-08-24
Hi!

I've installed feisty (works fine) and then gutsy on an other hard disk

I have 3 hard drives:

1) sda (only data)
2) sdb (feisty) and it has worked fine
3) sdc (gutsy)

but after the gutsy installation something has gone wrong and Grub doesnt load anymore (error 17)

How can i restore GRUB?

I`ve tried this, starting from the liveCD but it doesnt work:

sudo mount /dev/sdc2 /mnt
sudo mount /dev/sdc2 /mnt/ubuntu/boot
sudo grub-install --root-directory=/mnt /dev/sdc2


my fdisk -l looks so:

> ubuntu@ubuntu:~$ sudo fdisk -l

Disk /dev/sda: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *           1       38912   312560608+   7  HPFS/NTFS

Disk /dev/sdb: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1               1        5137    41262921   83  Linux
/dev/sdb2            5138        5542     3253162+  82  Linux swap / Solaris
/dev/sdb3            5543       38913   268052557+  83  Linux

Disk /dev/sdc: 320.0 GB, 320072933376 bytes
255 heads, 63 sectors/track, 38913 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sdc1               1         243     1951866   82  Linux swap / Solaris
/dev/sdc2           33777       38913    41262952+  83  Linux
/dev/sdc3            9462       33776   195310237+  83  Linux


---

### Post by Pumalite on 2007-08-24
Try Super Grub: [http://supergrub.forjamari.linex.org/?section=download](http://supergrub.forjamari.linex.org/?section=download)

---

### Post by confused57 on 2007-08-24
You might want to reinstall Feisty's grub IPL to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)

It looks like you've installed Gutsy's grub to the root partition, so you should be able to use a chainloader entry to boot Gutsy:
[http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems](http://users.bigpond.net.au/hermanzone/p15.htm#Operating_System_Entries_for_Multiple_Booting_More_Linux_Systems)

---

### Post by ArtF10 on 2007-08-24
Similar thing happened to me.  Do post if/how you get it resolved.

---

### Post by amonsul on 2007-08-26
Hi!

It was a bios problem. For some reason the harddiskorder has changed and this was the problem. I`ve changet it now and all works fine.

Anyway, thanks a lot for your help!

---

