---
title: "Local disk boot"
date: 2011-03-22
forum: Installation &amp; Upgrades
---

### Post by ylafont on 2011-03-22
[SIZE=3]I needed to replace my existing usb stick with a larger one. So, I formated a new USB stick with DOS and installed grub2. I copied my grub congiguration files files over to the new thumbdrive and now i cannot not boot the local DOS version installed on the USB drive.
I used to be able to boot the USB into dos by using 
 
INSMOD FAT
CHAINLOADER +1 
 
Now when I choose the menu, it just reloads grub. did i do something wrong? 
 
i installed grub on the sting with the following.
grub-install --root-directory=/media/dos7 /dev/sdb1 --force which i think was the command i used to installed it on the previous stick. 
 
I did create a second NTFS partion on the thumbdrive, but i do not htink that should be a problem since imake sure the correct partition is set to root with 
 
set root=(hd0,msdos1)
[/SIZE]

---

