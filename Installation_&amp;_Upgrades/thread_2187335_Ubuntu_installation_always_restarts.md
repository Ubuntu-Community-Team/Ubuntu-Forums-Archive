---
title: "Ubuntu installation always restarts"
date: 2013-11-11
forum: Installation &amp; Upgrades
---

### Post by childintime on 2013-11-11
[COLOR=#ff0000]EDIT: This issue is fixed, but I still cannot access neither Ubuntu nor my Windows, I am stuck in Grub console, see last post if you are interested.[/COLOR]

Hello,


I downloaded ubuntu-12.04.3-desktop-amd64.iso and mounted it to USB. I restart my laptop, select Install Linux and select language, then it says I have no internet, I press "Continue", and then I click "Install Ubuntu alongside Windows 8" and click "Continue", the computer just restarts and I see the again the same Try-Ubuntu-or-install-it menu.
And hence I cannot install Ubuntu. I check md5 hash for iso and it's correct. I also tried to burn iso with unetbootin. Am I supposed to remove USB after clicking continue? 

I read many thread with same problem, but no concrete solution!

Thanks.

---

### Post by fantab on 2013-11-11
You need to provide more info about your computer, like its hardware, model etc.
Did Windows 8 come preinstalled or did you install it yourself?
Can you 'Try Ubuntu Without installing"?

---

### Post by childintime on 2013-11-12
I installed Windows 8 myself, it's new Asus laptop. I think the problem is that I need to allocate space on hard drive manually for ubuntu. I made some free unallocated space on hard disk, and then go to installation. First very strange that "Install alongside Win8 button is gone". Anyways, I press on "Something Else" to try to define installation myself. 

I read that I need to choose that free unallocated space and press "Add", but when I press on free space Add button is inactive! Here is pic about what I am talking about: [http://i.imgur.com/ApWEfYF.jpg](http://i.imgur.com/ApWEfYF.jpg)

---

### Post by fantab on 2013-11-12
Not sure what is happening there, however, you can boot with Ubuntu DVD/USB and 'Try Ubuntu without installing'... open Gparted and make your partitions. IMO you are cramped for space on that HDD with two OS.
Do you have more than one HDD or SSD?
Also if you have 'FastStartup' enabled in Windows8, [Disable Faststartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").

---

### Post by childintime on 2013-11-12
I couldn't edit partitions because I had 4 primary already :mad:

Anyways, I partitioned everything, made space for: 
/
/boot
/home
swap area

And it all goes well until few minutes into installation comes the error: [COLOR=#000000]The 'grub-efi-amd64-signed' package failed to install into /target/
[/COLOR][COLOR=#000000]
[/COLOR][COLOR=#000000]

[/COLOR]

---

### Post by fantab on 2013-11-12
From Live Ubuntu DVD/USB post the output of:

```
sudo parted -l
sudo fdisk -l
```

> error: [COLOR=#000000]The 'grub-efi-amd64-signed' package failed to install into /target/[/COLOR]

This error can happen if you are trying to install Ubuntu in UEFI mode on a 'msdos' Disk or on a GPT Disk without EFI partition..... the output of the above will gives us more details.

---

### Post by childintime on 2013-11-13
here we go :)

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
Partition Table: msdos


Number  Start   End    Size    Type      File system     Flags
 1      1049kB  368MB  367MB   primary   ntfs            boot
 2      368MB   210GB  210GB   primary   ntfs
 3      210GB   592GB  381GB   primary   ntfs
 4      592GB   746GB  154GB   extended
 8      592GB   602GB  10.0GB  logical   ext4
 5      602GB   606GB  3999MB  logical   linux-swap(v1)
 6      606GB   746GB  140GB   logical   ext4
 7      746GB   746GB  299MB   logical   ext2




Model: PQI Cool Drive U320 (scsi)
Disk /dev/sdb: 2093MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos


Number  Start   End     Size    Type     File system  Flags
 1      16.4kB  2093MB  2093MB  primary  fat16        boot




Warning: Unable to open /dev/sr1 read-write (Read-only file system).  /dev/sr1
has been opened read-only.
Error: /dev/sr1: unrecognised disk label           


 


ubuntu@ubuntu:~$ sudo fdisk -l


Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 4096 bytes
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2bfb4dc8


   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   410318847   204800000    7  HPFS/NTFS/exFAT
/dev/sda3       410318848  1155399679   372540416    7  HPFS/NTFS/exFAT
/dev/sda4      1155401726  1456766975   150682625    5  Extended
Partition 4 does not start on physical sector boundary.
/dev/sda5      1174933504  1182744575     3905536   82  Linux swap / Solaris
/dev/sda6      1182746624  1456181247   136717312   83  Linux
/dev/sda7      1456183296  1456766975      291840   83  Linux
/dev/sda8      1155401728  1174933503     9765888   83  Linux


Partition table entries are not in disk order


Disk /dev/sdb: 2092 MB, 2092957184 bytes
129 heads, 32 sectors/track, 990 cylinders, total 4087807 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disk identifier: 0xf842da10


   Device Boot      Start         End      Blocks   Id  System
/dev/sdb1   *          32     4087806     2043887+   6  FAT16

---

### Post by fantab on 2013-11-13
> dev/sda4      1155401726  1456766975   150682625    5  Extended
Partition 4 does not start on physical sector boundary.

**[FIXPARTS]("http://www.rodsbooks.com/fixparts/")** will take care of it for you.

You may have installed grub-efi instead of grub-pc.
**[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")** should fix it for you, run it from Ubuntu DVD/USB. When you use Boot-Repair make a note of LINK to BootInfo-Summary which it creates. If problems persist post the LINK here.

Edit: I see that you have created an ext2 partition, any particular reason for this? If not, use Ext4 as its the latest.
Only 10GB for Ubuntu is bit less, make it 20-25GB.

---

### Post by childintime on 2013-11-13
Well.. couldn't make fixparts to work, but I've used boot-repair and i could in fact install ubuntu succesfully. Now used ext4 for /boot as well as 30Gb space for ubuntu itself.

That said after I install, rebooted and grub didn't launch and I saw message: Error: file not found. Grub rescue>_

I googled that for some time and I think I managed to fix, because now it launched into this page:
[INDENT]   Minimal BASH-like line editing is supported. For the first word,  TAB lists possible command completions. Anywhere else TAB lists possible  device or file completions.
      GRUB>


Here i can type commands, googled for some time how to fix, but no luck as of yet.

fantab, thanks for you help.

 [/INDENT]

---

### Post by fantab on 2013-11-13
> **fantab said:**
> 
You may have installed grub-efi instead of grub-pc.
**[Boot-Repair]("https://help.ubuntu.com/community/Boot-Repair")** should fix it for you, run it from Ubuntu DVD/USB. **When you use Boot-Repair make a note of LINK to BootInfo-Summary which it creates. If problems persist post the LINK here.**


Can post the link to BootInfo Summary? If you don't have it then run Boot-Repair, click on Boot-Info summary and post the Link.

You can't really tell if Fixparts has worked or not. The fact that you could install Ubuntu now suggests that it may have worked.

---

### Post by childintime on 2013-11-13
I couldn't even manage to run Fixparts. Anyways, here is the link: [http://paste.ubuntu.com/6410064/](http://paste.ubuntu.com/6410064/)

But keep in mind i made this boot repair long ago, after that I used many different commands to fix various grub issues, and now when I run boot repair it does not finish successfully for some reason, hence does not provide link to summary.

Maybe I should try running boot repair with "Restore MBR" option?

---

### Post by fantab on 2013-11-13
No, you haven't run Fixparts. Try it again.

Also try boot-repair again from Live DVD/USB, make sure that you boot Live Ubuntu in PMAP/Legacy mode and NOT in EFI mode.

But before you do that, Have you disabled '[FastStartup]("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html")' in Windows8... 
Have you disabled '[fastboot]("http://www.intel.com/support/motherboards/desktop/sb/CS-032034.htm")', if you have intel mobo.

---

### Post by childintime on 2013-11-13
I don't understand, I installed fixparts, but when I run command it says: "The program 'fixparts' is currently not installed.  You can install it by typing:
sudo apt-get install gdisk". But at the same time tutorial says "do not use gdisk".

> make sure that you boot Live Ubuntu in PMAP/Legacy mode and NOT in EFI mode.

How can I do that?

And FastStartup is indeed disabled, and option fastboot is not existing in BIOS of my Asus motherboard.

---

### Post by fantab on 2013-11-13
Forget Fixparts; you can adjust the Extended Partition manually with Gparted. First, BACKUP all your Important DATA externally.
```
fdisk -l:

Disk /dev/sda: 750.2 GB, 750156374016 bytes
255 heads, 63 sectors/track, 91201 cylinders, total 1465149168 sectors
Units = sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): **512 bytes / 4096 bytes**
I/O size (minimum/optimal): 4096 bytes / 4096 bytes
Disk identifier: 0x2bfb4dc8

Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *        2048      718847      358400    7  HPFS/NTFS/exFAT
/dev/sda2          718848   410318847   204800000    7  HPFS/NTFS/exFAT
/dev/sda3       410318848  1155399679   372540416    7  HPFS/NTFS/exFAT
/dev/sda4      [COLOR=#b22222]**1155401726**[/COLOR]  1456766975   150682625    5  Extended
***Partition 4 does not start on physical sector boundary.***
/dev/sda5      1174933504  1182744575     3905536   82  Linux swap / Solaris
/dev/sda6      1182746624  1456181247   136717312   83  Linux
/dev/sda7      1456183296  1456766975      291840   83  Linux
/dev/sda8      1155401728  1174933503     9765888   83  Linux

```

Look at the number in bold red, 1155401726. Now these numbers should be divisible by 8, but they are not, especially the first one.
So you need to use Gparted and adjust the first number to the nearest possible number divisible by 8, which in your case should be **1155401720**. Using Gparted adjust the first number accordingly.
Sometimes these errors don't matter but since you are having trouble lets fix it to rule out the possiblity of this error causing boot problem.

This will help you understand booting in EFI and Non-EFI mode:
[https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode](https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_HDD_in_EFI_mode)

> UEFI/Legacy mode:
BIOS is EFI-compatible, and is setup in EFI-mode for this live-session.

Check and Disable EFI-mode in BIOS/UEFI if its enabled and switch to 'Legacy/CSM'.
Because you have not installed Windows in EFI-mode, nor does your HDD with its present setup support EFI booting.

If Re-installing Ubuntu is an option then Re-Install it with 'Something Else' option.

---

### Post by childintime on 2013-11-14
Thanks so much fantab

Anyways, first of all now trying to backup  my data, but unsuccessfuly so far. As you can see here:  [http://i.imgur.com/SXaqHrR.png](http://i.imgur.com/SXaqHrR.png) I cannot access or mount those windows  partitions, don't know why.

---

### Post by fantab on 2013-11-14
Try opening Nautilus as root:

```
sudo nautilus
```
Now try to open the NTFS/Windows partition.

If you Still can't then I hope you still have that Windows 8 Install DVD... We will need that. We are going to repair Windows boot so that Win can boot on its own. 
Follow the instructions in the Link below.
[http://windows8themes.org/using-bootrec-exe-to-fix-mbr-in-windows-8-master-boot-record.html](http://windows8themes.org/using-bootrec-exe-to-fix-mbr-in-windows-8-master-boot-record.html)

This will overwrite GRUB. If windows starts booting then you can do Backups safely.

EDIT:** After BACKUP**, are you open to re-installing Windows? Because, if you are, then change the 'msdos' disk to GPT which has definite and longterm advantages over MBR. For one, there is no need of any Extended Partition as GPT can have more than 100 Primary partitions. From GPT Windows can only boot in UEfI mode, which again has advantages over older BIOS and is the future.
Advantages of UEFI: [http://windows.microsoft.com/en-US/windows-8/what-uefi](http://windows.microsoft.com/en-US/windows-8/what-uefi)
Advantages of GPT: [https://wiki.archlinux.org/index.php/GUID_Partition_Table](https://wiki.archlinux.org/index.php/GUID_Partition_Table)

---

### Post by childintime on 2013-11-14
```
sudo Nautilus
``` launches this: [http://i.imgur.com/gyEIb36.png](http://i.imgur.com/gyEIb36.png) where i can't find anything.

I have few questions before doing what you told. If i repair windows, and launch what about Ubuntu, will i need to reinstall it or not? Or can I then fix Grub? If I need to reinstall it, i have no guarantees that I won't run into same problems as first time, and having ubuntu is something I really want. 

Also how do you know I am not using UEfI right now? Just wondering, it's new laptop, with new windows 8. When I press F2 while booting i go into that configuaration mode (Like BIOS), it does not even say BIOS anywhere. :wink:

---

### Post by fantab on 2013-11-14
> **sladeinflame7 said:**
> 

I have few questions before doing what you told. If i repair windows, and launch what about Ubuntu, will i need to reinstall it or not? Or can I then fix Grub? If I need to reinstall it, i have no guarantees that I won't run into same problems as first time, and having ubuntu is something I really want. 

Also how do you know I am not using UEfI right now? Just wondering, it's new laptop, with new windows 8. When I press F2 while booting i go into that configuaration mode (Like BIOS), it does not even say BIOS anywhere. :wink:

We can fix Ubuntu later. Right now, you want to **Backup your DATA**. And don't worry we will get Ubuntu up and running unless there is some extraordinary problem which this forum cannot solve.
There is however [another way]("http://superuser.com/questions/352157/mount-ntfs-windows-partition-on-ubuntu-live-cd") you can try to mount Windows partition from Ubuntu Live, but I wouldn't recommend it now. I suspect that your Windows did NOT shut down properly, and is probably also the cause of your BOOT problems. So If we force to mount windows partitions it might corrupt partition we are trying to mount. "Better safe than sorry", **you have DATA to save**.

Also If you repair Windows Boot and are able to boot then perhaps you can shut it down properly. Windows 8 with 'Faststart up' feature does NOT actually Shut down, it goes into "advanced hibernation". And this causes boot issues when dual-booting.
So once you are into Windows double check and [DISABLE 'FASTSTARTUP']("http://www.eightforums.com/tutorials/6320-fast-startup-turn-off-windows-8-a.html").

Now, if you look at the output of the 'parted -l' from the BootInfo-Summary in your earlier post:
```

parted -l:

Model: ATA ST750LM022 HN-M7 (scsi)
Disk /dev/sda: 750GB
Sector size (logical/physical): 512B/4096B
**Partition Table**: [COLOR=#b22222]**msdos**[/COLOR]
```

...you will see that the Partition Table on the Hard Disk is 'msdos'. With 'msdos' you can only boot in 'Legacy/BIOS/CSM' and NOT in UEFI. To boot in UEFI you need GUID Partition Table, GPT.
Windows can only boot in EFI mode from GPT Disk, while Ubuntu/Linux OS can boot from GPT in both EFI and Legacy modes.
This will explain more about UEFI [Unified Extensible Firmware Interface]:
[http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement](http://www.extremetech.com/computing/96985-demystifying-uefi-the-long-overdue-bios-replacement)
This should tell you more about Ubuntu's booting with EFI:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

Generally MOST newer computers, and more particularly newer Motherboards, HAVE UEFI instead of BIOS. UEFI is a STANDARD now.

It is still YOUR decision whether you want to boot in UEFI or NOT.

---

### Post by childintime on 2013-11-15
Thanks! So like you said, I fixed MBR, booted Windows 8 and done backup of my data. I also checked to make sure and I am indeed running Legacy BIOS.

What's my next step, as far as I understand I need to convert to GPT disk. For that in Disk Management I need to delete volumes, but how do I delete System reserved and C partitions?

And then I need to change Legacy BIOS to UEfI, but I didn't find such option in my bios.

---

### Post by fantab on 2013-11-15
> **sladeinflame7 said:**
> Thanks! So like you said, I fixed MBR, booted Windows 8 and done backup of my data. I also checked to make sure and I am indeed running Legacy BIOS.

What's my next step, as far as I understand I need to convert to GPT disk. For that in Disk Management I need to delete volumes, but how do I delete System reserved and C partitions?

And then I need to change Legacy BIOS to UEfI, but I didn't find such option in my bios.

Thats good, you have your data backed up.

Alright, What laptop brand and model do you have? Did Win8 come pre-installed or was it Win7?

In the BIOS find something like 'Boot Configuration', it should be under header 'Boot'. Then Look for 'Boot mode' check to see if you have UEFI listed there as an option. Confirm this. 
There is no point in converting it to GPT if you don't have that option. It maybe possible that your Laptop manufacturer has turned it off intentionally.

Also confirm in Windows8 that 'faststartup' is turned off and you are actually shutting down windows.

---

### Post by childintime on 2013-11-15
Asus K56C, bought 3 months ago.
BIOS:
Aptio Setup Utility
Version 215.1226
VBIOS Version 2137/I14K560.004
Version 205

When I bought it came just with DOS, I installed Win 8 myself.

Bios settings is very poor here. In Boot settings there are only few options and I checked all of them, nothing got UEfI in it. I checked all other tabs, nothing with UEfI either.

I think that my manufactured indeed disabled this option intentionally, because I read in some forums, how many options in Asus BIOS are just not there, like Secure boot.

---

### Post by fantab on 2013-11-15
So you don't have 'Secure boot' too? If you have it then disable it. Forget UEFI and GPT.

Go through my earlier post #14 read through it again. Using Gparted from Live Ubuntu DVD/USB readjust the partition /dev/sda4 as I suggested.

Once you have done that, run 
```
sudo fdisk -l
sudo parted -l
```
and post the output here, so that we can confirm that there are no errors.

---

### Post by childintime on 2013-11-15
No Secure boot as well in my BIOS.

Anyways, I tried to adjust that number before, but have no idea how to couldn't find such options in Gparted..

---

### Post by fantab on 2013-11-15
Ok...

Delete partitions from /dev/sda4 to /dev/sda8. Apply changes. Create a new Extended Partiton, when creating a new Extended Partition make sure it starts at the number I gave you the earlier post.
> the first number to the nearest possible number divisible by 8, which in your case should be **1155401720**.

Or whatever closest number, but it should be divisible by 8. After that apply changes. Check with 'fdisk -l' that it shows correct number. Once it is confirmed, make the other Logical Parition as required, you can use my suggestion below:
/dev/sda5 Logical 4-8GB SWAP
/dev/sda6 Logical 25GB Ext4 
/dev/sda7 Logical All the remaing GB EXT4.

Check with 'fdisk -l' It should not show any errors. All 'begin' numbers must be divisible by 8. Shutdown computer. 
Reboot with Ubuntu (go through the link in post #14) and make sure you boot in Legacy mode only, when booting you shoud see ubuntu color screen and not Black screen with options.
'Try Ubuntu without installing', from desktop INSTALL Ubuntu, use 'Something Else' option and Install ubuntu to /dev/sda6 [25GB partition]- mountpoint=/, Useas=Ext4, check Format. Make sure GRUB is installing to /dev/**sda**.

Good Luck.

---

### Post by childintime on 2013-11-15
Okay, I deleted all partitions, recreated, made fdisk -l and saw no problems like last time :) Tried to install ubuntu for fun, and got same error as first time: [COLOR=#000000]The 'grub-efi-amd64-signed' package failed to install into /target/

[/COLOR]I read your link, but I still don't understand how to not boot into EFI mode. I have no choices in BIOS, and when I load from live usb I get into black screen with 3 options which apparently means I am booting in EFI mode, but I don't know how to change that. Also they say to turn off secure boot, but again I don't have this option.

Maybe I should just try 13.10 version, or some other?

---

### Post by oldfred on 2013-11-15
When you boot Ubuntu from installer of Boot-Repair's live DVD/flash drive you should see in UEFI menu two choices. One will include UEFI and the other will not but may not be clear on what it says.

This shows both BIOS boot & UEFI boot screens, so you know which way you have booted and then can change to different entry in UEFI. Once you start booting in one mode you cannot switch.
       Shows install with screen shots.
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

When you boot with BIOS you get accessibility screen with tiny icons at bottom and purple. Any key then gives menu and f6 boot options.
When you boot with UEFI you get grub menu and have to manually add boot options.
Since you have MBR partitioning now, you only want BIOS boot.

---

### Post by childintime on 2013-11-15
oldfred, I am not booting from Boot-repair's live usb. I have only one usb and it's currently with ubuntu. What do you advice me to do exactly? I read your link many times, but many steps I can't even follow because my BIOS has very limited options.

---

### Post by oldfred on 2013-11-15
Even a limited UEFI/BIOS should show both UEFI & BIOS boot options from standard Ubuntu live installer.
You can always add Boot-Repair to Ubuntu live flash drive. If persistence is on, I think you can save, but may have to reinstall on reboot. 

If not sure you can use camera, take photo, shrink to small size as that is all that is allowed and in advanced editor use paperclip icon to attach.

Some other screens that users attached.

---

### Post by childintime on 2013-11-15
My BIOS is exactly like the on in the last pic. The only option mentioning EFI/UEFI is "launch efi shell from filesystem device" as you can see in the pic. Am I supposed to use it for installation?

---

### Post by oldfred on 2013-11-15
The efi shell is a command line type way to modify UEFI settings.
You still should have a separate boot order configuration.

Info on shell if interested, but not related to your boot issues.
 # from live CD and use efibootmgr
sudo efibootmgr -v
The "-v" option displays all the entries so you can confirm you're deleting the right one, and then you use the combination of "-b ####" (to specify the entry) and "-B" (to delete it). Examples #5 is delete:
[http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD](http://linux.dell.com/cgi-bin/gitweb/gitweb.cgi?p=efibootmgr.git;a=blob_plain;f=README;hb=HEAD)
[http://software.intel.com/en-us/articles/efi-shells-and-scripting/](http://software.intel.com/en-us/articles/efi-shells-and-scripting/)
Launch EFI Shell from File System Device
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#UEFI_Shell)

---

### Post by childintime on 2013-11-15
Thanks, but I don't understand what you are trying to say. I want to install ubuntu, i never used linux before, what exactly do i need to do? As I said my BIOS boot tab has absolutely no options for UEFI/EFI. You give me a lot of info, but I don't get what i need to do in next step!

---

### Post by oldfred on 2013-11-15
Some more Aptio screens, do have these?

---

### Post by childintime on 2013-11-15
Mine looks exactly like 2nd pic, but without "UEFI boot".

---

### Post by childintime on 2013-11-15
Okay so I read some guy in ask ubuntu told that that error comes due to signatures in ubuntu (whatever that means) and that 13.10 does not have this problem. So I indeed installed 13.10 without problems, then no Grub appeared so I ran boot-repair and I got grub and I can access my freshly installed ubuntu (hooorayy!), but there is no Windows 8 option in Grub to select. :-&

---

### Post by QIII on 2013-11-15
Don't want to alarm you, but we need to see if you inadvertently overwrote Windows.  Hopefully not, so don't get wrapped around the axle.  Boot from install media and follow the instructions [here]("https://help.ubuntu.com/community/Boot-Info") to get some important information from your system so we can take a look.  Post the url back here so folks can look at it.

Run your machine in a live session only until someone can have a look.

---

### Post by fantab on 2013-11-15
> **sladeinflame7 said:**
> Okay so I read some guy in ask ubuntu told that that error comes due to signatures in ubuntu (whatever that means) and that 13.10 does not have this problem. So I indeed installed 13.10 without problems, then no Grub appeared so I ran boot-repair and I got grub and I can access my freshly installed ubuntu (hooorayy!), but there is no Windows 8 option in Grub to select. :-&

Congratulations on installing Ubuntu 13.10.
Let us see why Windows8 is NOT showing up in GRUB's Menu. Post the LINK to 'BootInfo-Summary' which Boot-repair creates.

---

### Post by childintime on 2013-11-16
After I booted ubuntu, I ran some mandatory updates, then done "sudo update-grub", rebooted, and then I can see Windows in the grub, but now I can see 2 entries of windows :D

```
Ubuntu
Windows 8 (loader) on dev/sda1
Windows 8 (loader) on dev/sda2
```

Actually I don't mind it as long as everything works and it does. Thanks everyone, especially fantab, for your help! ;)

---

### Post by fantab on 2013-11-16
That is because you have Two paritions where Windows boot files are stored. And AFAIK you can boot from both, however one will boot faster that the other. You can find out booting from which entry is faster and stick to it.

*** Upgrades to Windows 8 are known to cause issues with Ubuntu boot. If in future you faced with such a situation, just run Boot-Repair.

I am glad you resolved your issues.
Good Luck.

---

