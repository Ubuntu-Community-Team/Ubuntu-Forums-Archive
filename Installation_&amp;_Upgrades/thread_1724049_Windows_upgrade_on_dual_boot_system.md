---
title: "Windows upgrade on dual boot system"
date: 2011-04-07
forum: Installation &amp; Upgrades
---

### Post by DanielNewbie on 2011-04-07
I have a dual boot laptop (Acer Timeline 1830) working fine. I'm running Ubuntu 10.10 and Windows 7 Home Premium Edition. I need to upgrade Windows 7 Home Premium to Windows 7 Professional (Thats Winblows for ya.). My questions: Has anybody here done this upgrade, did it go seamlessly (Didn't destroy your master boot record, etc) and is there anything anything else i should know before doing this upgrade?

---

### Post by Quackers on 2011-04-07
Welcome to UF :-)
The upgrade is likely to over-write grub (in the mbr of the drive), making Ubuntu unbootable. This is easily repaired by re-installing grub from the live cd desktop.
Please find out the Ubuntu root partition number (it will be something like sda5 or something like that) by installing gparted to ubuntu, then running it.

---

### Post by DanielNewbie on 2011-04-08
Thanks Quackers

The Linux partition is sda5. Will I need this information to fix the mbr? Is there anything else I should know about reinstalling grub? I did my initial installation of 10.10 from a flash drive rather than a CD and I assume that I could reinstall grub from the flash just as easily.

---

### Post by Quackers on 2011-04-08
Yes, you can re-install grub from the usb.
You should boot from the usb and select "try ubuntu" and when the desktop loads, open up a terminal and copy/paste these commands, one line at a time and pressing enter after each line.
```
sudo mount /dev/sda5 /mnt
sudo grub-install --root-directory=/mnt /dev/sda
```
NOTE !!!
Those messages pre-suppose that sda5 is your Ubuntu root partition.

The process should report no errors.
You can then reboot, when Ubuntu should boot directly. If so, open a terminal and run ```
sudo update-grub
``` and as grub.cfg is run you should see the Windows Loader recognised. If so, reboot and you should get the grub menu appearing giving you the option of which OS to boot.

---

### Post by DanielNewbie on 2011-04-08
Thank you. I will let you know how it goes.

---

### Post by Quackers on 2011-04-08
Hokey cokey, good luck :-)

---

### Post by DanielNewbie on 2011-04-08
OK. I just did the upgrade from Winblows 7 Home Premium to Winblows 7 Professional on my dual-boot machine running Ubuntu 10.10. There was no problems with the upgrade and grub still allowed me to boot into Linux after the upgrade.
 
Qauckers
 
Even though I did not need to reinstall grub it was nice to be prepared for that nasty possibility. Better safe than sorry. Thanks again.

---

### Post by Quackers on 2011-04-08
That was quick :-)
Ok, but now you have the details, if you ever need them!

---

