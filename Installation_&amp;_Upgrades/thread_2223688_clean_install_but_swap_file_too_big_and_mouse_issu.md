---
title: "clean install but swap file too big and mouse issues"
date: 2014-05-12
forum: Installation &amp; Upgrades
---

### Post by Bhakti108 on 2014-05-12
Hi

Just completed a clean install of 14.04. I decided to tick LVM as I wanted to use its functionality to manage my 3Tb discs similar to the way "storage spaces" does in win. However I decided to accept the default install and not manually setup the partitions. 

BIG Mistake! I have 32gig Ram with an Intel® Core™ i7-4770K CPU @ 3.50GHz × 8 and a Nvidia Quadro K4000/PCIe/SSE2 - SSD 120 Gig and 2 x 3Tb HDD, There is absolutely no rhyme or reason for having 31 gig of swap space, but that is what LVM set up. 

When i go into the GUI for it, it tells me that the drive size cannot be altered. That is BS as it's lost space on an ssd - stupid to say the least. 

Is there a fix for this situation, or did the developers completely overlook the fact that many desktop machines are using high amounts of RAM and maybe defaulting LVM to match the swap to the ram size is a little overblown today?

The likelehood is that, with that CPU and RAM I wont *ever* actually use *any* of the swap space, not even when rendering big video's which is what I need that gear for. 

I would dearly like to recover that space without having to do another install. 

2nd issue, which is irritatiing, the wireless mouse, (new batteries) seems to get attracted to spots on the display, like it will "magnetise" to some text in a web page, or to a window bar on the desktop and I have to jerk it to free it. Is there something to tweak to improve it? its a logitech two button/scroll wheel mouse. Additional drivers don't show a need for a proprietary driver and it has worked for years on all my other Linux flavours. 

Any help gratefully recieved.

---

### Post by TheFu on 2014-05-12
Best to ask 1 question at a time.

Turn off the swap, clean up the LV, create a new LV with 2G of swap, use mkswap to format it, enable the new swap partition - that should be enough, unless you hibernate.  Default installations have to assume people will use standby and hibernate, hence why the amount of RAM is set as the default.

---

### Post by Bhakti108 on 2014-05-12
Phew, thanks, at least there is away. Please could you expand a little, I have never used lvm before, so how does one 'clean up' the lv? I have removed swap and now have that as unused space. I am not sure how to proceed from here. 

perhaps if I explain what I am tyring to get too, it might make it easier. I have always had my / partition seperate from my /home one. how do I acheive this using LVM or am I thinking in old terms and not understanding the concept of LVM properly? Like I have 120 gb ssd which contains everything at the moment. Should I leave / on that and also 2gig swap and move /home to one of the hdd? if so how do i do that? 

Sorry to sound like such a fool, I am struggling to understand the logic ov lvm. 

Thanks for any help you can give me.

---

### Post by oldfred on 2014-05-14
I do not know nor use LVM, but some links. You cannot use gparted, but have to use LVM tools.
I probably would have kept SSD as boot drive, so it would not be part of LVM??

 LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

---

### Post by Bhakti108 on 2014-05-14
Thanks OldFred

I will work my way through those links and then see what I have learnt. I actually think that LVM did create a small separate sector on the ssd for the boot drive, because checking it with gparted shows a /boot/efi partition, a boot/ partition and then the LV see screenshot [ATTACH=CONFIG]253164[/ATTACH] One thing that puzzles me, is why it created a fat32 and an ext2 partition. Very confusing. The original stuff I read in regard of using LVM certainly did not indicate the complexity of this tool. It made it seem a very easy way to set up software mirroring. Cest la vie - off I go to read some more. 

:P

---

### Post by oldfred on 2014-05-14
With LVM and maybe RAID, it seems to automatically put the efi partition outside of the LVM or RAID. 
I had assumed that UEFI could only read a FAT32 partition in MBR or gpt partitioning. But just saw a thread where the efi partition was inside the RAID?

And if encrypted it will have a /boot partition outside the LVM. Was yours encrypted or is that the default with all LVM?

---

### Post by Bhakti108 on 2014-05-14
I didn't select encrypt, so am presuming its not.

---

