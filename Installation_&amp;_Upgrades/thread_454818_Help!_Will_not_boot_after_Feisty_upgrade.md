---
title: "Help! Will not boot after Feisty upgrade"
date: 2007-05-25
forum: Installation &amp; Upgrades
---

### Post by ebike on 2007-05-25
Hi All,

My Mythtv box (TV) is down](*,) after I tried upgrading it from Edgy to Feisty. I used the standard GUI upgrade manager to perform the upgrade as recomended, but the kernel refuses to boot on re-start.

The console shows:  

> Starting up
Loading, please wait:  ** <-- long timeout here then the following lines**

    Check root= booting cat /proc/cmd ine
    or missing modules, devices: cat /proc/modules ls /dev
ALERT! /dev/disk/by-uuid/069bc8f4-baca-4325-abc0-163757ebb818 does not exist. Dropping to shell!

BusyBox v1.13 .... etc
Enter 'help' for a list of built in commands

/bin/sh: can't access tty; job control turned off
(initramfs)

Can someone please show me how I can fix this with the livecd as a boot disk. 
Very much appreciated, so the kids can watch TV again ......:(

---

### Post by confused57 on 2007-05-25
You'll need to mount your root partition, using the live cd:
[http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD](http://users.bigpond.net.au/hermanzone/p10.htm#Mounting_Ubuntu_with_Dapper_Desktop_LiveCD)

You can run this from the terminal to determine your current partition filesystem UUID's:
```
blkid
```

Whatever directory you used to mount your root partition, let's say you used "/media/ubuntu", you can open your menu.lst and /etc/fstab and compare the UUID's in these files to the blkid results:
```
gksudo gedit /media/ubuntu/boot/grub/menu.lst
gksudo gedit /media/ubuntu/etc/fstab
```
menu.lst is short for menu.list

If they're different, you can probably just copy & paste the new UUID from the blkid output to your menu.lst & fstab.

---

### Post by ebike on 2007-05-26
Hi, 

tried that,but the UUID's are the same ......:(

My boot partition is hda1, and it shows exactly the UUID that is being reported as nott existing.

Any other suggestions?

---

### Post by confused57 on 2007-05-26
> **ebike said:**
> Hi, 

tried that,but the UUID's are the same ......:(

My boot partition is hda1, and it shows exactly the UUID that is being reported as nott existing.

Any other suggestions?
Is your /etc/fstab also showing the correct UUID?  You might want to post your /boot/grub/menu.lst and fdisk -l...the -l is a small "L"

```
sudo gedit /media/ubuntu/fdisk -l
```

You might also try the command line interface(CLI) to investigate your computer and possibly get your Ubuntu to boot:
[http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot](http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot).

If this doesn't work, you might try doing a filesystem check on your root partition:
[http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem](http://users.bigpond.net.au/hermanzone/p10.htm#filesystem_check_on_an_ext3_filesystem)
the gparted live cd is probably the easiest way to do this, but it can be done from the terminal.

You could also try the Super Grub Disk:
[http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html](http://users.bigpond.net.au/hermanzone/SuperGrubDiskPage.html)
the main download website seems to be down at the moment, hopefully it'll be back online soon.

---

### Post by ebike on 2007-05-26
Yes the UUID was correct in both menu.1st and /etc/fstab ..

I cannot post what you want as the machine is not connected to the network at present ... I will see if
I can arrange that.

By the way, how do I re-install grub to the MBR, just in case that has been corrupted.

---

### Post by confused57 on 2007-05-26
> **ebike said:**
> Yes the UUID was correct in both menu.1st and /etc/fstab ..

I cannot post what you want as the machine is not connected to the network at present ... I will see if
I can arrange that.

By the way, how do I re-install grub to the MBR, just in case that has been corrupted.

You can try reinstalling grub to the mbr, using the live cd:
[http://ubuntuforums.org/showthread.php?t=224351](http://ubuntuforums.org/showthread.php?t=224351)
sure wouldn't hurt to try it

---

### Post by ebike on 2007-05-26
Hi,

I have tried to re-install grub to the MBR, but that doesn't help ... mind you, grub boots fine, it just can not
find the disk using the UUID.

I have also tried e2fsck on the boot partition, and there doesn't seem to be any bad blocks.

I did an fdisk -lu again on the drive and noticed that no partition had an asterix "*" in the boot column, so I
made the /dev/hda1 partition bootable with the "a" option, wrote out the table and tried re-booting, but still no joy.

I am getting stumped.

I might next try modifying menu.1st and /etc/fstab to not use UUID, but use the old method of named partitions
and see if that will work.

Any other suggestions very welcome though.

---

### Post by confused57 on 2007-05-26
Have you tried booting one of the older Feisty kernels?

This thread "might" help:
[http://ubuntuforums.org/showthread.php?t=421588](http://ubuntuforums.org/showthread.php?t=421588)
or
[http://ubuntuforums.org/showthread.php?t=415009&highlight=tty+turned+off](http://ubuntuforums.org/showthread.php?t=415009&highlight=tty+turned+off)

---

### Post by ebike on 2007-05-26
Tried that .... still no joy.

If I don't sort this soon I am going to do a backup of that partition and do a complete re-install of Feisty
from the CD and a re-install of Mythtv ..... not a  happy camper :(

---

### Post by ebike on 2007-05-28
Found no resolution for this problem, so bit the bullet and re-installed. ....:(

I tried initially with the "Feisty backend frontend" guide, but that was a complete pain, as it automated everything
on boot, so if you shutdown mythtv, it logged you out. The edgy version of that, at least let you stay in the session and open up a console to fix anything ...

So, I installed the desktop frontend backend version and that worked fine... and I can go back to the gui for 
any admin tasks as well as the console.

---

### Post by jordg on 2008-01-04
Not sure if this was the problem but after moving hard disks I could not boot unless I changed root=UUID=bla-bla to root=/dev/hda1 in the grub boot menu at boot

It seems that in /boot/grub/menu.list the kopt=root parameter can be left from previous settings so when you upgrade a kernel it hold on the old UUID and not the new.
This can get out of sync with /etc/fstab also

kopt=root=UUID=c0785248-c5d2-4fcc-b76a-eeb19f04f49f ro

Personally I think UUIDs have succeeded in making things complicated

---

