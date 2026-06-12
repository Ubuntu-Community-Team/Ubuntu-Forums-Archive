---
title: "beginner tries to install alongside windows 7"
date: 2011-02-03
forum: Installation &amp; Upgrades
---

### Post by avaroha on 2011-02-03
I want to install ubuntu and have boot up option. Do I need to partition before downloading ubuntu? Will I be able to access my face book and other chrome pages when I open chrome in ubuntu?

---

### Post by joemartin on 2011-02-03
download and use wubi.....

---

### Post by mastablasta on 2011-02-03
> **avaroha said:**
> I want to install ubuntu and have boot up option. Do I need to partition before downloading ubuntu?

No, but before you install it you will need to. Another option to just try out the system is to either run it live or install it "sort of within windows" using Wubi. only you need to lock a couple of packages so they don't break the install later on.
or you can create a new partition and install the system side by side. careful thoguh as some compputers with win7 come with 4 primary partitions preinstalled.
 
I suggets you try live session first to see if it will all work well upon install. Live session can be made by **booting** from liveCD or LiveUSB (to create live usb key in Windows you can use for example unetbootin)
 
> 
Will I be able to access my face book and other chrome pages when I open chrome in ubuntu?
 
yes.
 
you can also try Chromium (chrome without reporting to google...), Opera, Firefox and many others.

---

### Post by joemartin on 2011-02-03
yes...you can access anything in ubuntu as you can with windows 7.  the only thing is, you have to install chrome (as you did in windows 7) after install..chrome is not included....go to applications.....ubuntu software center....internet....web browsers....install chrome......

welcome to linux....you have now chosen (ubuntu) the best operating system in the world....

---

### Post by avaroha on 2011-02-03
thanks everyone for the replies. I am not sure about using wubi because someone posted that it only gives 30Gb space - is that right? Do I need a programme to partition or is it included in Ubuntu or windows 7?

---

### Post by Bluesan on 2011-02-03
See here for guidance on dual booting Windows 7 and Ubuntu:

[http://ubuntuguide.org/wiki/Ubuntu:Maverick#Dual-Booting_Windows_and_Ubuntu](http://ubuntuguide.org/wiki/Ubuntu:Maverick#Dual-Booting_Windows_and_Ubuntu)

---

### Post by avaroha on 2011-02-04
thanks very much. read wiki and partitioned disc - 130 GB now unallocated. Do I need to format or anything before I install ubuntu? i have got a disc with a mag i bought

---

### Post by Rubi1200 on 2011-02-05
No need to format, leave it as unallocated space.

When you start the installer, choose the manual partitioning option and then tell the installer to format as ext4 and make the mount point / (the root file system).

What I would do, though, is in the 130GB is create a swap partition. Swap needs to be 1.5-2x the RAM you have. So, if you have 2GB RAM, swap will be 4GB.

If you also want a separate home partition, you could do something like this:

From the 130GB:
1 partition for / (of about 15-20GB)
1 partition for swap (see above)
The rest for /home (your files, photos etc.)

---

### Post by avaroha on 2011-02-05
thanks again. just discovered that the DVD has lubuntu - not ubuntu. or PCLinuxOS 2010.12. Any advice?

---

### Post by coffeecat on 2011-02-05
> **avaroha said:**
> thanks again. just discovered that the DVD has lubuntu - not ubuntu. or PCLinuxOS 2010.12. Any advice?

That's the LXFDVD142 from the latest issue of Linux Format magazine, isn't it? Is that the only LXF magazine you've bought, or do you have some back numbers? Ubuntu 10.10 was on the Christmas issue LXF139, or 10.04 a few months prior to that. If you don't have access to earlier Linux Format DVDs, you'll have to download the ISO and burn it to CD yourself. Have a look here:

[http://www.ubuntu.com/](http://www.ubuntu.com/)

---

### Post by avaroha on 2011-02-05
thanks. downloaded, burnt cd, installed, and ubuntu is running! Can my windows files be accessed from ubuntu? or is there a way to transfer them?

---

### Post by coffeecat on 2011-02-05
> **avaroha said:**
> thanks. downloaded, burnt cd, installed, and ubuntu is running!

That was quick! :shock: Some sort of record, I think. :wink:

>  Can my windows files be accessed from ubuntu? or is there a way to transfer them?Yes. Simply look in the Places menu for your Windows partition and click on it. A browser window will open. Try to minimise accessing the Windows partition and try not to write to it at all. Vista and Windows 7 sometimes react badly to writes from outside. I can't see what you decided on for a partition layout, but a shared NTFS data partition for use with both Windows and Ubuntu is a better option than accessing your Windows partition from Ubuntu.

---

### Post by avaroha on 2011-02-06
thanks - have some popcorn!:popcorn: oh the smiley won't copy.

windows has a 10GB and a 170Gb partition. New ubuntu partitions are 20GB /  8GB swap  102 GB /home.

How can you make the shared partition? Will try the access you suggested now.

---

