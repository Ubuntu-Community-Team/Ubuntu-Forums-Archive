---
title: "Installing ubuntu on a partition of a second drive"
date: 2017-09-28
forum: Installation &amp; Upgrades
---

### Post by astroch2 on 2017-09-28
Hi there.
Im asking for help because I wanna install ubuntu on a paritition of my secondary hard disk.

I have a ssd (for windows) and there is no space for linux ( and i dont want to erase anything). So i have to install ubuntu on my hdd. My hdd have 3 partition and only one is empty.

I tried everything. But i cant boot ubuntu. In the boot device options, my hdd doesnt even appear, only my ssd with windows does. The bios just let me acces windows. What should i do?

---

### Post by mastablasta on 2017-09-28
use boot repair tool to create the bootinfo summary, so we can see how your partitions are arranged and what is called on boot.:

[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

don't use the repair button yet.
you may need ot run it from live session.

or are you saying that you can't even boot into a live session? it is not quite clear from the post.

---

### Post by astroch2 on 2017-09-28
I cant boot into ubuntu. My hdd doesnt appear in the boot device options. I tried changing the priority in bios (hdd>ssd), but my pc runs windows.

---

### Post by oldos2er on 2017-09-28
Do you have Ubuntu installed already? If not you need to create a live medium from an ISO on either a DVD or USB flash drive, and set your bios to boot from it.

---

### Post by astroch2 on 2017-09-28
I used a usb flash drive to install it.

I cant get in the partition using Windows (of the ssd), but according to the Ubuntu of the installation usb stick, ubuntu has been correctly installed in the partition (i can see the files of ubuntu in the partition running the usb).  I just cant boot the ubuntu of the partition.

---

### Post by oldfred on 2017-09-28
Use the Ubuntu live installer in live mode and add the Boot-Repair ppa to it. 
Then when the report runs it should give you a link to a pastebin site. 
Since report can be long, we do not expect it to fit here, so just post link.

---

### Post by oldos2er on 2017-09-28
> 
I cant get in the partition using Windows (of the ssd), .

That's normal,  Windows can't see or read Linux partitions. 
Follow oldfred's advice.

---

