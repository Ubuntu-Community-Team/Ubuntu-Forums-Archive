---
title: "ubuntu usb maker.. its a joke?"
date: 2010-01-21
forum: Installation &amp; Upgrades
---

### Post by auni418 on 2010-01-21
dont get me wrong i am happy with my Ubuntu until i want to use the usb maker thing.. i got netbook remix and now i want to install it.. i use one of my usb drives.. BUT.. ubuntu usbmaker dont let me formate it.. i have used gparted, yes with ntfstools and tried formate it in every possible way with and without flags and **** and usbmaker dont seem to accept it however.. the usbmaker cant do ****.. it tells me it cant use the stick** and then gives me everything from 1 - 2 partitions.. i have backtracked this problem as far as i can it i dont get it..

unetbootin makes it work great! but why shold i have to go so far as unetbootin to get things done? is usbmaker the most unuseless pice of software or what.. ?

what did i miss? what did i do wrong? any ideas?

yes i have used the same stick to install win7 sometime ago..

---

### Post by Yogotiss on 2010-01-21
When using gparted... Do you unmount the drive first? If not you have to do that first in order to format the drive then use **[COLOR=Blue]System[/COLOR]**>>[COLOR=Blue]**Administration**[/COLOR]>>**[COLOR=Blue]USB Start Up Disk Creator[/COLOR]**

---

### Post by auni418 on 2010-01-21
i have done that too.. no progress..

i can formate it in many different formats in gparted.. but usbmaker cant handle any of them.. not even fat 16,ext2 or ntfs.. do i have to use som special flag? i have tried boot asand whit out boot.. all the same.. the stick i got is a scandisk qruzer.. acctualy 2 of them.. 2 & 8 gb and its all the same..

---

### Post by djchandler on 2010-01-21
> **auni418 said:**
> i have done that too.. no progress..

i can formate it in many different formats in gparted.. but usbmaker cant handle any of them.. not even fat 16,ext2 or ntfs.. do i have to use som special flag? i have tried boot asand whit out boot.. all the same.. the stick i got is a scandisk qruzer.. acctualy 2 of them.. 2 & 8 gb and its all the same..

I've over thought things like this before myself with Linux. Put the USB thumb drives back the way they were before you started partitioning and formatting.

Fat 32 is the preferred format, but it should also work in Fat 16 if < 2GB. Try the 2GB again as a single partition only, format as Fat 16 ms-dos compatible.

After that, safely remove the usb drive, start USB Startup Disk Creator, and don't put in the usb drive again until it asks for it. The usb drive can't be a mounted volume for it to work.

---

### Post by C.S.Cameron on 2010-01-22
I've had problems with usb-creator before, it generally works best if the md5sum for the iso is correct.
I generally use boot and lba flags, but lba is not always required.
I have best success installing directly after erasing the data from an unetbootin install.
I haven't had much success at all using u-c as a disk formatter.

---

### Post by Handssolow on 2010-01-22
Check out the information below if you want to refresh your USB stick. When removing partitions and formatting I disconnect the hard drive and use a live CD rather than running from a hard drive to avoid any risk of getting the drive letters wrong. For reasons which escape me I then use XP to format the flash drive. I once cocked things up ?lost MDR and had to do a low level format using perhaps the "Ulimate Boot CD".

[http://www.pendrivelinux.com/restoring-your-usb-key-partition/](http://www.pendrivelinux.com/restoring-your-usb-key-partition/)

Edit:I've also successfully used the HP USB Disk Storage Format Tool mentioned in the above link.

---

### Post by Herman on 2010-01-22
I have recently had a bad experience with the Ubuntu USB Startup Disk Creator too.

I'm travelling and installing Ubuntu for family and friends as I go and I needed to use USB Startup Disc Creator for re-installing Ubuntu in a netbook.

First it kept refusing to use the USB stick I had emptied for it. The USB I was trying to use was 2GB and formatted with a FAT32 file system using GParted.
Then USB Startup Disk Creator formatted the wrong USB device. The disc it wrongly formatted happened to be the one which I moved my data from the first one to and also contained the .iso file I had intended to use. I found that rather inconvenient, not to mention embarrassing. 

I don't think I made a mistake and clicked the wrong disc by accident but maybe I'm wrong. I think I was being careful and did everything correctly. Usually it's the human who makes the mistake and not the software, and I'm only a human, maybe it was my own fault. Since there are a few others in this thread who are also reporting problems with Ubuntu USB Startup Disk Creator I have decided to add my voice to this thread.

Maybe there is a need to take another look at Ubuntu USB Startup Disk Creator and see if it's possible for the program to be improved somehow.
Ubuntu USB Startup Disk Creator is a very important program for those of us who want to install and/or repair Ubuntu in any computer with no CD/DVD drive, and times when I have used it previously it has worked flawlessly and I really like it when I'm able to use it properly.

---

