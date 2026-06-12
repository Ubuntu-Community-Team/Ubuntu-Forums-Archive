---
title: "Boot options and partitions UEFIDualBIOS (UEFI not enabled)"
date: 2013-08-23
forum: Installation &amp; Upgrades
---

### Post by ManudaNZ on 2013-08-23
Firstly I have been trying for hours trying to understand how to install Ubuntu. All I can say is that this is an extreme mission and to me almost starting to feel like it is a futile exercise for a complete new Linux user.
 
WHY IS THIS SO HARD??? Why is this so hard?

I have been playing with Dos and computers since before Dos was invented (that's right - my First computer was a ZX Spectrum 32bit, used a tape drive to install programs into ram, no HDD etc.. used Basic to programme my own games to use on it etc..) So I am no slouch to partitions, Bios etc.

However, Ubuntu has me pulling my freakin hair out and making me extremely frustrated. the documentation is a JOKE. and very annoying to delve into. Every step i keep saying, Why is this so hard when Microsoft make lidfe so easy and simple. Anyhow rant over.. A bit more background info.

I purchased my computer 2 months before Win8 came out so had Win7home installed. Upgraded to Win8 the day it came out. havn;t regretted it ever since (well maybe the Metro UI sucks but apart from that it is fine) The reason I want to use Linux is my daughter is about to start ina new age school that has Linus based computers. I want to be able to have a linux based system so she can do work at home on the same programs that she uses at school, like kdenlive movie editing software etc.. which are generally only linux based.

I tried the wubi.exe route but came up with error upon reboot "Boot is not recognised" and "Press ENTER to go to OS and then Windows will just start when I hit ENTER. Help docs say I have Secure boot, But as I have older settings my Bios doesn't support Secure boot so this is nonsense.

Righto, now onto the frustrating parts.

OK computer specs:

motherboard: Gigabyte GA-Z77M-D3H-MVP.
Chip: Intel i7-3770, 3.4Ghz.
Memory: 8GB DIMM
BIOS system; UEFI Dualboot version F4.

After reading lots of Stuff I found this article here which seemed to be the correct thing to do. [https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_Quickly_and_Easily_via_Trial_and_Error](https://help.ubuntu.com/community/UEFI#Installing_Ubuntu_Quickly_and_Easily_via_Trial_and_Error)

So I went into Disk management and then shrunk my windows partition to allow 200GB space to install  Ubuntu. See image.
I notice there is a 100MB EFI partition. Is this the Windows Boot loader? I cant find any documentation/questions regarding what this is for.

[IMG]http://i.imgur.com/BVveaDH.jpg[/IMG]




So far so good. So I change Bios to boot on my DVD drive.

Insert the Ubuntu disk (64bit desktop I burned from iso). Got to Try/Install Unbuntu. Hit Install. 

Now when I go into the next screen it only asks me for 2 options. Wipe clean and install, or Do something Else.

It doesn't ask me to install alongside my windows??? Why is this?

My only assumption is that by changing the BIOS 1st boot option to DVD it now doesn't recognise windows boot loader at all.

This is where most documentation falls over as it assumes you have the 3 options and not the 2 options. So I end up with going to the option "Do something else"

Now what the **** do I do? I am a novice in Linux and there are hundreds of options and a very alien looking dialog box.

For a start I now see 4 partions: and not 3 like I see in the windows mgmnt.

(EDIT: Just did this again to get the exact settings I see in the Partition setup dialog.)

this is what I see

/dev/sda
free space,          ,1MB
/dev/sda1, fat32  ,104MB        33MB used
/dev/sd2,            ,104MB,       unknown used
/dev/sd3, ntfs      ,790247MB   300MB used
free space,          ,209716MB   free space


So how do I install from here Ubuntu with Dual boot facility?

What do I select as My / (root) 

I am thinking that I want to make a root, swap and home partitons but not sure how big I need to make them.

I am thinking / (root) 8Gb, /Swap 16Gb, /home = rest of the free space left. Does this sound right?

Once I have the correct Partitions, I think I can manage after that, but My Bios puts a spanner in the works. And the 1Mb free space and fat32 drives throw me as to what they could be. I am guessing the fat32 is the windows boot loader. 

I am also guessing/hoping that once I install Ubuntu I can use the GRUB loader to set up my Dual boot options. But I can't find the correct help about doing this successfully.

Thanks for any help.

Manu.da

EDIT: [http://paste.ubuntu.com/6019759/](http://paste.ubuntu.com/6019759/)

---

### Post by oldfred on 2013-08-24
UEFI is a whole different system than BIOS which we have had for over 30 years. Most users have not seen anything else than BIOS. But Apple converted to UEFI when they changed to Intel processors, but most Apple users do not install new systems.

UEFI uses the new gpt partitioning table, not the old MBR(msdos) partitioning with 4 primary partition limit.
 [http://en.wikipedia.org/wiki/GUID_Partition_Table](http://en.wikipedia.org/wiki/GUID_Partition_Table)

Windows requires  another unformatted partition.
      
 Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

 Order on drive is important:
[http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition](http://en.wikipedia.org/wiki/Microsoft_Reserved_Partition)

Windows 8 also uses fast boot which really is just hibernation. That is always on, and must be turned off to correctly install and dual boot Ubuntu.
      
 WARNING for Windows 8 Dual-Booters
[http://ubuntuforums.org/showthread.php?t=1953674](http://ubuntuforums.org/showthread.php?t=1953674)
It defaults shutdown to a hybrid hibernation/off state for fast boot 
[http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8](http://www.kapilarya.com/how-to-enable-disable-fast-start-up-in-windows-8)

Instead of booting from the MBR with BIOS, UEFI uses an efi partition for booting. It is a lot larger than the old MBR so more boot code is allowed and multiple boot loaders coexist, each in different folders. You have to choose in UEFI menu which system (folder) to boot from. Somewhat like having multiple hard drives each with a different boot loader in each MBR.

 efi system partition should be a 200-300 MiB FAT32 partition that's flagged as an EFI system partition (ESP) and must be the first partition. In libparted-based tools, you'd give it a "boot" flag (which is entirely unrelated to the MBR boot/active flag, although libparted makes them look the same).  If you have one do not create another.

Use Windows disk tools to shrink Windows and reboot a couple of times to make sure it has run chkdsk and updated itself to its new size.
Make sure fast boot and secure boot are off. 
Best to boot Ubuntu installer in UEFI mode, not CSM/BIOS/Legacy mode.
      
 UEFI Compatibility Support Module (CSM), which emulates a BIOS mode 

You also will need to run Boot-Repair after install to fix some grub  bug issues as it does not create correct chain load entries to boot Windows.

Best to make full backups of your Windows install and a Windows repair flash drive.

 Windows 8 UEFI repair USB must be FAT32
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)
[http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/](http://social.msdn.microsoft.com/Forums/en-US/samsungpcgeneral/thread/e7ed293e-b565-44ee-a536-166dddf32205/)
[http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/](http://www.ghacks.net/2012/11/01/how-to-create-a-windows-8-system-repair-disc/)

      
 For the Total space you want for Ubuntu:
Ubuntu's standard install is just / (root) & swap, but it is better to add another partition for /home if allocating over 30GB.:
Only if gpt -  all partitions in gpt are primary:
gpt: 250 MB efi FAT32 w/boot flag (for UEFI boot or future use for UEFI, you only can have one per drive, so if already existing do not attempt another)
gpt: 1 MB No Format w/bios_grub flag (for BIOS boot not required for UEFI)
for gpt(GUID) or MBR(msdos) partitioning
Ubuntu partitions - smaller root only where hard drive space is limited.
If total space less than about 30GB just use / not separate /home or standard install.
1. 10-25 GB Mountpoint / primary or logical beginning ext4(or ext3)
2. all but 2 GB Mountpoint /home logical beginning ext4(or ext3)
3. 2 GB Mountpoint swap logical

   Depending on how much memory you have you may not absolutely need swap but having some is still recommended. I do not hibernate (boots fast enough for me) but if hibernating then you need swap equal to RAM in GiB not GB. And if dual booting with windows a shared NTFS partition is also recommended. But you usually cannot create that as part of the install, just leave some space. Or partition in advance (recommended).
One advantage of partitioning in advance is that the installer will use the swap space to speed up the install. Thanks Herman for the tip.
[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

More info and details of installs by different users in link in my signature.

---

### Post by ManudaNZ on 2013-08-24
This is all wonderful information. But it doesn't help in the slightest.

Firstly. If I try to boot in UEFI: mode from the Desktop(64) cd, Ubuntu wont load. I just get blank screen with the white underscore at top of screen.

However if I set Bios to boot from CD, then insert CD as I start machine, then Ubuntu installer loads fine, The "Try Ubuntu" option works fine. I have installed flash, listened to music on the web (posted this on here) etc.. So Ubuntu doesn't work in UEFI 

When I tried to create partitions I created a / root @ 8gb, then Created a /home with the rest of free space and selected my / (root) partition to install ubuntu on, and hit "Install". An Error came up that I didn't have a boot sector?

---

### Post by oldfred on 2013-08-24
Only 8GB is pretty small for / (root), I normally suggest 10 to 25GB and only the smaller amount for small hard drives.
You are forcing a BIOS install which will not work with dual booting Windows in UEFI. You can later convert to UEFI with Boot-Repair but will still have the video issue once installed.

When you boot in UEFI mode, you should be grub menu. At grub menu press e for edit, scroll to linux line and replace quiet splash with nomodeset. That works with most video issues but what video do you have.

       How to set NOMODESET and other kernel boot options in grub2 - both liveCD & first boot, but different 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)
Info on other boot parameters
[http://www.kernel.org/doc/Documentation/kernel-parameters.txt](http://www.kernel.org/doc/Documentation/kernel-parameters.txt)

---

### Post by ManudaNZ on 2013-08-25
geforce GTX550

---

### Post by ManudaNZ on 2013-08-25
Now I get new error.

Boot error:

Could not read file.

then it does a screen dump wall of text.

Sigh.

Checked Disk. It had 1 error.

---

### Post by ManudaNZ on 2013-08-25
OK Downloaded new ubuntu this being Release 12.4.3...
This works fine. I use the Shift+restart command to boot from DVD amd64 Desktop Bootdisk.

I didn't ned to use the nomodeset and all seems to be working great.

Went with Try ubyntu option first.

Opened terminal tested EFI mode using: [ -d /sys/firmware/efi ] && echo "Installed in EFI mode" || echo "Installed in Legacy mode" 

It reported "Installed in EFI mode"

OK Just to be clear so I don't stuff up my Win8..

 When I go to install Ubuntu. It Still doesn't come up with the option to Install Alongside Windows, So i choose "Something else" category.

From the list I provided above, It seems that I already have a boot protected partition (assuming this is the unknown 1Mb area.)
It also has an EFI partition sda1, fat32, 104Mb.
I have no idea what sda2 is for. so we will just ognore this for now. and then we see we have the windows partition.

Now. At the bottom of the Dialog it also asks for "Device for Boot loader instructions"

it defaults to /dev/sda, but If I am understanding the help files/documented advice, I now select the sda1 as the partition for my boot deice?

I can take my 200Gb free space and make a /(root) partition [Ext4, journal] with that and just have linux use that for everything.

Is this all correct?

Then when it is installed I use the boot repair and viola I have the option of Ubuntu or Windows to boot into??

I just want to be ultra sure as I don't want to have to lose my windows install. I have it backed up--but still, I'd rather it stay intact.

Thanks for your advice so far.

Regards
Manu

---

### Post by oldfred on 2013-08-25
In post #2 I have info on the Microsoft reserved partition.

I think with UEFI installs, saying to install to sda will automatically install grub2's boot loader to the efi partition as that is the only place it is supposed to be installed. With BIOS it can be in several places although MBR of sda is most correct.

One large / (root) partition will work but best to also have some swap. That would be a default install. If you deleted the partitions from first install or just had the space as unallocated then the install side by side should work.
And you do need Boot-Repair to fix up the os-prober bug issue to add correct chain load entries to boot Windows (or you can manually add entries your self).

---

### Post by ManudaNZ on 2013-08-26
I don't get the "Side by Side" Installation option come up on my computer at all. This is my main problem..

If I got this option in the menu then I wouldn't have any problems installing Ubuntu.

BuT (like I said numerous times.) I don't get this option..

Never mind.. 

I tried doing this about 9 months ago on another computer and I had similar problems. CD doesn;t work, crashes upon ""Try ubuntu first" etc...

I guess this is a sign that Linux is just not for me.

Maybe one day when Ubuntu make some decent instructiions with Installs that work properly I might give it another try in the future. But untill then I give up and stay with Windows.

GL all.

---

