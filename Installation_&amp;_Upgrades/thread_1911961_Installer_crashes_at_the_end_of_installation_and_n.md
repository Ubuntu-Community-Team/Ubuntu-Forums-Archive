---
title: "Installer crashes at the end of installation and no boot then."
date: 2012-01-19
forum: Installation &amp; Upgrades
---

### Post by zeiz on 2012-01-19
I've been using Ubuntu for quite a while and even made 10.4 my main OS.
However I still need Windows for work so I placed it on another disk.
On the first disk along with Ubuntu I used to have up to 15 partitions to try various distros but then I deleted all those small partitions and I have now the following layout:
sda1-Suse11.4 (ext4)Primary 
sda2-FreeBSD (ufs)Primary   
sda3-Extented
sda5-swap                    
sda6-ubuntu 10.4 ext4       
sda7-empty, ext2           
sda8-empty, ext2            
sda4-storage(fat32) Primary

sdb1-windows7 32bit
sdb2-Extended
sdb3-swap
sdb4-Fedora ext4

Grub2 is on sda to boot everything.

I'm trying now to install Ubuntu 12.04(a) on empty partition sda8 to slowly migrate to next LTS release.
However installer crashes at the end with message "Migration of documets...failed.." and then "restart required" box appears. After reboot
(and updating of grub2) new installation boots but hangs in the middle.
I tried Mint 12 with perfectly the same result :)
Ubuntu 11.10 performs even worse: kernel panic in the middle of boot.

Didn't find anything about such problem. Any help appreciated.

---

