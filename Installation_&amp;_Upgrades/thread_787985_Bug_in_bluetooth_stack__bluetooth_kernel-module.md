---
title: "Bug in bluetooth stack / bluetooth kernel-module?"
date: 2008-05-09
forum: Installation &amp; Upgrades
---

### Post by TheMagican on 2008-05-09
Hi,

I've recently updated to kubuntu hardy. After this update, the sync with my PocketPC (Windows Mobile 5) won't work any more. Every time I try to establish the bluetooth-connection with my laptop, the complete PC freezes after a few seconds and I can only press the power-button to turn it off.
I don't think that it is a KDE / bluez / synce problem as booting with the old kernel, which is still installed on my laptop, the pairing and synchronizing works fine. Using the new 2.6.24 kernel, my laptop freezes every time I try to establish the BT-ActiveSync-connection - even if I don't activate the BT-funtion for ActiveSync with "dund --listen --activesync --msdun call dun".
With other BT-devices everything works fine. I've got a Lego NXT-Brick whose programms are transferred by bluetooth and this connection works...
Does anybody have an idea, what could be the exact reason for this? I'm not that familiar with kernel-issues so, as the bluetooth-functionality is done by a kernel module: is there a way to use the bluetooth-module from the 2.6.22 kernel (which worked great for me) with the new 2.6.24 kernel? If yes, how can that be done?


Thanks a lot
Andy

---

### Post by TheMagican on 2008-05-10
Hi,

I've solved the problem myself ;)
Refering to the old synce-wiki ([http://www.synce.org/oldwiki/index.php/Connecting_your_Windows_Mobile_2005_device_via_Bluetooth_using_Bluetooth](http://www.synce.org/oldwiki/index.php/Connecting_your_Windows_Mobile_2005_device_via_Bluetooth_using_Bluetooth)) it is (sometimes) necessary to create some devices, which didn't exist on my upgradeded Ubuntu. After I've executed the few lines to create the devices, everything worked fine.


Greets
Andy

---

### Post by zuccster on 2008-05-27
Hi,

I have the same issue on both my laptop and desktop running Hardy.  Creating the device nodes manually didn't help.  Nothing in any log that I can find.  I'll try an older kernel and report back.

Zucc

---

