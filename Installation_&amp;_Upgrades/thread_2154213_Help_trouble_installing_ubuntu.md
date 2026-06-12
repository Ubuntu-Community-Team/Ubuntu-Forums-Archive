---
title: "Help trouble installing ubuntu"
date: 2013-06-13
forum: Installation &amp; Upgrades
---

### Post by hondaprelude on 2013-06-13
Hello,

I have windows 7 64bit im trying to install ubuntu 12.04 alongside windows 7. I partitioned a 200gb partition on the hard drive for ubuntu. please be kind this is the first time trying to install ubuntu and I dont want to possibly mess up the windows side of the hard drive. When trying to install it I keep getting an error message. here is a link to the error message I keep getting if anyone wants to look at it.[http://www44.zippyshare.com/v/11891918/file.html](http://www44.zippyshare.com/v/11891918/file.html)

---

### Post by fantab on 2013-06-14
I am having trouble reading the link you posted. Try this instead: [http://paste.ubuntu.com/](http://paste.ubuntu.com/)

I suspect that you want install Ubuntu as Dual Boot on a separate partition but you are using WUBI installer which will install Ubuntu INSIDE Windows. Is my suspicion correct?

---

### Post by DasEi on 2013-06-14
Hello hondaprelude,

from your above post here I assume you don't want wubi, but an additional install on the freed 200gb place, so alongside, so that's called dualboot. As fantab mentioned, the information from your link isn't too good, the place here might be better for more specialised or thicky threads, so I might point you to irc.ubuntu.com  , though this is also a possible place to ask. The Task is moderate as far as I get it, even for a ubuntu-starter,  but resposivness is not as fast as in irc, consider asking there, I'm leaving soon for some 2 Hours, either (as maaany more)me  can later  be found in irc. For now  I can point you to alternate install, usb-install , but can't google it for you while in  absence  DasEi

---

### Post by hondaprelude on 2013-06-14
Ok thank you for that I didn't know that the wubi was trying to install Ubuntu within windows. I am trying to do a dual boot where the Ubuntu os is on the 200gb. Am I getting the wrong installation file or just going about the procedure the wrong way?

---

### Post by hondaprelude on 2013-06-14
Ok so an update on what I did this morning I installed unetbootin on the usb drive and just selected the Ubuntu 12.04 from there list and installed it. I reformatted the 200gb partition of the hard drive as ntfs. When I booted up the computer I booted into Ubuntu off of the usb. When I tried to install it I Kept getting an error that there was no root directory on the 200gb partition. When I tried to format it to ext 2, 3, or 4 and put a root directory on it the error was then that the drive was busy so it still wouldn't install. I wiped my computer and reinstalled widows 7 the hard drive at the moment only has a c partition. I want to create another 200gb partition for Ubuntu and install Ubuntu so that my system is then a dual boot system. what format should I format the 200gb partition in. I thought that Ubuntu was able to use ntfs is this not true?

---

### Post by ubfan1 on 2013-06-14
No, Ubuntu cannot install to an ntfs partition.  ext3 or ext4 would be best.  The installer should grab the free space and allow you to select the filesystem.

---

### Post by fantab on 2013-06-14
No Ubuntu/Linux will NOT install on NTFS filesystem. (It can read and write data to it later with the help of a ntfs3g driver). To install Ubuntu you have to use EXT4 filesystem.

With Ubuntu USB, using GPARTED you can format it as Ext4. Also, installing Ubuntu on 200GB single partition may not be a good idea. Ubuntu needs atleast two partitions but for you I recommend 3 partitions for Ubuntu.

20-30GB ext4 / for Ubuntu system files
2-4GB Linux SWAP
178-166 ext /home for your DATA, like Documents, Videos, Music etc.

Here is a catch: 'Msdos' partition table can have only 4 Primary Partititons. If we need more then we have to create an EXTENDED partition. Withing Extended partition we can have more than 100 Logical Parititions. 
If you have further doubts regarding this then post the output the following command from Ubutunt USB:

```
sudo parted -l
```

or post the screen shot from GPARTED showing all your Partitions Plus a screen shot of your paritions from Windows.

---

