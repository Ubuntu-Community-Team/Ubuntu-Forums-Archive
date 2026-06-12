---
title: "ASUS P5P55D-E LX Mobo Can't install Ubuntu 10.04 Lucid Lynx 32-bit"
date: 2010-10-20
forum: Installation &amp; Upgrades
---

### Post by travellersolo on 2010-10-20
I just purchased a new PC with the following specs:

Intel Core i5-760
ASUS P5P55D-E LX (S1156 mobo)
Sapphire HD 5750 Vapor-X 1GB Video Card
Samsung 1TB HDD
Corsair DDR3 PC1333 Gaming RAM - 2x2GB
DVD: Samsung DVD burner (internal)

I have made several trials to install Lucid Lynx but all failed:

1. Installed Windows 7 64-bit, hdd formatted as NTFS and ext3, then trying to install Lucid Lynx 32-bit : failed.

2. Installed Windows XP 32-bit, hdd formatted as FAT32, then trying to install Lucid Lynx 32-bit : failed.

3. Trying to install Lucid Lynx 32-bit with a clean hdd formatted as FAT32: failed.

In all the scenarios above, I have tried using Ubuntu installers on CD, DVD, or USB. on CD and DVD, the process always stopped after the Ubuntu logo screen, not even reached the langauage selection screen. 

On USB, with Legacy set to On in the BIOS, it did run and started by the option screen where we get to choose booting from the usb, or booting from hdd, or memory test, etc., but after choosing the booting from usb (and then hdd also) option, the process also stopped after the Ubuntu logo screen.

I have experience dual booting Windows XP with Lucid Lynx on an older system, so I'm not completely new in this. I'd like to know what actually went wrong?

Is ASUS P5P55D-E LX really having problem with Ubuntu?

---

### Post by elton1984 on 2010-10-31
Use FAT32 to install Ubuntu? Is it possible? 
And maybe you can try to use 64bit?

---

### Post by jrev on 2010-10-31
Hi, If you want to format you HD before installing use the Ubuntu CD-live and **gparted** :
make a primary partition and a /home partition file system = ext 4
then start the installation.
If you want to keep Windows it's a little bit more complicated...:)

---

