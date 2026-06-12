---
title: "Installer Crashed... Now what!"
date: 2016-02-05
forum: Installation &amp; Upgrades
---

### Post by ross4 on 2016-02-05
I am trying to install Xubuntu on the following machine:
 [LEFT]HP EliteBook 6930p; Intel(R) Core(TM)2 Duo CPU  P8700  @ 2.53GHz; Disk 149GiB (160GB);  x86_64; memory 4GiB[/LEFT]
 [LEFT]VGA compatible controller[/LEFT]
 [LEFT]Intel Mobile 4 Series Chipset Integrated Graphics Controller[/LEFT]
 [LEFT] Windows Vista[/LEFT]
 [LEFT] 
[/LEFT]
 [LEFT] I chose Xubuntu because that is what I have been running on my other machine for the last year or so.[/LEFT]
 [LEFT] I downloaded xubuntu-14.04.3-desktop-i386.iso and burned it to a 16 GB USB. It booted fine and ran well so I decided to install it while running it live. It resized the Vista partition and then, part way through the installation. The messge “Installer Crashed” came up, along with a longer message about sending a bug report, which I don't think happened. When I checked the partitions on the disk, I found that the Vista partition had been shrunk by the amount I requested but the remainder of the disk had not  been partitioned or formatted. I used a Mint live CD to re-expand that partition.[/LEFT]
 [LEFT] 
[/LEFT]
 [LEFT] Oddly, the USB on which I installed the 32-bit Xubuntu would not boot again.[/LEFT]
 [LEFT] 
[/LEFT]
 [LEFT] I then installed  xubuntu-14.04.3-desktop-amd64.iso on the same USB after removing all old files and I installed linuxmint-17.3-xfce-64bit.iso  on a similar  16 GB USB.
[/LEFT]
 [LEFT] 
[/LEFT]
 [LEFT] Both of these booted fine and seem to work as live installations.[/LEFT]
 [LEFT] I then tried installing Xubuntu from the 64-bit iso while running it live. I got the same “Installer Crashed” message and the same lack of re-boot on this USB. This time, the disk was properly repartitioned and formatted, though.[/LEFT]
 [LEFT] 
[/LEFT]
 [LEFT] I haven't tried installing Mint yet because I am worried that trying that might do damage to the whole system.  [/LEFT]
 [LEFT] 
[/LEFT]
 [LEFT] I've been working on this for several days and now asking the forum for solutions. Btw, I am not committed to using Xubuntu 14.04 LTS but it seemed like a reasonable approach.[/LEFT]
 [LEFT] Regards,[/LEFT]
 [LEFT] Ross[/LEFT]

---

### Post by conor9 on 2016-02-05
had something similar recently - I was recycling a hard disk that had been part of a RAID1 system. The installer would get to the bit about choosing partitions, display no options and then crash if I selected anything other than the exit button.

I found that I had to uninstall the dmraid package in order for the installer to correctly see the partitions (despite gparted being able to see the partitions). Not sure if this is of any help?

---

### Post by ross4 on 2016-02-05
Could be related but I can't make a connection at the moment.

---

### Post by Vladlenin5000 on 2016-02-06
I agree, no connection. Except for the culprit being the same hardware component, the hard drive.
In you case it has nothing to do with RAID. Most likely a failing drive. I wouldn't trust a (10yo ??) 160GB drive today...

I suggest you check for errors in the live session without installing. The Disks utility should be enough: Select the drive on the left > CTRL+S > Autotest

---

### Post by Bucky Ball on 2016-02-06
When you say the 'disk was repartitioned and formatted', how exactly was it formatted? You don't need to create anything on there prior to install, just leave free space where you are going to install Ubuntu/Xubuntu.

My guess, and it's only a guess, is that you may have created NTFS partitions to install Xubuntu. Xubuntu won't install on NTFS partitions, therefore, when you try to install Ubuntu 'automagically' it see nowhere to install (no free space) and crashes. 

