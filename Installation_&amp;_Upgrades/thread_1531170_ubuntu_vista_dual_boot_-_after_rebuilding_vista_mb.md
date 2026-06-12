---
title: "ubuntu vista dual boot - after rebuilding vista mbr how do I get to ubuntu"
date: 2010-07-14
forum: Installation &amp; Upgrades
---

### Post by dave_in_roanoke on 2010-07-14
All was going fine (current vista and ubuntu 10.4) after updating both; grub2 began defaulting to memtest. After lots of googling I found and loaded the startup manager.
 
I was able to choose my vista as default but something hosed my vista mbr. I've got that fixed and now I don't hit grub2 at all when booting I go straight to vista.
 
I have the current 10.4 Live CD and the Alternate CD. 
 
I'd like to get back to my dual boot and there is nothing on my linux partition that I need so a re-install is acceptable.
 
If there a relatively simple to get grub2 operational please share it with me.
 
If there is not, is there anything that I should do with the existing linux partitions.
I have one HD with: 
my vista C: [280 gb],
ubuntu [165 gb],
ubuntu [7 gb] and 
HP Factory Image [9 gb] 
 
Thanks Dave

---

### Post by oldfred on 2010-07-14
You must have reinstalled the windows MBR not just the boot sector.

How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu 9.10)
[http://ubuntuforums.org/showthread.php?t=1014708](http://ubuntuforums.org/showthread.php?t=1014708)
kansasnoob on grub or grub2 reinstall
[http://ubuntuforums.org/showpost.php?p=9338226&postcount=41](http://ubuntuforums.org/showpost.php?p=9338226&postcount=41)

Install from LiveCD install on sda5 and want grub2 in drive sda's MBR:
Find linux partition, change sda[COLOR=DarkRed]5[/COLOR] if not correct, I cannot tell from the windows list what sdaX is your install sda2?
sudo fdisk -l
sudo mkdir /mnt/sda[COLOR=DarkRed]5[/COLOR]
sudo mount /dev/sda[COLOR=DarkRed]5[/COLOR] /mnt
sudo grub-install --root-directory=/mnt /dev/sda
If any errrors:
sudo grub-install --recheck --root-directory=/mnt /dev/sda

---

### Post by dave_in_roanoke on 2010-07-14
:popcorn:

Thanks OLDFRED you seem to have completely understood my problem and knew what I would need to do.

The 1st link (How to restore the Ubuntu/XP/Vista/7 bootloader (Updated for Ubuntu  9.10)
[http://ubuntuforums.org/showthread.php?t=1014708 )]("http://ubuntuforums.org/showthread.php?t=1014708")

Seemed to be "IT". 

Historically "google" has been my fist recourse for all problems. I think that  ubuntuforums might be my #1 for ubuntu questions.


[]("http://ubuntuforums.org/showthread.php?t=1014708")

---

