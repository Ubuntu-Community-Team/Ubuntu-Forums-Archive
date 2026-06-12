---
title: "No partitions displayed during installation"
date: 2017-02-17
forum: Installation &amp; Upgrades
---

### Post by artuntun on 2017-02-17
I am trying to install Ubuntu 14.04 on a ASUS Republic of Gamers G701. When I come to the screen of partition choosing no partition is displayed like in the following image.

[http://imgur.com/a/yiwFe](http://imgur.com/a/yiwFe)

If I try to click on + - or equal button it get frozen. If I try to continue, I can not since I have to choose a partition. I already created in windows a partition , so the partition exists. 
If I run the command 
> sudo lsblk -o NAME,FSTYPE,SIZE,MOUNTPOINT,LABEL

I get

> NAME   FSTYPE    SIZE MOUNTPOINT LABEL
loop0  squashfs  1.4G /rofs      
sda             57.9G            
&#9492;&#9472;sda1 vfat     57.9G /cdrom     UBUNTU 16_0


which is basically the USB which I am doing boot from.


I have read that the problem might by that my SATA hard drive is with the option RAID instead of AHCI. But in the BIOS there is no other option than RAID.

Any idea?
Thanks!

---

### Post by oldfred on 2017-02-17
Is there a BIOS update available from Asus?

The server installer recognizes RAID much better, and then you can install any desktop of your choice making it any flavor of Ubuntu that you want.

Are the drives the newer NVMe type. That often requires Vendor updates to work also.

Edit.
Also use the newer versions of Ubuntu. All the updates will be in the newer versions and they should work better.
Try 16.04.2 which just came out today, 16.10 or even the still in development 17.04.

---

### Post by RobGoss on 2017-02-18
What are the specs for your machine


- Brand name & model
- CPU
- RAM (size)
- graphics chip/card
- wifi chip/card

This will help others to trouble shoot your problem


How did you create your installation media and what program did you use?

Did you try formatting that USB drive before you install the ISO file?

Did you check the integrity and authenticity of your download

**How to veriry**

[https://www.ubuntu.com/download/how-to-verify](https://www.ubuntu.com/download/how-to-verify)

I would have to say in most cases checking the** ISO** file is almost always good, but! there are cases were the files maybe corupt

---

