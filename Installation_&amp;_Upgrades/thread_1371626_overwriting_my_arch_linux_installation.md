---
title: "overwriting my arch linux installation"
date: 2010-01-03
forum: Installation &amp; Upgrades
---

### Post by sneilan on 2010-01-03
I want to move back to ubuntu again. Arch linux is not an operating system for those who like progress in computing. It's for those who like to forever muddle around with packages and configurations that have already been figured out by someone else. People don't really build on each other's work in the arch linux environment as they do on ubuntu.

My opinions aside, I'm wondering how I might install ubuntu 9.10 over my arch linux install & maintain my /home partition. I have two hard drives. arch is on the secondary drive & winblows is on the primary drive. I boot onto the windows drive & since grub is on the winblows drive, I can boot off the secondary drive with nothing but arch on it.

Again, I would like to install ubuntu on this secondary drive and maintain the /home partition.

**output from df while in arch, not having mounted the winblows drive:**
sneilan@sneilan-desktop:~$ df
Filesystem           1K-blocks      Used Available Use% Mounted on
/dev/sdb3             30723344  11726064  18997280  39% /
none                   2028928       212   2028716   1% /dev
none                   2028928       272   2028656   1% /dev/shm
/dev/sdb1                38888     10949     25931  30% /boot
/dev/sdb4            453404716  97691892 355712824  22% /home

----

**/boot/grub/menu.lst in the arch drive**
# Config file for GRUB - The GNU GRand Unified Bootloader                                                  
# /boot/grub/menu.lst                                                                                      

# DEVICE NAME CONVERSIONS 
#                         
#  Linux           Grub   
# -------------------------
#  /dev/fd0        (fd0)   
#  /dev/sda        (hd0)   
#  /dev/sdb2       (hd1,1) 
#  /dev/sda3       (hd0,2) 
#                          

#  FRAMEBUFFER RESOLUTION SETTINGS
#     +-------------------------------------------------+
#          | 640x480    800x600    1024x768   1280x1024  
#      ----+-------------------------------------------- 
#      256 | 0x301=769  0x303=771  0x305=773   0x307=775 
#      32K | 0x310=784  0x313=787  0x316=790   0x319=793 
#      64K | 0x311=785  0x314=788  0x317=791   0x31A=794 
#      16M | 0x312=786  0x315=789  0x318=792   0x31B=795 
#     +-------------------------------------------------+
#  for more details and different resolutions see        
#  [http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution](http://wiki.archlinux.org/index.php/GRUB#Framebuffer_Resolution) 

# general configuration:
timeout   5
default   0
color light-blue/black light-cyan/blue

# boot sections follow
# each is implicitly numbered from 0 in the order of appearance below
#
# TIP: If you want a 1024x768 framebuffer, add "vga=773" to your kernel line.
#
#-*

# (0) Arch Linux
title  Arch Linux
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/724c9474-8de8-4d9c-b798-4783e19e3353 ro
initrd /kernel26.img

# (1) Arch Linux
title  Arch Linux Fallback
root   (hd0,0)
kernel /vmlinuz26 root=/dev/disk/by-uuid/724c9474-8de8-4d9c-b798-4783e19e3353 ro
initrd /kernel26-fallback.img

# (2) Windows
#title Windows
#rootnoverify (hd0,0)
#makeactive
#chainloader +1

---

### Post by zvacet on 2010-01-04
Install Ubuntu on top of Arch and **do not format home partition**.

---

### Post by nothingspecial on 2010-01-04
When you get to the partitioning bit of the install, choose the manual (advanced) option.

Click on the arch partition and click change (or modify or something like that). Choose to use it as an ext4 file system, set the mount point as / and check the format box.

Then choose your home partition (/dev/sdb4) and choose use as ext3 journaling file system (or whatever file system it is) set the mountpoint as /home but **_[SIZE="3"][COLOR="Red"]DO NOT CHECK THE FORMAT BOX[/COLOR][/SIZE]_**

---

### Post by sneilan on 2010-01-04
Got it. Thank you both very much for your time and advice! I will respond with how it goes shortly.

---

### Post by sneilan on 2010-01-04
Actually, I do have one question:

Can I get rid of the /boot partition if / is going to be used for ubuntu?

---

### Post by zvacet on 2010-01-04
Yes,you can remove boot partition if you want,but in that case grub will be on MBR.

---

### Post by sneilan on 2010-01-04
got it. I guess I'll just leave the grub settings alone in the last screen which should install grub whether or not it's on there.

---

