---
title: "Xubuntu doesnt recognize my installed OS and partitions"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by ftcX98 on 2014-08-25
Hello Ubuntu Community,

I wanted to install the latest xubuntu LTS beside my normal Windows 7. However the installer said there was no other operating system installed and displayed a blank hard drive. So I went back to windows and made a specific partiton of 250 GB for xubuntu on my 1 TB hard drive. Now when I join back to the live xubuntu displays both the windows volume and the xubuntu one on the desktop and the file manager, but not in the installation setup**: **[http://i.imgur.com/uomXndo.png](http://i.imgur.com/uomXndo.png)

Additionally, when I proceed to create a 250gb partition there, it says there is no “root file system defined“.
I backed up my windows so every tip would be appreciated **:**)

Another fact about xubuntu is driving me crazy too**:** As a user of a german keyboard I tried to set german as the keyboard language but theres is nor confirm or safe button, so I keep tzping on an english board. [http://imgur.com/bmuOSCw](http://imgur.com/bmuOSCw)

Thank you

---

### Post by grahammechanical on 2014-08-25
As regards the German keyboard layout there is an ADD button.

My advice would be to load to the Live session desktop and open Gparted and see if that recognises the existence of a 250GB unallocated space. If so use Gparted to turn that unallocated space into a partition and format it or give it a file system of Ext4. Then run the installer. You might want to create two partitions out of it. You will need a swap partition.

Regards.

---

### Post by ftcX98 on 2014-08-25
The Add button just adds another language to the one i already selected...

Gparted displays the same but displays following message
[URL="http://i.imgur.com/aMU91lv.png"]http://i.imgur.com/aMU91lv.png

thank you
[/URL]

---

### Post by ajgreeny on 2014-08-25
Noot sure about the keyboard problem, I only ever use an English _UK version and have never had a problem.

Regarding your partition problem, you should** never ever make a partition for a Linux OS using windows**; you should only shrink your windows partition but not actually make a new partition, just leave unallocated space and then make new partitions during the Ubuntu installation.

From a live DVD or USB Ubuntu system can you show the output of 
```
sudo fdisk -l
sudo parted -l
```The first may just show an error, but it should help us figure out the reason for the problem even if you do.

---

### Post by ftcX98 on 2014-08-26
[http://i.imgur.com/spOK6mo.png](http://i.imgur.com/spOK6mo.png)

It says it has an error but displays sda1-3 which probably are my three partitions of windows, xubuntu and maybe something else by my computer manufacturer.
Thanks for your support so far.

---

### Post by yancek on 2014-08-26
Your GParted and parted outputs indicate you have GPT partitioning on your system and that is corrupted.
If this was an OEM install of windows 7, the three partitions are probably  small boot partition, a recovery partition and a very large system partition.
Which installation option did you use with Xubuntu, Something Else?  You should shrink the largest windows partition from windows7 to create free/unallocated space for Xubuntu and retry.  I don't use GPT so can't help with that.

---

### Post by memomelaque2 on 2014-08-26
I have had a similar experience lately. Both Lubuntu and Kubuntu recognize that the disk contains Windows and gives the right options, both go on to install GRUB. But, Ubuntu will not recognize the Windows system and when I do "other" to install, it does not include GRUB and then only starts up Ubuntu, no Windows option.

---

### Post by ftcX98 on 2014-08-26
> **yancek said:**
> Your GParted and parted outputs indicate you have GPT partitioning on your system and that is corrupted.
If this was an OEM install of windows 7, the three partitions are probably  small boot partition, a recovery partition and a very large system partition.
Which installation option did you use with Xubuntu, Something Else?  You should shrink the largest windows partition from windows7 to create free/unallocated space for Xubuntu and retry.  I don't use GPT so can't help with that.

I already shrinked the the Windows 7 partition, and made a new one for Xubuntu, but no matter if I 1 or 2 or 3 partitions, gparted or the installer display a plain and empty hard drive (with no OS). This is not an OEM install, when my computer crashed a while ago I reinstalled it.

---

### Post by ftcX98 on 2014-08-29
Anyways thanks for you effort...

---

