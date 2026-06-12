---
title: "I can't figure out how to install XP"
date: 2008-11-25
forum: Installation &amp; Upgrades
---

### Post by Patney on 2008-11-25
Hi, I want to install XP on my computer. I am currently running only Ubuntu, but I made another partition with enough place. But when I put in the installation CD for XP it will only let me format the entire HDD and install, or delete linux and install on my Ubuntu-partition (which the installer refer to as First Partition). How do I install on the empty partition?

It's not a normal Windows XP-installer though, the CD is a Toshiba CD which I got with my computer.

---

### Post by Therion on 2008-11-25
Windows does not like sharing.  Period.  That's problem one.  Problem two is that you are using a recovery CD.  Recovery CD's are not meant to "just" install Windows, they're used to restore your PC to an "out of the box condition".  That means Windows and all the bloatware that comes with your shiny new laptop when you take it out of the box and configured just as it came out of the box when you bought it new.  

In short, you don't get options with a recovery CD; you pop it in, boot the system and take what it gives you.

If you want to dual-boot Windows alongside Ubuntu, you'll need to reinstall Windows and then reinstall Ubuntu, or install Ubuntu using Wubi, which, frankly I don't really recommend, but it IS another install option.

---

### Post by taurus on 2008-11-25
What filesystem did you format that empty space to?  Make sure it is ntfs or windows won't detect it.  You can use gparted (install it with synaptic if you have not) and format that empty partition to ntfs.  Otherwise, can you post the output of this command from a terminal?

Applications -> Accessories -> Terminal
```
sudo fdisk -l
```
Another thing is once you install windows, you won't be able to boot Ubuntu again since windows will overwrite your MBR.  Therefore, you need to reinstall GRUB to MBR so you can boot both OSes.

[https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows](https://help.ubuntu.com/community/RecoveringUbuntuAfterInstallingWindows)

---

### Post by Patney on 2008-11-25
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x2ffa60bd

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          45       11986    95924115   83  Linux
/dev/sda2           14218       14593     3020220    5  Extended
/dev/sda3           11987       14217    17920507+   b  W95 FAT32
/dev/sda5           14218       14593     3020188+  82  Linux swap / Solaris

Partition table entries are not in disk order


It's in FAT32, but I can easily format it to NTFS when I use the Live CD, but not when I use the installed version.

Oh, and the only reason I'm installing XP is because I can't get the bridging-stuff to work in Ubuntu (just want to play xbox 360 live), and it's so easy in XP.

---

### Post by taurus on 2008-11-25
If you want to convert it from fat32/vfat to ntfs in Ubuntu, you want to make sure the partition, /dev/sda3, is not mounted first.  

If /dev/sda3 shows up with this command, 

```
df -h
```
then you can unmount it with

```
sudo umount /dev/sda3
df -h
```
Otherwise, use the LiveCD if you wish.

---