Leave free space, choose 'Something else' when you get to the partitioning section of the install, manually partition the drive. Choose the mountpoints in there (/ and /swap, among others, are selectable defaults) and set to format but make sure the existing Windows partitions, and any other existing partitions, are NOT set to format.

Also, did you check the install media for defects prior to attempting the install? That's one of the options when you boot. When you are preparing the USB to transfer the ISO, you should, in Gparted, choose 'Device> Create partition table' to completely wipe it, then create one FAT32 partition on there. 

What are you using to burn the ISO to USB? UNetbootin? Universal USB Installer? Rufus?

---

### Post by ross4 on 2016-02-06
Bucky Ball, thanks for your reply. 
Here are some more details.

  	 	 	 	     I burned all the ISOs to USBs using UNetbootin.

  

  After the first attempt crashed, when I looked at the harddrive using gparted, the ntfs parttition for Vista  had been shrunk but the remainder of the drive was just unformatted free space, I think. At any rate the remainder had not been formatted.

  

  I then re-expanded the ntfs partition to include the entire disk, checked that Vista booted properly, which it did after going through a disk check.

  

  I then tried installing a second time and the installation crashed again but gparted indicates that, after the second failed attempt, the hard drive on the HP had been formatted as :

  /dev/sda1,  ntfs,             84.6   GiB, boot
  /dev/sda2, extended,     60.47 GiB
  /dev/sda5, ext4        ,    60.47 GiB
  /dev/sda6, linuxswap      3.90 GiB
  

  I have burnt (using UNetbootin each time) three different Live CDs (linuxmint-17.3-xfce-64bit.iso , xubuntu-14.04.3-desktop-i386.iso, xubuntu-14.04.3-desktop-amd64.iso) each of which has worked fine as a live CD. The two xubuntu crashed at the attempt to install while in Live CD mode. I haven't tried to install from the Mint CD.
  

  Could a such problem be connected to a problem on the USB? I didn't think so but I've been more often wrong than right in my understanding about such things.

I followed your instructions about

---

### Post by ross4 on 2016-02-06
oops, somehow posted too soon.
I followed your instructions about prepping the USB properly and have once again burnt an ISO but haven't tried installing it yet.
Regards,
Ross

---

### Post by ross4 on 2016-02-06
I finally DID try to install Xubuntu from a USB prepped according to Bucky Ball's advice:
*"When you are preparing the USB to transfer the ISO, you should, in  Gparted, choose 'Device> Create partition table' to completely wipe  it, then create one FAT32 partition on there."* and it installed successfully. Which is very nice! However, instead of trying to install it while in the Live USB mode like I had always done previously, for the first time I tried installing from the UNetbootin menu. So, I can't be sure whether it was prepping the disk properly, installing directly from the UNetbootin menu or both which actually made the install go through to completion.

I would like leave this thread open to hear opinions on this. Also, since my original intention was to remove Vista completely during the install and I intend to try that soon, I may as well try again the next time from within the Live USB mode to see what happens. I will report the results of this on this thread.
To everyone who offered ideas, thank you very much, Especially to Bucky Ball.
Cheers,
Ross

---

### Post by Bucky Ball on 2016-02-06
No probs and glad it worked.

As your initial support request is solved, please mark the thread as solved (see first link in my signature). This will not close the thread to further discussion but it will help other users.

Best to start new threads for new support requests, even if they are somehow related. You can always provide a link back to this thread in the new one. You 'remove Vista' project, for instance, is not related to installations and upgrades or your installer crashing so it would be in the wrong thread in the wrong area. (Note: You can use the USB 'live' session or Gparted from your running install. Install Gparted from the Software Centre. But let's talk about this some other place and time ... )  

Good luck and enjoy! :)

(PS: Staff don't close threads (and only staff can) unless we happen to come across a very old one, an old one someone has woken from the dead by posting on it and bringing it to our attention, or the posters on the thread are misbehaving. This thread doesn't fit any of those criteria, your support request is solved, so chat away! :))

---

### Post by ross4 on 2016-02-07
Done. Thanks very much again.
Ross

---

