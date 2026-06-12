---
title: "Mount LVM file system"
date: 2007-04-30
forum: Installation &amp; Upgrades
---

### Post by dartkel on 2007-04-30
I have just moved from Fedora core 6 to Ubuntu. I have two hard discs - one with the Ubuntu which works fine. The other has much of my old data under Fedora (which I cannot boot). I have amended my fstab file successfully to access hdc1 but this is just the boot sector.
I need to access hdc2 which has my old data. This is shown as 8e Linux LVM and I cannot get the fstab file to recognise this fs.

Any ideas on how I can mount hdc2 with LVM?

---

### Post by JohnnyKimble on 2007-05-04
I've not much experience with LVM, but I did have a similar problem to you, so here's how I solved it (Ubuntu 7.04 server).

1. Install lvm2:

sudo apt-get install lvm2
sudo cp -r /lib/lvm-200/ /lib/lvm-0

2. Take note of the LV Name for the volume you want to mount from the output of the following command (/dev/VolGroup00/LogVol00 in my case):

sudo lvdisplay

3. Run the following commands to mount the logical volume:

sudo modprobe dm-mod
sudo vgchange -ay
sudo mkdir /mnt/old_hd
sudo mount /dev/VolGroup00/LogVol00 /mnt/old_hd

Worked for me!

HTH,
JK

---

### Post by dartkel on 2007-05-05
Thanks, I will try and let you know.

---

