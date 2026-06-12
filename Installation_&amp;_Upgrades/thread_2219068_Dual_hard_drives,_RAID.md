---
title: "Dual hard drives, RAID"
date: 2014-04-22
forum: Installation &amp; Upgrades
---

### Post by bsliv on 2014-04-22
I'm trying to setup a Ubuntu 14.04 headless lamp server with dual 4tb drives in a raid 1 setup off a usb stick.  The furthest progress I've made is a successful install with only one drive attached.  

If I have both drives attached, the installation fails copying system files or installing grub.  

If I have one drive attached and try to create the raid array, it reboots when it reads the hard drive during the first 2 seconds of booting.  

How should I set this thing up most easily?  I don't have a mouse.
Can I create the raid 1 array after installing the os and booting from the hard drive?  
Is it better/easier to create the array during the os installation?
Are there clear instructions on setting up 14.04 with large hard drives?
Are there clear instructions on setting up raid 1 with large drives? 

To me a boot loader works at a shoe store.  Grubs are found in the garden.  A partition is a wall.  I don't want my hard drive divided.  Why are there 3 partitions on my 1 drive?  Why is this so tough?  

sys c: and copy a: c:\dos was a whole lot easier.

---

### Post by papibe on 2014-04-22
> **bsliv said:**
> How should I set this thing up most easily?  I don't have a mouse.
You don't need a mouse to install "Ubuntu Server". The installer uses text mode so you only need a keyboard.

If you want to install the Desktop version, I don't think it would be possible to use the graphical installed without a mouse. However, there another installers called 'alternate', which works in text mode. You can find them [here]("http://www.ubuntu.com/download/alternative-downloads").
> **bsliv said:**
> Can I create the raid 1 array after installing the os and booting from the hard drive? 
Yes if the OS partition won't be part of the raid (which is what I would do BTW).
> **bsliv said:**
> Is it better/easier to create the array during the os installation?
Only if the OS will be located inside the raid. If not, you can create it later.
> **bsliv said:**
> Are there clear instructions on setting up 14.04 with large hard drives?
'Large' as they would use GPT partitions? Are you using BIOS or UEFI?
> **bsliv said:**
> Are there clear instructions on setting up raid 1 with large drives? 
Software raid right? Take a look at these couple of guides: [Software Raid]("https://help.ubuntu.com/community/Installation/SoftwareRAID"), and [Server Advance installation]("https://help.ubuntu.com/12.04/serverguide/advanced-installation.html").

Hope it helps. Let us know how it goes.
Regards.

---

### Post by bsliv on 2014-04-22
Thanks for the reply despite my obvious signs of frustration.  

