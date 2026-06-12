---
title: "No Boot option in 'Side by Side' Install"
date: 2012-10-10
forum: Installation &amp; Upgrades
---

### Post by leonex on 2012-10-10
Hello guys,

I am a windows 7 (64 bit) user and wanted to try out Ubuntu on my laptop.

I downloaded Ubuntu Desktop 12.04LTS (64 bit) on my USB and and followed [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows) to create a bootable USB stick. Before starting my install i used Windows 7 disk management to shrink my hard-disk(500GB) to 400GB and left 100GB free.

After booting with USB stick I chose the side by side install and finished intalling Ubuntu.

After restart I a unable to see any boot option on my startup screen. I tried pressing shift and esc but only Windows 7 option shows up. I tried running 'Run Ubuntu from USB' and launched the 'Install Ubuntu' option again but it gave me the same results.

Could you guys help me with the above problem?

---

### Post by darkod on 2012-10-10
Did you try to boot it with the usb stick connected?

When you do a usb install the bootloader sometimes ends up to the usb by mistake.

---

### Post by kc1di on 2012-10-10
I'd go [here]("https://help.ubuntu.com/community/Boot-Repair") and download a copy of boot-repair and run that it will install grub2 to the MBR for you and if it does not work will give you a log file with the errors which you may post here and we could help further. 
good luck :)

---

### Post by leonex on 2012-10-10
I tried booting with USB->Boot with first hard Disk, but its jut going back to USB Boot Screen.

However, after the boot install I have finally got the boot options. Here is my paste bin script: [http://paste.ubuntu.com/1270888/](http://paste.ubuntu.com/1270888/)

However, it shows like 7 options with two Windows 7 option. Is that normal or something weird? I am still not sure where Ubuntu has been installed. I didn't have 2 disks before I installed Ubuntu. I have pasted my Disk management image:

[IMG]http://s7.postimage.org/n7ta160nv/Dsk.jpg[/IMG]

---

### Post by darkod on 2012-10-10
The grub2 detects boot files and makes the entries in the boot menu. You seem to have win7 boot files on both sda2 and sda3. Usually they would be only on sda2.

Try booting Win7 loader on /dev/sda2 first, if that works, use that one.
If it doesn't work, try the /dev/sda3.

You always had two disks only they set them up so that the second small one doesn't show in windows. Linux detects them all.

It sort of a small rapid disk (SSD) installed as an addition to the HDD.

PS. Your ubuntu is on sda6 (root) and sda5 (swap), as you can see.

---

### Post by leonex on 2012-10-10
Ok, the way i understand it, Linux uses 4+14.64GB on Disk 1 and 3.84GB on Disk 0 as a swap memory? If so how do I get Linus to use the 96.16GB on Disk 0.

---

### Post by darkod on 2012-10-10
No.

It uses the 96.16 GB as root partition, and the 3.84 GB as swap partition. There is no ubuntu on Disk1.

---

### Post by leonex on 2012-10-10
Got it. Thanks a lot for all the help darkod and kc1di.

---

