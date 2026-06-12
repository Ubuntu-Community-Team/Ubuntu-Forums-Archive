---
title: "Unable to Install GRUB in /dev/sda"
date: 2011-05-03
forum: Installation &amp; Upgrades
---

### Post by DeXeS5689 on 2011-05-03
Ok so recently a friend recommended I try Ubuntu.  So I downloaded and ripped 11.04. Reset PC went to install and got to  about 95% then got an error that said "Unable to Install GRUB in  /dev/sda" then downloaded 10.04 LTS and got same issue along with 10.01  (friends disc) and same issue. I have tried both 64 and 32bit, have  tried iso and usb. I was able to install it on an older machine of mine  and enjoying it. But I really want it on my main machine. Here are the  specs of my main.
 MOBO = X58 SATA 6Gb/s USB 3.0 ATX Intel Motherboard
 CPU = Intel Core i7-980X Extreme Edition Gulftown 3.33GHz LGA 1366 130W Six-Core Desktop Processor BX80613I7980X
 HDD = 4(four)-Western Digital VelociRaptor WD3000HLFS 300GB 10000 RPM SATA 3.0Gb/s 3.5" Internal Hard Drive Raid 0
 RAM = CORSAIR DOMINATOR GT 6GB (3 x 2GB) 240-Pin DDR3 SDRAM DDR3 2000 (PC3 16000) Desktop Memory Model CMG6GX3M3A2000C8
 DVD = LG Black 10X Blu-ray Burner
 GPU = 2(two) XFX HD-597A-CNB9 Radeon HD 5970 Black Edition 2GB 512  (256 x 2)-bit GDDR5 PCI Express 2.1 x16 HDCP Setup in CrossFireX
 PSU = ULTRA X4 1600W POWER SUPPLY MODULAR
 and here are links of the screens showing which steps Ive taken for basic install and what result is.
 [http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-1.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-1.png)
[http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-2.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-2.png)
[http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-3.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-3.png)
[http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-4.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-4.png)
[http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-5.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-5.png)
[http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-6.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-6.png)
[http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-7.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-7.png)
[http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-8.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-8.png)
[http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-9.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-9.png)
 Number 8 and 9 are the issue and choices after words. I am unable to  select any choice on step nine. when i hit OK it wont do anything.
 I hope this is all enough info and would love any help that is given.  My friend who is an Ubuntu user is throwing his hands in the air at  this point lol.
 While doing research I found a few ppl with similar issues. And one  person said when he made his own /root and /home partitions it worked. I  get similar issue even if I take those steps.
Ive collected as much info for you guys as I can think of if you need more info plz let me know.
Im sure it has something to do with either my raid (which I cant see how  because I have taken my HDD out of raid and still had same issue) or  some kind of hardware that is not meshing well with Ubuntu.
Please help.

---

### Post by alanfwiliams on 2011-05-03
if you have a windows partition you can try and install ubuntu using wubi this will let you install ubuntu throug windows on any partion you want. you can also use it to uninstall it if you dont like what you see. this is the link to wubi [http://www.ubuntu.com/download/ubuntu/windows-installer](http://www.ubuntu.com/download/ubuntu/windows-installer) oh and have your iso loaded so it wont have to download the os again

---

### Post by alanfwiliams on 2011-05-03
oh i just checked your screenshots man you have to chose sda1 as the drive to have the boot loader on 
hope im correct im new to

---

### Post by dino99 on 2011-05-03
> **alanfwiliams said:**
> oh i just checked your screenshots man you have to chose sda1 as the drive to have the boot loader on 
hope im correct im new to

NO the good place is sda not sda1

---

### Post by dino99 on 2011-05-03
> **DeXeS5689 said:**
> 

[http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-3.png](http://i1225.photobucket.com/albums/ee398/dexes812/Screenshot-3.png)

Please help.

this screenshot shows a raid0, that might be the problem, remove it first (before formatting) from the livecd open a terminal and run:

sudo dmraid -rE

then follow this howto to install:

[http://ubuntuforums.org/showpost.php?p=10161428&postcount=2](http://ubuntuforums.org/showpost.php?p=10161428&postcount=2)

---

