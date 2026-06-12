---
title: "Partitioner window empty on install"
date: 2010-01-16
forum: Installation &amp; Upgrades
---

### Post by cap10101 on 2010-01-16
I am struggling to figure out why I cannot get Ubuntu to install.  I boot my machine and run LiveCD and I can see me 36G raptor in GParted or partitioner or under Places but when i try to install 9.1, there is no drive after the keyboard layout in partitioner.  Can anyone please shed some light on this.  I have changed sata ports but that didnt help either.  I don't understand how it would be a driver issue if I can see the drive and partition it.

Any help would be appreciated!

---

### Post by cap10101 on 2010-01-17
Nobody??

---

### Post by pgj_69 on 2010-01-17
Having same problems here.
Jaunty - sees it
Kubuntu 9.1 - window empty
Ubuntu 9.1 - window empty
Ubuntu 9.1 64 - window empty

Have tried the acpi=force irqpoll options to no avail

Have tried to set the sata options in bios to each different settings without any luck.

Am able to see the drive with gparted livecd and able to partition it there - no luck on ubuntu install.

Am also able to see the drive with gparted booting ubuntu 64 live and can partition but no luck with seeing it on install.

Have tried changing the flags on drive thru gparted - boot, etc. without any luck.

fdisk -l - returns - Unable to open /dev/sda

Have not tried to install the server version which I have read a little about iSCSI ?

The attached screen shot should explain pretty well what is going on..

Any ideas, have been messing with for a day now, really confused....

---

### Post by garvinrick4 on 2010-01-17
> **pgj_69 said:**
> Having same problems here.
Jaunty - sees it
Kubuntu 9.1 - window empty
Ubuntu 9.1 - window empty
Ubuntu 9.1 64 - window empty

Have tried the acpi=force irqpoll options to no avail

Have tried to set the sata options in bios to each different settings without any luck.

Am able to see the drive with gparted livecd and able to partition it there - no luck on ubuntu install.

Am also able to see the drive with gparted booting ubuntu 64 live and can partition but no luck with seeing it on install.

Have tried changing the flags on drive thru gparted - boot, etc. without any luck.

fdisk -l - returns - Unable to open /dev/sda

Have not tried to install the server version which I have read a little about iSCSI ?

The attached screen shot should explain pretty well what is going on..

Any ideas, have been messing with for a day now, really confused....

I would say myself to go back into gparted and delete first two partitions and make it
one full partition and start over. Do not use the Manual but let gparted tell you what
it is going to do according to your instructions on size. It will put grub in right spot and
if you do not like its suggestions you can always use manual. Does not take that long to
reinstall and it will be right. Here is link if you need it. Good reading if you do not need it.
If you are to use Manual partition it is a must read.

[GRUB 2 bootloader - Full tutorial]("http://www.dedoimedo.com/computers/grub-2.html#mozTocId802943")

---

### Post by pgj_69 on 2010-01-17
The installer is not seeing the drive, that is, if it is gparted within the installer, it is not allowing a choice, manual, auto, etc. Maybe I am mis understanding your post. 

The screen shot I provided shows gparted which I am running from the livecd in the lower left, and on the right is the install, where the partitioner step of the install is coming up blank.

I just set the entire drive to unallocated space to see if it would be recognized during install and it is not. Then set the entire drive to an ext2 partition to see if it would be recognized then, which it is not. I previously tried an entire disk partition of fat32 to see if it would see the drive during install and that did not happen either. 

During install if the installer would see the drive I would happily let it do whatever it wanted, just to get grub or something installed, and then change it later.

Thank you for the article, is a good read, but - After manually installing grub as suggested, the installer still cannot see the drive to install - Output follows :

ubuntu@ubuntu:~$ sudo mount /dev/sda1 /mnt/
ubuntu@ubuntu:~$ sudo grub-install --root-directory=/mnt /dev/sda
Installation finished. No error reported.
This is the contents of the device map /mnt/boot/grub/device.map.
Check if this is correct or not. If any of the lines is incorrect,
fix it and re-run the script `grub-install'.

(fd0)	/dev/fd0
(hd0)	/dev/sda

---

### Post by garvinrick4 on 2010-01-17
Run Code:
                   sudo fdisk -l

that is small L 
What does it look like. Copy and paste here.

---

### Post by garvinrick4 on 2010-01-17
Reinstall from Scratch now that you have read gparted manual.

---

### Post by pgj_69 on 2010-01-17
Install from scratch?

Help me out on that one, I have been trying to install by selecting the install menu from the initial screen after you select the english language. I have added parameters using F6 as in acpi=force and irqpoll which all have ended up when the installer gets to the partitioner window it remains blank, no drive visible to select for partitioning.

Do you mean a minimalist install? or a command line install?

This has happened using three different install cd's, install works with 9.04, goes all the way thru.

It's a samsung hdd so am now going to try and use there tools and reset the drive to defaults, maybe something is goofy with the drive. Just seems odd I can boot into the live cd and select gparted from the menu, and see the drive, partition the drive and what not, but the installer will not see the drive.

I am also downloading the server version to try and install as I have read this might solve this problem because of iSCSI?

Thanks

---

### Post by pgj_69 on 2010-01-17
I could just upgrade the 9.04, but was wanting a clean install on this new pc.

---

### Post by pgj_69 on 2010-01-18
FIXED!!!

The following is what I did all at one time, so unsure as to what exactly it was, but the system installed fine, and the drive showed in the partitioner portion of the install and everything went well.

1) Downloaded the Samsung hdd utility and booted into it and ran the diagnostics. Did a low level format including removal of any MBR present using there software/utility.

2) Pulled the battery on the motherboard and clearing all memory and setting it to factory default.

3) In a weird way I am leaning to this one - switched to a usb stick install instead of the cd. Made the start-up disk with the usb start-up disk program from xubuntu which I use on my laptop. Why do I think so? eliminates any io errors from the cdrom drive, which did check out fine, but.......

Thanks.

---

### Post by audiomick on 2010-01-18
There are fairly regular posts from people who have similar problems. The advice generally is to try the alternate CD, which uses a different partitioning tool, and seems to have less problems. This worked for me. Anyway, you have yours solved now, so that is good.

Interesting that you say you are using a Samsung HD. I am too, also in my NAS, and am determined never to buy that brand again. They work, but I had issues with both machines having trouble finding the disks.

---

