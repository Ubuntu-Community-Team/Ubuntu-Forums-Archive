---
title: "modify menu grub2"
date: 2010-03-25
forum: Installation &amp; Upgrades
---

### Post by davidtuti on 2010-03-25
Hi,

I have in my computer: kubuntu, windows xp and windows 7. The three operative systems are in the same disk.
I boot with Grub2 and I have the option of boot with windows xp, when I select windows xp other menu appears and I can select windows 7 or older version where is windows xp.

I would like that in the principal menu of my grub2 appears the option windows 7 and windows xp without have to enter in the other menu. That is possible? How could I do this?

Many thanks and sorry for my english!

---

### Post by andrewthomas on 2010-03-25
It may help if you post some more info. Try this info script
 
Boot Info Script courtesy of forum member meierfra
Page with instructions and download:
[[COLOR=#444444]http://bootinfoscript.sourceforge.net/[/COLOR]]("http://bootinfoscript.sourceforge.net/")
Be sure to highlight and use code tags (#) to make it easier to read when you post the results.txt.

---

### Post by davidtuti on 2010-03-25
Many thanks,
I attach the file of the result of the script.

---

### Post by wkulecz on 2010-03-25
Maybe the grub2 docs are catching up with the needs....

Best I've found yet:
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)

---

### Post by andrewthomas on 2010-03-25
Win 7  wrote its boot  loader to the XP partition.


I have adapted the following from 

[http://ubuntuforums.org/showthread.php?t=1411495](http://ubuntuforums.org/showthread.php?t=1411495)

especially 

[http://ubuntuforums.org/showpost.php?p=8861307&postcount=23](http://ubuntuforums.org/showpost.php?p=8861307&postcount=23)

add an entry in/etc/grub.d/40_custom 
```
menuentry "Microsoft Windows 7 (on /dev/sda6)" {
insmod ntfs
set root=(hd0,6)
search --no-floppy --fs-uuid --set 84700C5B700C55F8
chainloader +1
}
```[B]Step 2 Copy the file  bootmgr and the directory Boot from the XP   partition to the Win_7 partition 

[/B]```
cd /mnt
sudo mkdir 1 6  
sudo mount /dev/sda1 1
sudo mount /dev/sda5 5
sudo cp -r 1/bootmgr 1/Boot 5
```Once you succesfully copied "bootmgr" and  "Boot":

[B]Step 3  Edit the bcd on your Win 7  partition.
I don't know what to put here. If you read the post through you may be able to adapt it for your circumstances
[/B]

---

### Post by oldfred on 2010-03-25
meierfra, who wrote the boot_info script is one of two or three who can get windows to boot from an extended partition. So the instructions and links in andrewthomas post should work. Your windows 7 is in an extended partition which MS says can only be installed/booted thru a primary partition.

To understand a little more about windows booting - This discusses Vista but 7 is the same for booting.
Multibooters, Pictures here worth 1000+ words
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)

---

