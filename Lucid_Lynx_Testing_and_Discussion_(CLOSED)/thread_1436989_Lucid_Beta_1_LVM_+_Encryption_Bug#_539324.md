---
title: "Lucid Beta 1 LVM + Encryption Bug# 539324"
date: 2010-03-23
forum: Lucid Lynx Testing and Discussion (CLOSED)
---

### Post by linux4me on 2010-03-23
I just did a clean install of Lucid Beta 1 using LVM and encryption. I got the error regarding a failed swap partition setup described [here]("https://bugs.launchpad.net/ubuntu/+source/debian-installer/+bug/539324"). I think I may have found a simpler workaround than is described there, but I need some confirmation from someone more knowledgeable.

When I got the error message that the attempt to mount the file system failed, I clicked "Yes" to return to the file system summary screen. Then I clicked on the swap partition, chose "swap" for the type, and then clicked Enter. Once back at the file system summary screen, I scrolled down to select finish the installation. From that point, I *think* the installation finished normally. It stayed on "wiping swap space for security" for a long time--hours--but never hung and I am able to boot into Lucid normally. 

I just have one question. Is my swap partition set up correctly?

When I enter:```
fdisk -l
```I don't get any output. When I look at /etc/fstab, this is what I see:> # /etc/fstab: static file system information.
#
# Use 'blkid -o value -s UUID' to print the universally unique identifier
# for a device; this may be used with UUID= as a more robust way to name
# devices that works even if disks are added and removed. See fstab(5).
#
# <file system> <mount point>   <type>  <options>       <dump>  <pass>
proc            /proc           proc    nodev,noexec,nosuid 0       0
/dev/mapper/<my host name>-root /               ext4    errors=remount-ro 0       1
# /boot was on /dev/sda5 during installation
UUID=eacf84a9-5c81-4fdc-b1b8-35059910d56b /boot           ext2    defaults     $
#/dev/mapper/<my host name>-swap_1 none            swap    sw              0       0
/dev/mapper/cryptswap1 none swap sw 0 0

Does that mean my swap partition is correctly set up? If not, how do I check?

---

