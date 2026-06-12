---
title: "Can't get my head around hd(0,0) and sda1 conversion!"
date: 2010-03-16
forum: Installation &amp; Upgrades
---

### Post by Ostrichmeat on 2010-03-16
Hi all,

I'm setting up my menu.lst for GRUB Legacy (downgraded from GRUB2 in 9.10) and I'm just having difficulty getting my head around converting the /dev/sda1, sda2 etc to hd(0,0), (0,1).

My partitions are as follows:

sda1 = Windows XP (ntfs primary partition)
sda2 = Windows Vista (ntfs primary partition)
sda3 = Linux boot (small ext2 primary partition)
sda4 = extended partition
sda5 = Windows XP second different installation (ntfs logical partition)
sda6 = Ubuntu 9.10 root (ext3 logical partition)
sda7 = linux-swap (swap logical partition)

As I said, I am trying to set these up in GRUB, but cannot work out what all the hd(0,x) equivalents are. I *thought* it was just a case of subtracting 1 from the sdax number, but it doesn't appear to be that way.

---

### Post by phillw on 2010-03-16
> **Ostrichmeat said:**
> Hi all,

I'm setting up my menu.lst for GRUB Legacy (downgraded from GRUB2 in 9.10) and I'm just having difficulty getting my head around converting the /dev/sda1, sda2 etc to hd(0,0), (0,1).

My partitions are as follows:

sda1 = Windows XP (ntfs primary partition)
sda2 = Windows Vista (ntfs primary partition)
sda3 = Linux boot (small ext2 primary partition)
sda4 = extended partition
sda5 = Windows XP second different installation (ntfs logical partition)
sda6 = Ubuntu 9.10 root (ext3 logical partition)
sda7 = linux-swap (swap logical partition)

As I said, I am trying to set these up in GRUB, but cannot work out what all the hd(0,x) equivalents are. I *thought* it was just a case of subtracting 1 from the sdax number, but it doesn't appear to be that way.

Hi, you are correct.
hd(0,0) = sda1

The full run-down on it, along with installation of grub legacy can be found here --> [http://www.gnu.org/software/grub/manual/grub.html#Naming-convention](http://www.gnu.org/software/grub/manual/grub.html#Naming-convention)

You may also find the ubuntu community document useful --> [https://help.ubuntu.com/community/GrubHowto](https://help.ubuntu.com/community/GrubHowto)

Regards,

Phill.

---

### Post by coffeecat on 2010-03-16
> **Ostrichmeat said:**
> converting the /dev/sda1, sda2 etc to hd(0,0), (0,1).

> **phillw said:**
> Hi, you are correct.
hd(0,0) = sda1

Actually, it's (hd0,0) - note placement of brackets.

I know you've downgraded to legacy grub and that you're no longer using  grub 2, but just for completion (and to show that the grub devs are  completely on the side of the angels :rolleyes:), the convention in grub  2 has changed.

In grub 2, the device (drive) number starts from zero and the partition number starts from 1.

So that, sda1 = (hd0,0) in legacy grub = (hd0,1) in grub2.

---

