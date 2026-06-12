---
title: "ubuntu and win7"
date: 2010-04-28
forum: Installation &amp; Upgrades
---

### Post by gis777 on 2010-04-28
Hi
I installed ubuntu 10.4 on flash drive but when I remove the flash drive and I want to boot the windows it doesn't work
 
I have to keep flash drive in order to boot the windows
 
How can I solve this problem? and how can I boot windows and ubuntu completly indipendent from each other?
 
Thanks

---

### Post by dentman on 2010-04-28
You messed up your boot on your C: drive.
Put your Win 7 disk in reboot and navigate to REPAIR and let it do it's thing.
 This SHOULD fix it.

:guitar:

---

### Post by bcbc on 2010-04-28
When you installed ubuntu on the flash drive (/dev/sdb) it installed grub to the master boot record on /dev/sda (your internal hard drive). Grub looks for the menu stored in your ubuntu installation - that's why you can only boot with the flash installed.

What you need to do first, is boot ubuntu with the flash in place, and install grub to the MBR on /dev/sdb. This will allow you to boot ubuntu later.

Then you need to replace the MBR on /dev/sda with the windows boot loader.

If you don't do it in this order, then you won't be able to boot ubuntu afterwards (you could repair with the install cd, but avoid if possible).

Step one: if you don't have a win7 repair disk, boot win7 and create one.
Step two: boot ubuntu and go to a command line and install grub to the MBR on your flash.
```
sudo grub-install /dev/sdb
```
Step three: remove flash, and boot from your win7 repair dvd and let it repair itself (will replace the bootloader). If you have issues, see the following [link]("http://ubuntuforums.org/showpost.php?p=6391959&postcount=1")
Step four: if you want to boot ubuntu, make sure you tell your computer to boot from the flash drive. Otherwise, it will boot windows.

Final note: I am assuming you have one internal drive and one flash drive. If you are not sure, run 
```
sudo fdisk -l
```
This will list your partitions and you can make sure that ubuntu is on /dev/sdb

---

### Post by wilee-nilee on 2010-04-28
Here is a link to the W7 recovery disc. This disc is just to get you to the recovery options, it is not a install disc.
[http://neosmart.net/blog/2009/windows-7-system-repair-discs/](http://neosmart.net/blog/2009/windows-7-system-repair-discs/)

---

### Post by presence1960 on 2010-12-05
Link works fine for me. You probably installed GRUB to internal disk rather than to the external disk. Just to be sure do this:

Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

---

