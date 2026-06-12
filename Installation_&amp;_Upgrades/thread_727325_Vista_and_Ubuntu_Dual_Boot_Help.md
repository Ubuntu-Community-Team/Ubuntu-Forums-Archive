---
title: "Vista and Ubuntu Dual Boot Help"
date: 2008-03-17
forum: Installation &amp; Upgrades
---

### Post by Darkchef on 2008-03-17
Hey all,

I know this has all been asked before but i have a few other questions that i cant seem to find answers for. I want to have a dual boot of ubuntu on my computers as i currently have vista installed (which is seriously eating my ram away) but dont want to delete it just yet as i will be hopefully upgrading the ram sometime soon. 

Anyway, I currently have have two partitions, 

One partition with my vista installation at 36GB and another blank partition availiable at 36GB.

I want to install ubuntu 7.10 on this blank partition. However i would like to chnage the ubuntu partition to 20gb and then add the remaining free space to the vista partition. Is this possible without erasing all data ? 

Also how would i install ubuntu to the blank partition during installation ? 

If you could help me out this would be great .

Cheers 

Dan

---

### Post by Pumalite on 2008-03-17
Get Gparted Live CD: [http://gparted.sourceforge.net/download.php](http://gparted.sourceforge.net/download.php)
Burn to disk and boot from it. Post screenshot.

---

### Post by Darkchef on 2008-03-17
Heres the screenshot you asked for. See if you can help. the partition with label STORAGE currently has the free space.

---

### Post by Pumalite on 2008-03-17
Wrong screenshot. The one I want is of Gparted depicting your partitions. You use the camera icon at the bottom. You have to boot Gparted first.

---

### Post by Darkchef on 2008-03-17
Sorry mate, my screenshot didnt seem to save last time so im uploading the screenshot with a live boot of unbuntu. Anyway heres the right screenshot.

EDIT : not too sure what the first partition is for, iv never detected that within windows. im guessing thats acer's emergency backup feature which ive never used. Also there also seems to be another drive that ive never seen called /dev/mmcblk0 that is just under a GB In size ?

---

### Post by Pumalite on 2008-03-17
First of all backup everything. Click on sda2 and delete it. Make new partition on the left (of sda2, 'beginning') of 20000 MB. Make another partition with the rest. This smaller partition has to be next to your Windows. When you have acomplished that; post new screenswhot.

---

### Post by Darkchef on 2008-03-17
the sda2 partition labelled acer contains my vista installation and all my installed programs, would i need to keep this intact ?? i have no idea what sda1 is for ?? im guessing system recovery for acer but im not sure??

EDIT : maybe ive confused things here. storage isnt yet empty as im still saving all the data from it. Storage will be used for the linux partition. but i want to only use 20gb of this and add the remaining space to the windows partition or if this sint possible, keep it as a seperate partition.

---

### Post by Pumalite on 2008-03-17
Change everything I said to dsa3 then, after you backup everything. Funny; sda2 appears empty, or it looks like it. But, you are right; it says ...boot. The large partition has to be on the right then. And the small one on the left, next to Windows.

---

