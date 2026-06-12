---
title: "usb installer will not work!!"
date: 2014-06-23
forum: Installation &amp; Upgrades
---

### Post by nnvt on 2014-06-23
Hello,


I've installed and removed ubuntu from my laptop a bunch of times and never had failures with creating a bootable usb, but now I do for some random reason

I'm using a 8gb Lexar usb flash drive and I have used a ton of programs to create the usb i tried it on my laptop with windows 7 and i tried it on windows 8 then I tried to make it on my imac running windows 8 and all looked good but everytime I boot my laptop with this flash drive it says "No Operating System found! No bootable media press any key" Is my USB drive broken or something? It looks like all the programs fail to install the bootloader to the flash drive or the flash drive is just dead, when i open the flash drive in windows it shows all the normal ubuntu files that it's supposed to have but i'm not able to boot from it :/

My BIOS (UEFI) is set to legacy mode (as usual) and the flash drive doesn't get detected at all when disabling legacy mode
can anyone help me?


thanks,

nnvt

---

### Post by LastDino on 2014-06-23
Naming those programs could help a little tbh. Is it the latest version of Ubuntu (14.04)?

---

### Post by nnvt on 2014-06-23
Yep it's the latest version of ubuntu (14.04) downloaded multiple times straight from the ubuntu website


and the programs used were: UNETBootin and Universal USB installer

---

### Post by Urbanmasque on 2014-06-23
I had this problem yesterday and I'm also having problems booting from USB (CD/DVD error from USB install). 
When I got that messaging yesterday I removed all USBs except for my keyboard and was able to get to try/install screen. It sounds like it might not even be recognizing the info on the flash drive. Try to run the pen installer on something else and try again. I ran into this randomly while trying to boot from a 4Gb Kingston, but when I put it onto a SanDisk it ran fine (with the exception being the corrupted CD/DVD error).  Also, make sure you've installed the .iso onto the formatted flash drive. (which is sounds like you have, but doesn't hurt to double check).  Also, make sure to make USB the primary boot option. Save and Restart.

I'm new to Ubuntu but I remember seeing this yesterday and thought I'd throw in my two cents, and see if it helped.

---

### Post by Bucky Ball on 2014-06-23
The USB dongle needs to be BLANK before creating the Ubuntu installer. I mean totally. Don't just delete the files on the USB; format it to FAT32 using Gparted or a Windows tool. 

The USB boot creation process WILL NOT remove any files that are on the USB dongle already. And that includes hidden files. If there are any other files on there apart from the Ubuntu installation ones put there during UNetbooting or Univeral Boot you're generally dead in the water. I speak from experience. ;)

Format the drive to FAT32 and try again. If you've already done this, ignore and carry on ...

---

### Post by LastDino on 2014-06-23
Also, just to throw in one more software into mix, use Lili (Live Linux usb creator) and yeah, format the USB to FAT 32 before hand.

---

### Post by nnvt on 2014-06-23
It's a distro problem... It seems like the ubuntu iso got uploaded in a bad condition cause i downloaded it multiple times and got the same issue! I tried linux mint and that booted instantly, Also I got rid of the flash drive problem and I'm now using a partition on my hard drive to boot installers!

---

### Post by Bucky Ball on 2014-06-23
If you consider the issue solved please mark it as solved from Thread Tools at the top right of this page to help others. Thanks.

---

### Post by LastDino on 2014-06-24
But I used the same uploaded images to make Live USB and install them on my PC though. I don't have DVD player and I've Ubuntu, Ubuntu gnome and Xubuntu installed on this system.

---

### Post by Urbanmasque on 2014-07-09
> **Urbanmasque said:**
> I had this problem yesterday and I'm also having problems booting from USB (CD/DVD error from USB install). 
When I got that messaging yesterday I removed all USBs except for my keyboard and was able to get to try/install screen. It sounds like it might not even be recognizing the info on the flash drive. Try to run the pen installer on something else and try again. I ran into this randomly while trying to boot from a 4Gb Kingston, but when I put it onto a SanDisk it ran fine (with the exception being the corrupted CD/DVD error).  Also, make sure you've installed the .iso onto the formatted flash drive. (which is sounds like you have, but doesn't hurt to double check).  Also, make sure to make USB the primary boot option. Save and Restart.

I'm new to Ubuntu but I remember seeing this yesterday and thought I'd throw in my two cents, and see if it helped.


Solved my issue eventually by removing the memory from my motherboard. I had 2 [Corsair XMS3 4GB (1 x 4GB) DDR3-1333 Memory]("http://pcpartpicker.com/part/corsair-memory-cmx4gx3m1a1333c9") plugged in.  Removing one got me through the CD Errno 5 issue and I was able to install Ubuntu 14.04 and start up the OS without the USB afterwards.  Now I'm dealing with other issues, and I look forward to pulling my hair out about it alongside you fine gentlemen.

---

