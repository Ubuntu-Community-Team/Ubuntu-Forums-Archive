---
title: "Need help to boot !!"
date: 2012-07-01
forum: Installation &amp; Upgrades
---

### Post by Z3Th on 2012-07-01
Hi everyone;

&#304; am trying to install Ubuntu 12.04 LTS to my desktop. First i tried to boot with a usb. I've Sony USB 3.0. I used Unetbootin then Universal USB installer then Flashboot programs. All failed :(

After that i burned a cd. But it has just a black screen when restart my pc.

Unetbootin  -->  i can see instal menu when i choose install or try ubuntu fisrt a black screen then menu coming back again and i cant do anything in that phase.

Universal Usb Installer --> i can choose install ubuntu then too many codes are passing in my screen then stopping. Above last line it is writing something with ehci_hcd and last line is "Supports vblank timestamp caching Rev 1 (i dont remember exactly :( )

Flashboot  --> first gived error about ui keyword i deleted it then it gived error about "keyword gfx" i tried to type help and enter enter didnt do anything 

I thought maybe download is broken. I reinstall ISO file form Ubuntu.com and checked md5sum. it is correct. retried still samethings.

My desktop has i7-2600k cpu, GTX560 Ti, 6gb ram ddr3 1333, MSI P67A-GD80 (B3) Intel P67 Motherboard


(btw sorry for my english)

---

### Post by darkod on 2012-07-01
With a nvidia card you might need to use the nomodeset parameter to boot into live mode (and later into the installation for the first time, until you activate the correct driver).

Here you have instructions how to boot with the cd with nomodeset activated:
[http://ubuntuforums.org/showpost.php?p=10069997&postcount=1](http://ubuntuforums.org/showpost.php?p=10069997&postcount=1)

---

### Post by Z3Th on 2012-07-01
Thank you man :) Nomodeset solved my problem :) (i've spent nearly 2 days before posting)

---

