---
title: "Hp mini 311 wifi issue"
date: 2011-03-05
forum: Installation &amp; Upgrades
---

### Post by Gizmou on 2011-03-05
Hi,
 
*I am experiencing wifi issues - my wifi button is red and I can't connect to internet.*
 
*At first following these instructions - [http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9905937&postcount=2](http://ubuntu-ky.ubuntuforums.org/showpost.php?p=9905937&postcount=2)*
 
*everything worked.Unfortunately,additional drivers showed that I still don't have broadcom b43 wireless driver and broadcom sta propriety wireless driver installed.So I thought that this needs to be resolved,even though I had a wifi connection at that time. I installed the first option(b43 wireless driver) through wifi(which at that moment worked),as I don't have wired.After restart the wifi is now not working at all and even after trying the method which worked previously again(thought it might resolve the issue) - it seems it doesn't work.*
 
*Is there chances to revert to the previous drivers or somehow get my wifi working once more?*
 
*I have a usb and internet accces on my desktop pc so I could transfer some files if needed to get my wifi working.*
 
*I hope someone will help,thanks*

---

### Post by Gizmou on 2011-03-05
Anybody has any clues? 
 
Would appreciate if mod would move this topic to - networking section

EDIT : After much of research,decided to reinstall the system and use the instructions I used before,which now worked and I have a working wifi.
I still see the b43 driver and broadcom sta driver package under addition drivers,but I am not sure whether it's possible to do anything about it.
Regarding the instructions about setting up wifi if any body else has this issue -THANKS TO CHILI555  > The driver b43 is  installed by default, however, the driver requires proprietary firmware  to work properly. The firmware needs to be installed now.

May I assume you have another computer and a USB drive in order to grab  some files? First get these files and transfer them to your desktop. [http://downloads.openwrt.org/sources...a-3.130.20.0.o]("http://downloads.openwrt.org/sources/wl_apsta-3.130.20.0.o") and [http://mirror2.openwrt.org/sources/b...0.10.5.tar.bz2]("http://mirror2.openwrt.org/sources/broadcom-wl-4.150.10.5.tar.bz2")

Right-click the second one and select 'Extract here.'

Also grab this file: [http://archive.ubuntu.com/ubuntu/poo...uild1_i386.deb]("http://archive.ubuntu.com/ubuntu/pool/main/b/b43-fwcutter/b43-fwcutter_012-1build1_i386.deb")

Open Applications > Accessories > Terminal and enter these commands in order, one at a time.     

Code:

     cd ~/Desktop sudo dpkg -i b43-fwcutter* 
 It will try and fail to go out on the internet to grab the firmware. Don't worry, we will point it at the firmware ahead. 

Code: 
sudo b43-fwcutter -w /lib/firmware wl_apsta-3.130.20.0.o 
sudo b43-fwcutter --unsupported -w /lib/firmware broadcom-wl-4.150.10.5/driver/wl_apsta_mimo.o 
sudo chmod o+rx /lib/firmware/b43


Reboot and let us know if your wireless is now working.


Worked For Me.

---

