---
title: "Ubuntu mini.iso install onto a USB pen"
date: 2008-09-03
forum: Installation &amp; Upgrades
---

### Post by iharrold on 2008-09-03
So I am trying to install the Ubuntu 7.10 mini.iso located [here]("http://archive.ubuntu.com/ubuntu/dists/gutsy/main/installer-i386/current/images/netboot/mini.iso") onto a 1Gb USB pen.  I have successfully gotten the full install too work.  But it was too ballotted for my target pc -- Jetway J7F2WE1G5D (VIA C7 @ 1.5Ghz) with a 4Gb SD card as a hard drive via an SD to IDE converter.

Anyways... here's the steps I performed on an Ubuntu 7.10:
[PHP]
sudo umount /dev/sdb1
sudo fdisk /dev/sdb1
[/PHP]

Partitioned the USB drive by first "d" all the old partitions.
Then, "n" "p" "1" "<enter>" "<enter>" "a" "t" "6" "b" "w"

So it should end up as being full 1Gb USB pen partioned as FAT16 and bootable

Now to copy the ISO to the USB:
[PHP]sudo umount /dev/sdb1
sudo mkfs.vfat -F 32 -n miniU /dev/sdb1
sudo mount /dev/sdb1 ~/MountPoints/sdb1

mkdir miniCD
sudo mount mini.iso miniCD -o loop

cd miniCD
sudo cp -rf *.* ~/MountPoints/sdb1
cd ~/MountPoints/sdb1
sudo mv isolinux.cfg syslinux.cfg
sudo mv isolinux.bin syslinux.bin

cd ~
sudo umount /dev/sdb1
syslinux /dev/sdb1

sudo eject /dev/sdb[/PHP]

syslinux creates the ldlinux.sys file on the USB Pen.

The problem is when it boots of the USB pen... I get the start up screen shown [here]("http://www.psychocats.net/ubuntu/images/minimalhardy01.png")  however, anytime I enter anything at the boot prompt, the following message appears:
[B]
"boot: 
Could not find kernel image: linux
boot:"[/B]

What am I doing wrong or missing?  Thanks in advance.

---

### Post by kingfisher on 2008-10-22
Hi,

just had this problem too and found a solution.

> **iharrold said:**
> 
...
sudo mv isolinux.bin syslinux.bin
...
[B]
"boot: 
Could not find kernel image: linux
boot:"[/B]

What am I doing wrong or missing?  Thanks in advance.

Do NOT rename isolinux.bin - then it should work just fine.

Greetings,
Chris

---

