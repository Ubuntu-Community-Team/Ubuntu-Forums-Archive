---
title: "How to install on a USB stick"
date: 2011-02-12
forum: Installation &amp; Upgrades
---

### Post by pawan98 on 2011-02-12
Hi I have a 320GB Usb Stick, ( its really a usb drive ), but anyway, I want to INSTALL ubuntu on it, not put the installation on there, but install it, I've made separate partitions for Ubuntu, now i just need to install it on there, but i don't know how to :S.

---

### Post by mr_luksom on 2011-02-12
In the 'System' menu, look for Startup Disk Creator or enter:
```

sudo usb-creator-gtk

```

---

### Post by I am the Allspark on 2011-02-12
[COLOR=black][FONT=Verdana]Oh Hi! [/FONT][/COLOR]
[COLOR=black][FONT=Verdana]Im thinking of using Linux (im a Newbie) I tried to install it to my Memory stick from linuxliveusb.com, but couldn’t figure it out. Is it possible to Run Linux off USB (like a live CD) without installing it onto Dell Laptop [/FONT][/COLOR]
[COLOR=black][FONT=Verdana][/FONT][/COLOR] 
[COLOR=black][FONT=Verdana][COLOR=black][FONT=Verdana]PS. can i install it to memory stick without Formatting the already occupied Stick.[/FONT][/COLOR]
[/FONT][/COLOR]

---

### Post by zhogan85 on 2011-02-12
I_am_the_all_Spark,you can quite easily make a bootable usb using unetbootin, the download is available at [http://unetbootin.sourceforge.net/](http://unetbootin.sourceforge.net/). Then download the ISO file of whichever distro you want, presumably ubuntu, and unetbootin does the rest. There are plenty of tutorials on this already, both on ubuntu's site and in these forums. Simply do a Google search and you will find plenty. For more specific questions, don't be shy about starting your own thread. To my knowledge, creating a liveUSB will overwrite the data on your stick so its best to backup beforehand.

---

### Post by Cpierce on 2011-02-12
To make mine, I just unplugged the internal hard drive, stuck the USB in, and then ran the Ubuntu install CD as you normally would. If the USB is the only drive, then the CD will see it, and install on it.

---

### Post by C.S.Cameron on 2011-02-12
Following step by step for Full install of 10.10 to USB device, partition sizes given are for 8GB drive, adjust size to suit:

Turn off and unplug the computer. (See note at bottom)
Remove the side from the case.
Unplug the power cable from the hard drive.
Plug the computer back in.
Insert the flash drive.
Insert the Live CD.
Start the computer, the CD should boot.
Select language
Select install Ubuntu.
Select Download updates while installing and Select Install this third-party software.
Forward
At "Allocate drive space" select "Specify partitions manually (advanced)".
Forward
Confirm Device is correct.
Select "New Partition Table" click Continue on the drop down.
Click "Free space" and "Add".
Select "Primary".
Make "New partition size..." about 1GB.
Location = Beginning.
"Use as:" = "FAT32 file system"
And "Mount point" = windows.
Select "OK"
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 3 to 4 GB, Beginning, Ext4, and Mount point = "/" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = 1 to 2 GB, Beginning, Ext2, and Mount point = "/home" then OK.
(Optional)
Click "free space" and then "Add".
Select "Primary", "New partition size ..." = remaining space, (1 to 2 GB), Beginning and "Use as" = "swap area" then OK.
(Importent)
Confirm "Device for boot loader installation" points to the USB drive. Default should be ok if HDD was unplugged.
Click "Install Now".
Select your location.
Forward.
Select Keyboard layout.
Forward.
Insert your name, username, password, computer name and select if you want to log in automatically or require a password.
Selecting "Encrypt my home folder" is a good option if you are woried about loosing your USB drive.
Select forward.
Wait until install is complete.
Turn off computer and plug in the HDD.
Stick the side panel back on.

Note:
You may omit disabling the hard drive if after partitioning you choose to install grub to the root of the usb drive you are installing Ubuntu to, (ie sdb not sdb1). Be cautious, many people have overwritten the HDD MBR.
At boot you will then be given the option to boot your computer's hard drive, even when booting another computer.

---

### Post by pawan98 on 2011-02-18
*Bump*

I tried the above, when I tried to boot it, it said 'Failed to boot, press F1 to retry'

---

### Post by BananaPeal on 2011-02-18
> **pawan98 said:**
> *Bump*

I tried the above, when I tried to boot it, it said 'Failed to boot, press F1 to retry'

YEA! I had the exact same happen, although not that same message, mine just hangs.

I  think the installer's formatting thing messed up cuz when looking at the usb with testdisk it showed some irregularities with a fat32 partition that i was to use for storage.

try running this from liveCD:
[http://bootinfoscript.sourceforge.net/](http://bootinfoscript.sourceforge.net/)

 and posting the results.txt, would be interesting to see if it has similar errors to mine! And results.txt is useful in diagnosing problems with the boot files in linux.

my thread is: [http://ubuntuforums.org/showthread.php?t=1690358](http://ubuntuforums.org/showthread.php?t=1690358)

good luck!

---

### Post by C.S.Cameron on 2011-02-18
With a USB hard drive I would suggest making the first partition NTFS rather than FAT32.

---

### Post by BananaPeal on 2011-02-19
Thank you mr. Cameron!

> **C.S.Cameron said:**
> With a USB hard drive I would suggest making the first partition NTFS rather than FAT32.

That did it for me, finally booted into my installed linux. May I ask, wherever do you get your insights from? I never can find enough information in the documentation, does it all come from experience or is there a book i can shove my face in for a weekend?

Thanks again sir!:popcorn:

---

### Post by C.S.Cameron on 2011-02-23
> **BananaPeal said:**
> Thank you mr. Cameron!



That did it for me, finally booted into my installed linux. May I ask, wherever do you get your insights from? I never can find enough information in the documentation, does it all come from experience or is there a book i can shove my face in for a weekend?

Thanks again sir!:popcorn:

Tinkering and experimentation.

---

### Post by I am the Allspark on 2011-02-24
[COLOR=black][FONT=Verdana]Thanks zhogan85[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I downloaded Unbuntu from UNetbootin to my drive, and it's now on my Memory stick. I am know wondering if i can put it in its own file to keep it separate from other files i may want to save on the same USB stick. Will Unbuntu still Load as a live CD, if I do that?[/FONT][/COLOR]

---

### Post by C.S.Cameron on 2011-02-24
> **I am the Allspark said:**
> [COLOR=black][FONT=Verdana]Thanks zhogan85[/FONT][/COLOR]
[COLOR=black][FONT=Verdana]I downloaded Unbuntu from UNetbootin to my drive, and it's now on my Memory stick. I am know wondering if i can put it in its own file to keep it separate from other files i may want to save on the same USB stick. Will Unbuntu still Load as a live CD, if I do that?[/FONT][/COLOR]

No,it must be on root, make a folder for the other files instead.
When booting the  live drive you will find this folder in filesystem/cdrom.

---

