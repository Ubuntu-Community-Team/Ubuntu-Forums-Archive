---
title: "Grub doesn't load on startup - must use Live CD"
date: 2010-03-12
forum: Installation &amp; Upgrades
---

### Post by ShadowsOfSilver on 2010-03-12
Help? I can't use ubuntu without the Live CD, and I don't have any other operating systems...


I have Grub 2 and Ubuntu 9.10. if any more information is needed, I will gladly add it.

---

### Post by presence1960 on 2010-03-12
Let's see what you have on that machine. Let's get a better look at your setup & boot process. Boot the Ubuntu Live CD/USB. Choose "try ubuntu without any changes", when the desktop loads come back here and do the following:

1. Download the boot info script. There is a link in my signature.
2. Once downloaded move the boot info script to the desktop.
3. Open a terminal and run the command ```
sudo bash ~/Desktop/boot_info_script*.sh
```

  This will create a RESULTS.txt file on the desktop. Paste the entire contents of that file back here. Once pasted highlight all text and click the # sign on the toolbar to place code tags around the text. 

See [here]("http://bootinfoscript.sourceforge.net/") for more info on the boot info script.

Above link is to meierfra's Sourceforge web page.

---

### Post by ShadowsOfSilver on 2010-03-13
Okay, I did that. I think my grub.cfg file needs to be edited at a certain part, it needs a non-zero digit in that spot. But here are the results.


```
                Boot Info Script 0.55    dated February 15th, 2010                    

============================= Boot Info Summary: ==============================


=========================== Drive/Partition Info: =============================

no valid partition table found
blkid -c /dev/null: ____________________________________________________________

Device           UUID                                   TYPE       LABEL                         

/dev/loop0                                              squashfs                                 

============================ "mount | grep ^/dev  output: ===========================

Device           Mount_Point              Type       Options

aufs             /                        aufs       (rw)
/dev/sr0         /cdrom                   iso9660    (rw)
/dev/loop0       /rofs                    squashfs   (rw)

=======Devices which don't seem to have a corresponding hard drive==============

no block devices found 
```

---

### Post by presence1960 on 2010-03-13
Your hard disk is not being recognized. Check in BIOS and make sure your hard disk is recognized by BIOS.

---

