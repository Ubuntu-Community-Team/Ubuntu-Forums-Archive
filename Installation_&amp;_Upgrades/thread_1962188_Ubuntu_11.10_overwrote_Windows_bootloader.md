---
title: "Ubuntu 11.10 overwrote Windows bootloader"
date: 2012-04-20
forum: Installation &amp; Upgrades
---

### Post by crhodes on 2012-04-20
Hello, I have just installed Ubuntu from a 10.10 disc and it has  overwrote my Windows boot loader giving me no option to boot from  Windows, Ubuntu automatically boots and I' am not sure how to fix this, I  have updated to 11.10 if this affects the solution?, would be highly  grateful if someone could help me with this, thanks

---

### Post by strask on 2012-04-20
Try holding down shift when booting, you should get a GRUB menu that might have an option to boot windows.

If not, someone else will have to help you fix grub because I'm not an expert at that. But, if you are in a big hurry and would like to put the windows boot loader back (instead of grub, which will keep you from booting linux), here is how to do that:

1) Boot from the windows install DVD. Select language and click next.
2) Instead of installing windows, choose the repair option.
3) The DVD will search for windows installs on your computer
3a) It might say it found boot problems and offer to automatically fix them and restart; I am not 100% sure how much damage this will do to linux so I would avoid it.
4) Select your windows install from the list and click next.
5) Select the last option to get a command prompt.
6) Type the following:```
bootrec /FixMbr
```
THIS WILL OVERWRITE GRUB IN THE MBR, REMOVING YOUR ABILITY TO BOOT LINUX.

If you are not in that much of a hurry, just hang tight and someone will be able to help you get grub to boot windows for you.

---

### Post by oldfred on 2012-04-20
While in Ubuntu run this and see if it finds your Windows install.

sudo update-grub

If not download and run the boot info script from this and post the link it gives:
Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or post the link to a run of boot info script so we can see your exact configuration.

---

### Post by crhodes on 2012-04-20
Thank you for this help, the linux community is brilliant, i have followed your instructions and the boot program gave me the link:

[http://paste.ubuntu.com/938745/](http://paste.ubuntu.com/938745/)

---

### Post by oldfred on 2012-04-20
There is no Windows as there is no NTFS partitions and only your Ubuntu install and swap. Are you sure you did not say overwrite entire drive as part of the install? It says it will erase everything at that point.

You will not be able to recover a bootable Windows. If you did have some files that you did not backup, you may (only may) be able to recover some data with a lot of work. But then stop using drive and only use liveCD or USB. You will need another 320GB drive to copy data to.

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)
Testdisk & photorec
[http://www.cgsecurity.org/wiki/PhotoRec](http://www.cgsecurity.org/wiki/PhotoRec)
[http://www.psychocats.net/ubuntucat/recoverdeletedfiles/](http://www.psychocats.net/ubuntucat/recoverdeletedfiles/)
[http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html](http://ubuntu4beginners.blogspot.com/2011/01/recover-deleted-data-using-photorec-in.html)

---

### Post by crhodes on 2012-04-20
ugh, I selected install alongside Windows, obviously not worked, will have to install Windows again and hope that doesn't overwrite ubuntu, did take me a while to sort the ubuntu installation out kept stating there is no root file system- not allowing me to install, thanks anyway!

---

### Post by oldfred on 2012-04-20
I always prefer to partition in advance and then use manual install to choose & format those partitions for the install. 

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home:
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.

---

### Post by crhodes on 2012-04-21
Big thanks for this, sorted it now, I installed windows which did get rid of Ubuntu (apart from the swap), but I installed it again and this helped a lot, boot menu comes up in grub and the windows loader is also in there, thanks once again!

---