The [Server Advance installation]("https://help.ubuntu.com/12.04/serverguide/advanced-installation.html")[COLOR=#000000] looked like a good guide so I followed it word for word.  All went well until the instruction "Enter the partition size, then choose Primary, then Beginning."  Choosing Primary is not an option.  It goes straight from size to Beginning.  I continued anyway.  Further down it says to select the "Bootable flag:" line to change the value to "on".  Hmmmm.  I can select "bootable flag" but it won't change from off.

After the instruction "Once done select "Finish"", I get a message, "No root file system is defined.  Please correct this from the partitioning menu."  

The frustration continues.

Root file system?  No clue what that is supposed to be.  The instructions did have me change from Ext4 journaling file system to physical volume for RAID.  Physical volume for raid sounds like what I want.  Ext 4 journaling?  Can we be a bit more cryptic?  

Off to try the [/COLOR][COLOR=#000000] [/COLOR][Software Raid]("https://help.ubuntu.com/community/Installation/SoftwareRAID")[COLOR=#000000] instructions now.  


[/COLOR]

---

### Post by bsliv on 2014-04-22
I got through the first six step of [COLOR=#000000][COLOR=#000000] [/COLOR][/COLOR][Software Raid]("https://help.ubuntu.com/community/Installation/SoftwareRAID")[COLOR=#000000][COLOR=#000000] easy enough.  After selecting 'Configure Software RAID' I get the message, "Failed to create a file system.  The ext4 file system creation in partition #2 of scsi3 (0,0,0) (sdc) failed."  Then back to the previous menu to try it again with the same results.

IT SHOULD NOT BE THIS HARD!


[/COLOR][/COLOR]

---

### Post by papibe on 2014-04-22
Sorry to hear that.

The general procedure is shown in this video tutorial: [How to install Ubuntu in a RAID 0 array]("http://youtu.be/-x2rZe2Z9as?t=4m30s").

I hope that points you in the right direction.

Regards.

---

### Post by bsliv on 2014-04-22
> **papibe said:**
> You don't need a mouse to install "Ubuntu Server". The installer uses text mode so you only need a keyboard.

If you want to install the Desktop version, I don't think it would be possible to use the graphical installed without a mouse. However, there another installers called 'alternate', which works in text mode. You can find them [here]("http://www.ubuntu.com/download/alternative-downloads").

Yes if the OS partition won't be part of the raid (which is what I would do BTW).

Only if the OS will be located inside the raid. If not, you can create it later.

'Large' as they would use GPT partitions? Are you using BIOS or UEFI?

Software raid right? Take a look at these couple of guides: [Software Raid]("https://help.ubuntu.com/community/Installation/SoftwareRAID"), and [Server Advance installation]("https://help.ubuntu.com/12.04/serverguide/advanced-installation.html").

Hope it helps. Let us know how it goes.

Regards.

I'm trying 14.04. Yesterday I tried 13.xx and an older version that I used a year ago. I had issues with the older versions too but didn't document them. I don't think another version will help much.

I didn't want multiple partitions. I wanted simple. Having separate partitions for the os and user data sounds good but I don't want to complicate things at this point.

From what I've read GPT is necessary with 4TB drives and I've seen gpt somewhere while working with fdisk, or gdisk, or parted, or something like that. My pc has a bios. I think most do. UEFI? Universal efficient fuel injection? Unified electrical field interference? Huh?

Not going well.  I think my problem lies with my lack of understanding of the linux partitioning scheme.  Going thru auto mode creates 3 partitions, the main one or / or root, a swap, and another one (for boot loader?).  Each one has a different file system type unless using raid then they all have the same file system type.  Doesn't make sense.

---

### Post by bsliv on 2014-04-24
Another day wasted and I'm not much further.  I've tried so many different things my head is spinning.  It would be nice if I could try the right thing.  Tomorrow I get to tell my client I can't install software.  

I've tried 2 partitions, swap and /.  I've tried 3 partitions, swap, /, and biosgrub.  I've gone thru partitioning hundreds of times in the past few days.  The best help I've found so far is a youtube video in a language I can't understand using a older version that doesn't match up with this version.  Do I have to learn Spanish to install this OS?

---

### Post by mastablasta on 2014-04-24
> **bsliv said:**
> I'm trying 14.04. Yesterday I tried 13.xx and an older version that I used a year ago. I had issues with the older versions too but didn't document them. I don't think another version will help much.

I didn't want multiple partitions. I wanted simple. Having separate partitions for the os and user data sounds good but I don't want to complicate things at this point.

Multiple parittions (especially for system & data) on server would be a must if you ask me unless you plan to run OS from a different disk.[/QUOTE]

> 
From what I've read GPT is necessary with 4TB drives and I've seen gpt somewhere while working with fdisk, or gdisk, or parted, or something like that. My pc has a bios. I think most do. UEFI? Universal efficient fuel injection? Unified electrical field interference? Huh?

Not going well.  I think my problem lies with my lack of understanding of the linux partitioning scheme.  Going thru auto mode creates 3 partitions, the main one or / or root, a swap, and another one (for boot loader?).  Each one has a different file system type unless using raid then they all have the same file system type.  Doesn't make sense.

yes it is stemmign form lack of understanding of not just linux but some new hardware things as well. but don't worry we just need to find the right thing. the fact that you are using gpt is important as this is a very much new thing and works different from traditional mbr.

UEFI is different from BIOS. new motherbaords have UEFI mostly. [http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)

when searching for info you need to specifically state in your search that oyu want Raid 1 on GPT. yu may get better results such as:
[http://ubuntuforums.org/showthread.php?t=2109438](http://ubuntuforums.org/showthread.php?t=2109438)
[http://ubuntuforums.org/showthread.php?t=2102285](http://ubuntuforums.org/showthread.php?t=2102285)
[http://ubuntuforums.org/showthread.php?t=2201239](http://ubuntuforums.org/showthread.php?t=2201239)
[http://askubuntu.com/questions/342227/ubuntu-software-raid-gpt](http://askubuntu.com/questions/342227/ubuntu-software-raid-gpt)

etc.

to complicate things there is also UEFI secure boot: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

one thing you could try is Zentyal. this one has a GUI and you could try and set it up. i am not sure if version with 14.04 underneath it is out yet. i would put the OS on another disk and data separately in raid 1. if you plan to use mashcine only for LAMP you could just have the www folder on disk.  however i do not know much about raid & what is best for servers :-)

also it might be good to post what you are trying to do any why. perhaps there is a different and better solution/setup available.

edit: i've also noticed you are very misterious about your full setup, components etc. we are trying to give as much help as possible based on limited information provided.

e.g. this error "[COLOR=#000000]Failed to create a file system. The ext4 file system creation in partition #2 of scsi3 (0,0,0) (sdc) failed." [/COLOR]lead me here: : [http://askubuntu.com/questions/356522/filesystem-creation-fails-when-trying-to-install-ubuntu-over-windows](http://askubuntu.com/questions/356522/filesystem-creation-fails-when-trying-to-install-ubuntu-over-windows)

you could try with /boot or perhaps you even need /efi partition.

as well as this: [http://ubuntuforums.org/showthread.php?t=1875880](http://ubuntuforums.org/showthread.php?t=1875880)

---

### Post by bsliv on 2014-04-24
I woke up this morning without the frustration of last night but its returning.  I 'think' the partition table is ok but when it installs the base system I now get the message, "an error was returned while trying to install the busybox-initramfs package".  

I'm trying to setup a headless webserver with a raid 1.  I have a cheap new motherboard (Gigabyte 78lmt-s2p), amd cpu, 4gb ram, identical dual 4tb hard drives.  There is no cd/dvd drive, no mouse, no expansion cards.  

The motherboard has a cmos setup option of Native IDE, AHCI, and RAID.  I've tried all 3 but tend to leave it on Native IDE to try to reduce complexity.  I'm trying to install off a usb stick.  The stick had 12.04 on it but the install didn't work, can't remember why.  So I tried 13.10.  It didn't work either.  So I tried 14.04 desktop but it didn't work well without a mouse.  Now I'm using ubuntu-14.04-server-amd64.iso.

It appears I lack intelligence so I think I need someone to hold my hand for each keystroke.  Starting at the beginning.

Step 1:  Booting from the usb, 12 menu items appear.  Default, Install, Command-line install, Expert install, Command-line expert install, Install Ubuntu Server, and Multiple server install with MAAS.  So there are 7 install options.  I've tried them all except with MAAS, I don't know what MAAS is.  Which should I use?

---

### Post by bsliv on 2014-04-24
8 more hours wasted and I'm going backwards.

Is there a better place to ask for help?

---

### Post by bsliv on 2014-04-24
I can get the system to boot by eliminating the second drive and setting the cmos setup to ahci.  

Errors I've encountered along the way:
The failing step is install the grub bootloader on a hard drive.
Unable to install the generic kernal.
An error was returned while trying to install the busybox-initramfs package...
Can't install the system.
Objects being thrown about the room.

By process of elimination, I've determined the cmos should be set for ahci, not naive ide or raid.  Correct?
My working drive had 3 partitions:  /, swap, and biosgrub.  I think this has to be correct.  It would be nice be have this confirmed tho.
I can't seem to get by the busybox error now.

---

### Post by bsliv on 2014-04-24
I've determined Ubuntu 14.04 cannot be successfully installed from a usb stick with 2 drives attached, raid or no raid, partition on the second drive or not.  

Can anyone point to clear instructions on adding a second drive as a raid 1 device to a working system using 4TB drives?

---

### Post by mastablasta on 2014-04-25
does the install work if you have only one disk inside? 

have you seen this? : [URL="http://www.gigabyte.com/support-downloads/faq-page.aspx?fid=1526&pid=3833"]http://www.gigabyte.com/support-downloads/faq-page.aspx?fid=1526&pid=3833
[/URL]
did you update the BIOS (or does this have UEFI)?[http://www.gigabyte.com/products/product-page.aspx?pid=3833#bios](http://www.gigabyte.com/products/product-page.aspx?pid=3833#bios) 

[TABLE="class: tblborder tbl_driver, width: 900, align: center"]
[TR]
[TD]F1
[/TD]
[TD]1.12 MB
[/TD]
[TD]2011/03/28
[/TD]
[TD][Asia]("http://download.gigabyte.asia/FileList/BIOS/mb_bios_ga-78lmt-s2p_v.3.x_f1.exe") [China]("http://download.gigabyte.cn/FileList/BIOS/mb_bios_ga-78lmt-s2p_v.3.x_f1.exe") [America]("http://download.gigabyte.us/FileList/BIOS/mb_bios_ga-78lmt-s2p_v.3.x_f1.exe") [Europe]("http://download.gigabyte.eu/FileList/BIOS/mb_bios_ga-78lmt-s2p_v.3.x_f1.exe") Europe(Russia) : [FTP]("ftp://download.gigabyte.ru/bios/mb_bios_ga-78lmt-s2p_v.3.x_f1.exe") / [Http]("http://download.gigabyte.ru/bios/mb_bios_ga-78lmt-s2p_v.3.x_f1.exe")
[/TD]
[TD]

[LIST=1]
[*]First release
[*]**3TB HDD support**
[/LIST]
[COLOR=red]* Please use the latest [@BIOS]("http://download.gigabyte.asia/FileList/Utility/motherboard_utility_gbttools_gbt_atbios.exe") or FLASHSPI.EXE to reflash BIOS 

[/COLOR][/TD]
[/TR]
[/TABLE]

does the mobo even support 4TB hard disks?

---

### Post by bsliv on 2014-04-25
[I][COLOR=#000000]does the install work if you have only one disk inside? 
[/COLOR][/I][COLOR=#000000]Yes, no issues at all.  I'm currently working on adding a raid drive to a working system.

[/COLOR][I][COLOR=#000000]did you update the BIOS (or does this have UEFI)
[/COLOR][/I][COLOR=#000000]No, I didn't update the bios.  Not exactly sure what uefi is about but nothing in cmos mentions uefi. Can't use a mouse in cmos setup.  I think my Blazer has it tho.

[/COLOR][I][COLOR=#000000]does the mobo even support 4TB hard disks?
[/COLOR][/I][COLOR=#000000]df -h show the size at 3.6T, 3.4T available, so I'd have to say yes, the mobo supports 4TB drives.


On my working, 1 drive system there are 3 partitions.  During the process of adding the 2nd drive in a raid 1 array, I tried copying the /boot partition from sda to sdb.  It was only a 1mb partition and the error say insufficient disk space.  I made the boot partition 4mb this time.  No cutting/pasting and typing on a crappy keyboard takes a long time.

[/COLOR]

---

### Post by bsliv on 2014-04-25
It should not be this hard.

---

### Post by bsliv on 2014-04-25
I was mistaken and "efi cd/dvd boot option" is in cmos setup.  Is was set for auto.  Should it be efi or non-efi?  Is efi good?  What do i do different?

---

### Post by bsliv on 2014-04-25
I'm giving up, at least for the day.  20 hours sitting here today.  Frustration doesn't begin to describe it.

---

### Post by mastablasta on 2014-04-26
aha it might be using UEFI. i posted a link before. UEFI is new&imporved BIOS. disabling it should switch it into BIOS mode. however if it works using it it could be left on. but you might need an efi partition: [https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

sicne you try to do things the BIOS way i would disable efi. furthermore check the links i posted from tghe motherboard manufacturer. make sure your UEFI/BIOS is at the porpper version. it might support the disk, but does it support 4 TB disks in raid? it doesn't seem so. since everytime you try and create RAID you get errors. an di wonder if the errors are caused by the os or from BIOS/UEFI.

as you've said - it should not be this hard.

edit: if you need help and troubleshooting faster than people reply on this forum try the IRC channel. there might even be a dedicated server channel where people that do server stuff hang out. and response can be really fast.:
[http://community.ubuntu.com/help-information/](http://community.ubuntu.com/help-information/)

list of channels: [https://wiki.ubuntu.com/IRC/ChannelList](https://wiki.ubuntu.com/IRC/ChannelList)
[TABLE]
[TR]
[TD][#ubuntu-server]("irc://irc.freenode.net/ubuntu-server")
[/TD]
   [TD]Ubuntu server help and discussions
[/TD]
   [TD]soren
[/TD]
[/TR]
[/TABLE]

---

### Post by bsliv on 2014-04-26
I appreciate the help.  

It appears this motherboard is a 'hybrid'.  The help next to the cmos option, "EFI CD/DVD Boot Option" says EFI is essential to support > 2.2tb hdd.  So I took it off Auto and set it to EFI.  I physically disconnected the second drive and installed on the first drive.  I added the second drive using a mount point.  I figured I would create a cron job to rsync the 2 big partitions.  Not an ideal solution but a work around.

Even tho I enabled EFI in cmos, Ubuntu reports it is "Installed in Legacy mode."  GNU GRUB version 2.02~beta2-9 comes up when booted.  

There might be an updated bios available but not sure.  I'm using the F3 bios with a 2012 date.  Gigabyte's web site says the F3 bios should have a 2011 date.  The F4 bios says it has modified EFI compatibility.  Gigabyte offers a windows update and two updates that involve a floppy disk.  Floppy?  DVD's are old tech.  I'm not going to install windows and don't think I have a working floppy drive.  

I've read all the links from each post in this thread (and a whole lot more) and still a bit fuzzy on EFI.  I told my system to use it and it didn't.  If it didn't use it, it should only see 2.2tb but it sees all 4tb.  What does an EFI partition look like?  

I got a day and a half to decide how to configure this box.  I'd like to get raid 1 working so that if 1 drive goes down the second drive can boot the system and continue as normal.  But that doesn't seem possible.  I'm open to suggestions.

---

### Post by aapman on 2014-08-02
I had a similar problem, here is my workaround.


[LIST=1]
[*]Make a 1 GB partition on each disk;
[*]Make a 6 GB partition on each disk (I have 6 GB of RAM);
[*]Partition the rest of the free space on each disks;
[/LIST]

Now setup the partitions:
[LIST=1]
[*]Use the ONLY ONE of the 1 GB partitions for the boot partition. Mount one as '/boot';
[*]Set the 6 GB and large partitions as partitions for RAID;
[*]Use the 6 GB RAID partitions for 'swap';
[*]Use the large partitions as '/';
[*]Leave the rest of  1 GB  partitions unused;
[/LIST]

Now continue the installation without errors. The only drawback is that the boot partition is not part of a RAID. If the disk with the boot partition fails, install a boot partition on one of the other disk's 1 GB partition.

Hope this helps...

---

