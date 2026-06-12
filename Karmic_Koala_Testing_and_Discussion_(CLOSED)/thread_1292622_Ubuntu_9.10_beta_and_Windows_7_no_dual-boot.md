---
title: "Ubuntu 9.10 beta and Windows 7 no dual-boot"
date: 2009-10-16
forum: Karmic Koala Testing and Discussion (CLOSED)
---

### Post by andrei048 on 2009-10-16
Hello,

I have Windows 7 and I have just installed Ubuntu 9.10 (USB stick install). Ubuntu 9.10 comes with grub-2, that I have no ideea of.

My problem is that after I made my 2 partitions for Ubuntu (/dev/sda6 Linux and /dev/sda5 for Swap) and choose to install grub2 on /dev/sda6, the install rebooted but now I don't have a Grub menu to choose from.

Windows 7 boots like there is nothing else there.

Windows 7 has it's 100 MB partition at the begging of the hard-disk and Linux is installed on an extend partition, /dev/sda6 and /dev/sda5 being both logical partitions.

Any ideea how to fix this ?

---

### Post by lithorus on 2009-10-16
You need to install grub on /dev/sda. It needs to be installed on the Master Boot Record to get the first to boot. Otherwise it's up to the MBR of Windows 7.

---

### Post by adder1972 on 2009-10-16
[https://wiki.ubuntu.com/Grub2](https://wiki.ubuntu.com/Grub2)

---

### Post by the.lost.one on 2009-10-16
_shouldn't there be any way to write a few commands to direct windows bootloader to the karmic bootloader_? we could do this with jaunty and easyBCD. but easyBCD doesnt support grub2

---

### Post by psyke83 on 2009-10-16
> **the.lost.one said:**
> _shouldn't there be any way to write a few commands to direct windows bootloader to the karmic bootloader_? we could do this with jaunty and easyBCD. but easyBCD doesnt support grub2

No. The Windows bootloader treats non-Microsoft operating systems as *less* than an afterthought. You should install GRUB to the MBR, as was mentioned already.

---

### Post by Yakumo. on 2009-10-20
It should be entirely possible to do this with EasyBCD 2 (free windows BCD editing utility)

Some have had success already, but others (myself included sadly) are having problems with easybcd 2's grub2 support, but it is a beta atm and should be resolved soon.

---

### Post by scokem on 2009-10-21
> **Yakumo. said:**
> It should be entirely possible to do this with EasyBCD 2 (free windows BCD editing utility)

Some have had success already, but others (myself included sadly) are having problems with easybcd 2's grub2 support, but it is a beta atm and should be resolved soon.

I'm currently dual-booting Vista and Karmic using the WBM (configured with EasyBCD) and after weeks of messing around with various configurations, I finally have it working.  Hopefully this'll work for Win 7 and you'll be able to do it too.

Firstly, you're gonna need to re-install Ubuntu using ext3 (ext4 is out of the question for now - none of my attempts or the guys over on the EasyBCD forums have managed to get it to work yet).  When you do re-install it, make sure at the last part of the setup, you click the advanced button and choose to install grub to the drive you have configured to be /.

Once the install has completed, get into Windows and open EasyBCD - you'll need the beta version if you haven't already got it - then create a new entry for Ubuntu using the Linux option selecting the drive you've made / and ticking the box below it.  By ticking the box, you'll have opted to use NeoGrub so you should find a menu.lst file in C:\NST\ which you will need to edit with notepad or whatever text editor you use.  Firstly, comment out (or delete) all of the current sections that start with "title xxx" and then create a new entry with this (change the drive to be appropriate to your setup obviously):

```
title WhateverYouWantHere
root (hd0,4)
kernel /boot/grub/core.img
boot

```then save the file and reboot.  Select the entry and you should eventually end up looking at a nice Grub2 menu :)

I know it's not ideal to have to re-install using ext3 but it's the only option I'm aware of at the mo.  Hope this helps anyway.

---

### Post by Yakumo. on 2009-10-21
Sorry, i meant to say ext4 and grub2, I've duel booted ubuntu  with the vista/7  boot manager with ext3 very easily, easybcd almost makes it entirely self explanatory.

easybcd 2 claimed full ext4 support though which is what I'd wanted to try.

I posted on the neosmart forums too, hopefully they'll work out what's going wrong for the next build release.

---

### Post by oldfred on 2009-10-21
I installed Grub2 to the partition like you did. I do get warning messages that block device or something is not recommended but it works. With grub2 in the partition you can chainboot. I am doing it from old grub but I do not see why chainboot will not work with anything that is grub like i.e.  easyBCD. The chainboot does not care if the partition is ext4 since grub2 is what is chained to and will read the ext4 partition:

Put an entry like this but adjust for your drive & partition:

title       Ubuntu 9.10 Karmic 64 bit @ sdc7
root        (hd2,6)
chainloader +1

---

### Post by volcan_hacker on 2009-10-22
Hi,

I had similar problem and I just solved it using this and few other threads/wikis. Thank you guys, you are awesome! 

I am posting the complete process to help others.

**Problem:**
[I]I had Vista installed on sda1. I installed Karmic Koala 32bit beta on sda8 with ext4 and grub2. grub2 was written on MBR. And my Vista OS was gone, not listed on the the grub2 boot menu as expected. So I had to figure out how to add it there.
[/I]
**Solution:**

Get UUID of /dev/sda1 partition, where the Vista OS resides. Run this command and read the output,

```
sudo blkid
```Edited /etc/grub.d/40_custom,

```
sudo gedit  /etc/grub.d/40_custom
```Then added these lines at the end of this file,

```
menuentry 'Windows Vista'{
insmod ntfs
set root=(hd0,1)
search --no-floppy --fs-uuid --set <UUID of my /dev/sda1 partition>
chainloader +1
}
```saved the file, and run this command to update grub2 config,

```
sudo update-grub
```Now I can restart and select Windows Vista from the grub2 menu to load Vista.

Hope this helps others. 

Helpful link:
[http://ubuntuforums.org/showthread.php?t=1195275](http://ubuntuforums.org/showthread.php?t=1195275)

---

### Post by ranch hand on 2009-10-22
There are links within the post below to how to recover grub2 from a live cd;

[http://ubuntuforums.org/showthread.php?t=1285897](http://ubuntuforums.org/showthread.php?t=1285897)

Win JerryLewis Pro does not support ext4 so it can't read it at all.  Greater security for your non MS files.

---

### Post by Yakumo. on 2009-10-24
Easy BCD 2.0 build ***65*** just came out today, and it worked instantly with the 9.10 RC. using it was a 3 click process.

I just downloaded the ubuntu 9.10 RC cd, installed to a primary  partition with ext**4**, and bootloader on THAT partition. ran windows, ran  easyBC 2 (build 65) chose add new, linux -> grub **2** (no other options  necessary) reboot and it worked first time :)

---

### Post by ranch hand on 2009-10-24
Great.

Mark the thread solved for the next guy (top of page under "thread tools").

---

