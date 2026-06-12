---
title: "Firmware install, Ubuntu-Mate 20.04 ,Flatpak"
date: 2020-05-14
forum: Installation &amp; Upgrades
---

### Post by dieter-erich on 2020-05-14
Hi,
  Ubuntu-20.04 now features System Tools > Firmware. When I klick it I get a list of newer firmware that might be installed but no hint how to do this. Browsing the net I found that flatpak can do this. So, I installed flatpak and flatpak-gui. However, neither shows up in the menu. I thus started flatpak from the terminal and get a number of options but do not have any clue how to install the firmware listed above. In particular, I am hoping that the two cameras of my Lenovo think pad might work after the firmware install. Can anybody please help! I found a post here but it was not very helpful, I simply do not understand how to do it.
Thanks, DE

---

### Post by oldfred on 2020-05-14
Grub has a menu item, but you can do updates from command line.
Only some newer systems are supported so far.

Fwupd 1.4 brings with it many improvements  April 20, 2020
[https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released](https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released)
UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)
sudo fwupdmgr get-devices
sudo fwupdmgr get-updates
sudo fwupdmgr update

---

### Post by Dennis N on 2020-05-14
Looking at Firmware (gnome-firmware), if you select device on first window then click on 'Show Releases', the next screen allows selection of a specific firmware version, and the 'Install Upgrade' button. 

You don't necessarily need the flatpak version of this, as this application is also in the Ubuntu repository.

---

### Post by dieter-erich on 2020-05-15
THANKS,  "gnome-firmware" brings up a window, I can select device but "Show Release" is greyed out and I cannot select anything. I also tried to start as sudo but the result is the same: selections are not active

---

### Post by dieter-erich on 2020-05-15
Thanks, But it first says that there is an update and when I want to see it says there is none (see boldface):

sudo fwupdmgr get-devices
80XF
&#9474;
&#9500;&#9472;DF4128:
&#9474;     Device ID:           60aad756932e96a01edac5ef6a20810ea92e8afd
&#9474;     Current version:     0x3230343037332020
&#9474;     Vendor:              EMMC:0x000045
&#9474;     Serial Number:       0x9c561f01
&#9474;     GUIDs:               e0c07333-957a-516d-8427-0dcb6435dcc2 &#8592; EMMC\DF4128
&#9474;                          add792f2-7053-5638-80e7-20987fd16769 &#8592; EMMC\0069&0256
&#9474;                          46bd104a-9e64-5135-860a-e7ba831ce00d &#8592; EMMC\0069&0256&DF4128
&#9474;     Device Flags:        • Internal device
&#9474;                          •** Updatable**
&#9474;   
&#9492;&#9472;System Firmware:
      Device ID:           4c0caf5406adf77978f5732a407cde4ad36f4f25
      Current version:     0.0.214
      Minimum Version:     0.0.90
      Vendor:              LENOVO (DMI:LENOVO)
      GUID:                4ec947ca-706d-48ad-981d-9511704e807c
      Device Flags:        • Internal device
                          ** • Updatable**
                           • Requires AC power
                           • Needs a reboot after installation
                           • Cryptographic hash verification is available
                           • Device is usable for the duration of the update
    
blaas@ubuntu:~$ sudo fwupdmgr get-updates
• [B]DF4128 has no available firmware updates
• System Firmware has no available firmware updates
No updatable devices[/B]
blaas@ubuntu:~$ sudo fwupdmgr get-updates
• DF4128 has no available firmware updates
• System Firmware has no available firmware updates
No updatable devices
blaas@ubuntu:~$ sudo fwupdmgr update
• DF4128 has no available firmware updates
• System Firmware has no available firmware updates
No updatable devices
blaas@ubuntu:~$ 





> **oldfred said:**
> Grub has a menu item, but you can do updates from command line.
Only some newer systems are supported so far.

Fwupd 1.4 brings with it many improvements  April 20, 2020
[https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released](https://www.phoronix.com/scan.php?page=news_item&px=Fwupd-1.4-Released)
UEFI/BIOS updates brand model list  for Dell with (uefi >= 0.6.2 & dell >= 0.7.3) 
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist)
fwupx64.efi
[https://github.com/rhboot/fwupdate/blob/master/README.md](https://github.com/rhboot/fwupdate/blob/master/README.md)
[https://fwupd.org/lvfs/devicelist](https://fwupd.org/lvfs/devicelist) & 
[https://fwupd.org/vendorlist](https://fwupd.org/vendorlist)
sudo fwupdmgr get-devices
sudo fwupdmgr get-updates
sudo fwupdmgr update

---

### Post by oldfred on 2020-05-15
Only some Lenovo's are on the list.
It may be telling you Lenovo has an update, but Lenovo has not uploaded it, so it can be updated directly.

Check your version and go to Lenovo's site to see if an update is available.
Also check model and list of models available:
[https://fwupd.org/lvfs/devices/](https://fwupd.org/lvfs/devices/)

My system shows Gigabyte motherboard, Samsung SSD & HDD as updateable.
But this is what I get.
```
fred@Z170N-focal:~$ sudo fwupdmgr get-updates
&#8226; HGST HTS721010A9E630 has no available firmware updates
&#8226; Samsung SSD 970 EVO Plus 500GB has no available firmware updates
&#8226; System Firmware has no available firmware updates
No updatable devices

```

---

### Post by dieter-erich on 2020-05-16
Thanks! I understand! Could not find anything for my miix 320-10icre there. So, I shall have to continue living without the two integrated cameras, even after updating to 20.04!

---

