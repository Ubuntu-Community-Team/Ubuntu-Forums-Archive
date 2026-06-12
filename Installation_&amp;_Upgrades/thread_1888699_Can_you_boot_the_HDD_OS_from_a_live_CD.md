---
title: "Can you boot the HDD OS from a live CD?"
date: 2011-11-29
forum: Installation &amp; Upgrades
---

### Post by kenji_03 on 2011-11-29
I know you can boot a live CD version of Ubuntu, but is it possible to use a live CD as a "grub boot" drive?

Most of the problems I've had with Ubuntu are with Grub in one form or another, and I think that goes for a lot of people.  As such, is there any way to make a Grub CD or Grub USB that would let us boot into our /dev/sda partitions?

---

### Post by fdrake on 2011-11-29
> **kenji_03 said:**
> I know you can boot a live CD version of Ubuntu, but is it possible to use a live CD as a "grub boot" drive?

Most of the problems I've had with Ubuntu are with Grub in one form or another, and I think that goes for a lot of people.  As such, is there any way to make a Grub CD or Grub USB that would let us boot into our /dev/sda partitions?
that's actually a VERY VERY VERY interesting idea. I want to know more so i will follow your thread! good suggestion

---

### Post by kenji_03 on 2011-11-30
Well, I was able to use [this guide]("http://feeding.cloud.geek.nz/2009/08/grub-on-bootable-usb-rescue-stick.html") to make a "grub usb" that would boot.  But for some reason the version of Grub was missing all the normal grub commands (I installed it from an ubuntu live usb).  So while technically a success, it didn't help me one bit...

Can someone with more technical skill help me install grub from somewhere other than the cd?

---

### Post by darkod on 2011-11-30
What problems is actually grub2 on the MBR giving you, to want to use removable media just for boot?

And as far as those instructions are concerned, if I understand it correctly you need to run that procedure from your hdd OS booted up, not from a live usb. It's not the same. Can't you boot the hdd OS even once?

---

### Post by kenji_03 on 2011-11-30
> **darkod said:**
> What problems is actually grub2 on the MBR giving you, to want to use removable media just for boot?

And as far as those instructions are concerned, if I understand it correctly you need to run that procedure from your hdd OS booted up, not from a live usb. It's not the same. Can't you boot the hdd OS even once?

The problem is that I updated 10.04 incorrectly.  Had to delete my 10.04 install and install 11.10 on top of it.  For some reason GRUB would only load to the rescue mode after the install and after tinkering with it now it won't even load to that.

HENCE why I wold like to use a usb to boot it correctly (1: it'd add an extra layer of security.  2: My linux machine was not made for a CD drive, I have one but it is sitting on top of it -- guts exposed).

Edit: Also, I have three other partitions of Data I cannot afford to lose in NTFS format -- don't ask why.  It was a stupid move when I was a novice in Linux

---

### Post by darkod on 2011-11-30
If only grub2 didn't get installed, the easiest is to try reinstall it to the MBR first. However, there are two options:
1. The grub2 files and the package were correctly installed, only the part on the MBR isn't.
2. Both the package, files, and the part on the MBR are not installed.

If it's option 1, it's fairly easy to reinstall it to the MBR from live mode. Boot with the usb stick in live mode, in terminal do:

sudo fdisk -l (small L) to find out your root partition, unless you know it

Lets assume it's /dev/sda1

Reinstall grub2 to the MBR with:
sudo mount /dev/sda1 /mnt
sudo grub-install --root-directory=/mnt /dev/sda

Reboot and check if it worked.

But if the package files are messed up, you need to enter the hdd partition with chroot and reinstall all of it. I'll put it another post to be a separate procedure.

---

### Post by darkod on 2011-11-30
If the grub2 package was never installed, or is screwed up in major way, you can remove and reinstall it. The problem is that running from live mode is not aware of your root partition on the hdd, and the OS on it. You enter inside it with procedure called chroot.
In these commands I assume you have no separate /boot partition, if you do you need to mount it too after mounting root. I also assume that your root is /dev/sda1, if it's something else like /dev/sda5 just use that.

To mount the hdd partition ready for chroot from live mode you use:
```
sudo mount /dev/sda1 /mnt
sudo mount --bind /proc /mnt/proc
sudo mount --bind /dev /mnt/dev
sudo mount --bind /sys /mnt/sys
sudo chroot /mnt
```

From this point on, it's like you are inside your hdd installation as root user. To completely deinstall, then reinstall grub-pc package and create new config files, run:
```
apt-get --purge remove grub-pc
apt-get install grub-pc
grub-mkconfig
grub-install /dev/sda
```

To exit chroot and safely unmount:
```
exit
sudo umount /mnt/sys
sudo umount /mnt/dev
sudo umount /mnt/proc
sudo umount /mnt
```

In most cases that should do it. Unless you have some specific setup on your computer, for example HP or Dell protective tools that chop off part of grub2 on the MBR on every boot. There have been cases like that.

---

### Post by oldfred on 2011-11-30
Darko has given the simple and the full chroot methods to reinstall grub2. The simple one is easy enough and it should work for most from a Ubuntu LiveCD. Grub 1.99 now requires that you use a liveCD of the same version of Ubuntu to work correctly with the simple method.

Some do like to have other ways. (Some might call me a belt and suspenders type as I have all of them available on Cd or USB before I make system changes). Plus I have one or two other systems like slax & puppy, just in case.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

[http://www.supergrubdisk.org/](http://www.supergrubdisk.org/)

Herman has instructions for grub2 rescue boot CD, USB, or floppy. Also grub legacy
[http://members.iinet.net/~herman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM]("http://members.iinet.net/%7Eherman546/p20/GRUB2%20Bash%20Commands.html#GRUB2_CD-ROM")

---

