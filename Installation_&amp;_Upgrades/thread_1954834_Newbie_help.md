---
title: "Newbie help"
date: 2012-04-08
forum: Installation &amp; Upgrades
---

### Post by dkdias on 2012-04-08
I just tried to install Ubuntu on my computer on a second drive because my main drive has Windows XP on it, but I am having problems. Please help.  Here is what it is doing..

Dell computer boots and loads screen to pick Windows XP or Ubuntu. I pick Ubuntu and it says, "completing installation...."  It then goes to the splash screen and just stays there.  I press the tab button and I get these lines:
Init: Line 7 can't open dev/sr0 :no medium found
Init: Line 7 can't open dev/sr1 :no medium found
stdin : error 0

It repeats this many times then it says:

Busybox v1.13.3 (ubuntu 1:1.13.3- ubuntu 11) built in shell (ash) enter help for list of commands
Intramfs unable to find medium containing a live file system

I have windows XP on the C: harddrive(sda)and i have the linux on sdb. Windows is not recognizing the linux drive. The computer boots fine into Windows, but I want to use linux!  

Thank you for your help with this!!


A side queston: On the OS selection it has windows listed first, can I change that somehow to have linux listed first so It will boot into linux automatically upon boot up. Right now I have to switch the selection to boot into linux.  Thanks again!

---

### Post by Basher101 on 2012-04-08
by the looks of it you tried a Wubi installation, which creates a virtual partition _**inside**_ Windows. This is to usually test things out before going for the actual install...

To actually install it you will need to **boot** the live CD/USB. To do so you will need to change the bootorder in your BIOS. 

Once you boot the live CD you get a few options. Choose "Try Ubuntu" until you get to the desktop. Here you will see one icon on the desktop that will start the installation program. 

From here on i cannot give you 100% accurate instructions, as i do not know how the "install alongside windows" option works with 2 drives (and if it lets you select one, which it ***should***, but i am not 100% sure..). 

regards

---

### Post by dkdias on 2012-04-08
Below are all my hard drives and my system information. Thanks


255 heads, 63 sectors/track, 7294 cylinders, total 117187500 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xea1aa9c7

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1              63   114173954    57086946   83  Linux
/dev/sda2   *    16450560   117178109    50363775    7  HPFS/NTFS/exFAT
/dev/sda3       114173955   117178109     1502077+   5  Extended
/dev/sda5   ?   118564921   122234994     1835037   20  Unknown

Disk /dev/sdb: 20.8 GB, 20847697920 bytes
255 heads, 63 sectors/track, 2534 cylinders, total 40718160 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0x0007bfee

   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *        2048    38623231    19310592   83  Linux
/dev/sdb2        38625278    40716287     1045505    5  Extended
/dev/sdb5        38625280    40716287     1045504   82  Linux swap / Solaris

---

### Post by Basher101 on 2012-04-08
i cant really see much here^^ post a screenshot of Gparted using a Live CD. Thats something i can work with.

---

### Post by dkdias on 2012-04-10
What I am thinking about doing is just formatting both hard drives on my computer and starting all over.  I plan on removing all particians and then reloading linux onto the hard drive.  My question with this is will it wipe off all the grub too, so I won't have any of the splash screens listing both operating systems?  I know I will loose everything, but I am willing to do that..... thanks for the help!!

I guess my next question would be, which method to wipe the drives is easier.  A side problem I have had with the live CD in linux is the typing is garbled to look at so it is hard to figure out what I am doing?  Any suggestions?

---

### Post by mastablasta on 2012-04-11
> **dkdias said:**
> What I am thinking about doing is just formatting both hard drives on my computer and starting all over. I plan on removing all particians and then reloading linux onto the hard drive. My question with this is will it wipe off all the grub too, so I won't have any of the splash screens listing both operating systems? I know I will loose everything, but I am willing to do that..... thanks for the help!!
 
I guess my next question would be, which method to wipe the drives is easier.
 
simply reinstall windows. during reinstall choose to reformat the disk or rearrange partitions, windows will do the rest. it will delete/ovewrite grub.  then you install linux on new partition you created. i sugest you create disk space and then install to that using the default options. linux will create necessary partitions by itself.
 
formatting the drive will destroy all data on it.
if you have two disks you WILL need to manually tell it where to install grub and you need toput it in the correct place.
 
 > 
 A side problem I have had with the live CD in linux is the typing is garbled to look at so it is hard to figure out what I am doing? Any suggestions?
 
try booting with nomodeset or xforcevesa. after install has finished you may need to install additional driver for graphics card. but hard to say since you didn't provide any information.

---

### Post by roelforg on 2012-04-11
dev/sr* are cd-/dvd-stations
I think it wants the cd for some files.

---

### Post by mastablasta on 2012-04-11
yeah it seems it want's live disk but why? shouldn't you eject it after reboot.

---

### Post by roelforg on 2012-04-11
> **mastablasta said:**
> yeah it seems it want's live disk but why? shouldn't you eject it after reboot.
 
Maybe he used wubi's full install mode?
If you run it from the cd it still has to install stuff.
So maybe that mode wants the cd just like the inside windows mode needs the iso on virtual disk.

---

