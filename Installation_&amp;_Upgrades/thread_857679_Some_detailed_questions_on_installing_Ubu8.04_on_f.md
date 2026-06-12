---
title: "Some detailed questions on installing Ubu8.04 on fakeRAID1"
date: 2008-07-12
forum: Installation &amp; Upgrades
---

### Post by my_2_cents on 2008-07-12
Folks;

My first post. I haven't been successful yet in installing Ubuntu 8.04 on my multi-boot system. I'll try not to make this a long post, but I feel I'm close to a solution approach after reading many (conflicting) accounts of how to do this, none of which are exactly the route I am trying to use.

I have a mobo with Intel ICH6R fakeRAID controller and two new Seagate 1 TB drives setup in a RAID1 mirror. I use Terabyteunlimited BootItNG as my boot/partition manager and I have setup the following partitions already:

1 primary partition for BING
2 primary partition for Windows XP Home Edition (NTFS)
3 primary partition for USER data (NTFS)
4 extended partition for Linux:
  5 logical volume for Ubuntu root (ext3 if possible)
  6 logical volume for Ubuntu swap

Both BING and WinXP are working fine on the RAID1 mirror. I also had no trouble setting up the extended partition in preparation for installing Ubuntu.

My understanding of installing Ubuntu 8.04 from the Live CD to a fakeRAID mirror is:

1) boot Live CD
2) install dmraid to Live CD
3) start installer from Live CD
4) choose partitions manually for root and swap
5) follow installer to end (or error?)
6) install dmraid on root partition using console
7) install grub on root partition using console
8) reboot
9) select Ubuntu from BING menu
10) pray

Following are the details I would like to check with you for reasonableness. It has been 15 years since I used BSD on a Sun workstation, so my unix command understanding is rusty.

Install dmraid on Live CD:

add "universe" package and start a console and exec
> sudo dmraid -ay
to install fakeRAID (on ramdisk?)
I'll note the name of the fakeRAID device from the command output and then identify the root and swap partitions
> sudo fdisk /dev/mapper/fakeRAIDdev
For example, root might be fakeRAIDdev5 and swap fakeRAIDdev6

After running the GUI installer, I open a console and install dmraid on the root partition
> mount --bind /dev /target/dev
> mount - t sysfs sysfs /target/sys
> chroot /target
> aptitude install dmraid

While still in chroot, I install grub on the root partition
> cp /usr/lib/grub/i386-pc/* /boot/grub
and then run grub
> grub
grub> device (hd0) /dev/mapper/fakeRAIDdev
grub> find /boot/grub/stage1
from this result I get, for example, (hd0,4)
grub> root hd(0,4)
grub> setup (hd0)
grub> quit
> update-grub
I don't need to edit menu.lst because I have dmraid installed and grub is only managing the Ubuntu boot. BING is the boot manager in charge. For this reason, I can't install GRUB to the drive MBR.
I exit the console, finish the installation if I got an error, and reboot and hope that when I choose Ubuntu in BING that I get it to boot and see the RAID mirror and my two Ubuntu partitions.

I know there are many other ways to approach this setup, using the alternate CD command line and many other multi-boot setups possible, but if you see any specific errors in what I am doing or have specific advice, I would appreciate your input before I launch into this.

Ah, my Live CD distro has finished downloading. Now to burn it to CD and give this a go, after waiting a bit to see what you expert folks have to say about my approach.

Thank you very much for reading this to the end. Good day.

---

### Post by my_2_cents on 2008-07-15
My solution to this problem of Ubuntu 8.04 on RAID mirrors was to install VirtualBox on Windows XP and install Ubuntu inside VirtualBox.

---

