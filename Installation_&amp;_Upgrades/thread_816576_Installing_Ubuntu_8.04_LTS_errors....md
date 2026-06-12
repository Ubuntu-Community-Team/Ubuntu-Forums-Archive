---
title: "Installing Ubuntu 8.04 LTS errors..."
date: 2008-06-02
forum: Installation &amp; Upgrades
---

### Post by 95BlackGA on 2008-06-02
I just downloaded Ubuntu 8.04 LTS today, and I tried installing it. First I tried to install on my external drive that I am not using. That didn't work so, I decided I would partition my Windows XP drive, and do a dual boot on it. I successfully installed everything, but instead of booting right back into Ubuntu, I had to burn a file using Windows XP. After about 30 minutes of messing around on the net, I decided to get on Ubuntu to mess around with it. When trying to boot into Ubuntu, I get the following error : 

Kernel Panic - Not Syncing : VFS : Unable to mount root fs on unknown block. 

How do I fix this? I have read some places, but the fixes are difficult to understand for myself.

---

### Post by Pumalite on 2008-06-02
If you can boot a Live CD; post:
sudo fdisk -lu

---

### Post by 95BlackGA on 2008-06-02
Disk /dev/sda: 80.0 GB, 80026361856 bytes
255 heads, 63 sectors/track, 9729 cylinders, total 156301488 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0xeba9360d

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *          63    83425544    41712741    7  HPFS/NTFS
/dev/sda2        83425545   156296384    36435420    5  Extended
/dev/sda5        83425608   153276164    34925278+  83  Linux
/dev/sda6       153276228   156296384     1510078+  82  Linux swap / Solaris

Disk /dev/sdb: 60.0 GB, 60011642880 bytes
255 heads, 63 sectors/track, 7296 cylinders, total 117210240 sectors
Units = sectors of 1 * 512 = 512 bytes
Disk identifier: 0x8c87036a

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1              63   114190019    57094978+  83  Linux
/dev/sdb2       114190020   117210239     1510110    5  Extended
/dev/sdb5       114190083   117210239     1510078+  82  Linux swap / Solaris


I am trying to dual boot with the 80Gb drive. The 60Gb is the external that did not work.

---

### Post by Pumalite on 2008-06-03
Mount sda5:
sudo mkdir /media/sda5
sudo mount -t ext3 /dev/sda5 /media/sda5
Post:
cat /media/sda5/boot/grub/menu.lst

---

### Post by 95BlackGA on 2008-06-03
I got it installed and working. Although, I had to install a new card, and now it won't work. It boots normal, and then once the desktop is suppose to show, it just stays blank. I press the power button and the monitor shows the shut down log.

---

### Post by Pumalite on 2008-06-03
Follow my instructions on post # 4. Replace partitions accordingly.
You might have actually installed and have a graphics problem. In that case:
Ctrl+Alt+F1 to get command line, then:
sudo dpkg-reconfigure xserver-xorg
Choose vesa as the driver. Then:
startx

---

### Post by 95BlackGA on 2008-06-04
I am unable to do this, as I was very impatient when I installed my new video card. I tried reinstalling. Formatted the partition, and now during installs, I get a Sigkill, and the computer restarts. I am unable to do anything with Ubuntu, even run a LiveCD.

---

