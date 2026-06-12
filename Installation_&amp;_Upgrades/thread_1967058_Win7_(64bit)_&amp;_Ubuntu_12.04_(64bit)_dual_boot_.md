---
title: "Win7 (64bit) &amp; Ubuntu 12.04 (64bit) dual boot issue"
date: 2012-04-27
forum: Installation &amp; Upgrades
---

### Post by JB1234 on 2012-04-27
I've had Windows 7 (64bit) installed and running fine for a couple of weeks on my new system, but since installing Ubuntu 12.04 I'm completely unable to boot Win7.

At first I just though Win7 wasn't showing in grub so I tried update-grub, Win7 still wasn't detected.

After some digging on Google I decided to try boot-repair and used the 'recommended repair' option and then things got a little weird, now when the system boots up it goes straight into 'Windows Error Repair' with the following options and results;

'Launch Startup Repair' : selecting this option loops back to 'Windows Error Repair'.

'Start Windows Normally' : selecting this option takes me to the grub menu and I can boot into Ubuntu 12.04 as normal (Win7 option is still AWOL).

I tried boot-repair again and got the same result.

So I decided to try and repair Win7 using the original DVD;

The 'automatic repair' option ran through and eventually told me that it could not be repaired automatically.

So I selected the 'command prompt' option and tried;

chkdsk C: /r

this completed with no errors.

So I tried; BootRec.exe /FixBoot

which apparently completed successfully. 

So I tried; BootRec.exe /ScanOs

which reported '0 windows installations found'.

So I decided to reinstall Win7 (with the intention of using boot-repair to sort out grub afterwards), however when it came to selecting an install partition I got the following displayed underneath the partition selection box..

"Windows cannot be installed to this disk. The selected disk is of the GPT partition style"

So I can't even reinstall Win7 now :(

I've never had an issue like this before and I've been dual booting Ubuntu / Win7 for years (though not on this system which I built to replace my 4 year old slowly dying desktop).

I'm hoping someone on here can shed some light on the situation as I'm thoroughly stumped right now!

---

### Post by darkod on 2012-04-27
And is your partition table gpt or msdos? What does
sudo parted /dev/sda print

say?

Use boot-repair again but only to create the bootinfoscript results and post the link it provides. That will show more details.

---

### Post by JB1234 on 2012-04-27
> **darkod said:**
> And is your partition table gpt or msdos? What does
sudo parted /dev/sda print

say?

Model: ATA Corsair Force 3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot
 2      106MB   240MB   134MB                Microsoft reserved partition  msftres
 3      240MB   77.1GB  76.9GB  ntfs         Basic data partition
 4      77.1GB  120GB   42.9GB  ext4

> **darkod said:**
> Use boot-repair again but only to create the bootinfoscript results and post the link it provides. That will show more details.

[http://paste.ubuntu.com/951107/](http://paste.ubuntu.com/951107/)

---

### Post by JB1234 on 2012-04-27
> **poonjabi said:**
> install windows in virtualbox and erase hdd and put only ubuntu

problem solved :)

If I could run games and a couple of programs I need for work in a VM I would ;-)

---

### Post by garvinrick4 on 2012-04-27
[http://technet.microsoft.com/en-us/library/cc725797.aspx](http://technet.microsoft.com/en-us/library/cc725797.aspx)

---

### Post by darkod on 2012-04-27
Uhhh, you are using gpt and EFI boot. I think there are still issues making a good dual boot with this combination.

One thing I can see missing for sure, is a small 1MB partition with the bios_grub flag set on it. With gpt disks, grub2 doesn't fit fully on the MBR so it needs a small 1MB partition WITHOUT any filesystem. You can create it with parted for example, and DO NOT create filesystem on it. You just need to set the bios_grub flag.

The problem with the dual boot was that grub2 was deleting the windows EFI files. The EFI system partition should hold both, but if you don't backup the windows boot files before the ubuntu install, it seems they were getting deleted. Not sure if this is fixed in 12.04.

I don't have all the answers for you, maybe oldfred will. He knows much more about gpt + EFI than me.

---

### Post by JB1234 on 2012-04-27
> **garvinrick4 said:**
> [http://technet.microsoft.com/en-us/library/cc725797.aspx](http://technet.microsoft.com/en-us/library/cc725797.aspx)

Hmmm, that doesn't seem relevant unless I'm missing something. That article describes how to convert a GPT disk into an MBR disk from within windows if the drive is empty, firstly I can't get into windows and secondly it's installed on the disk in question.

From what I can gather from a few other sites on a modern system with a UEFI motherboard Windows 64bit actually *requires* a GPT disk.. now I'm even more confused!

---

### Post by JB1234 on 2012-04-27
> **darkod said:**
> Uhhh, you are using gpt and EFI boot. I think there are still issues making a good dual boot with this combination.

One thing I can see missing for sure, is a small 1MB partition with the bios_grub flag set on it. With gpt disks, grub2 doesn't fit fully on the MBR so it needs a small 1MB partition WITHOUT any filesystem. You can create it with parted for example, and DO NOT create filesystem on it. You just need to set the bios_grub flag.

The problem with the dual boot was that grub2 was deleting the windows EFI files. The EFI system partition should hold both, but if you don't backup the windows boot files before the ubuntu install, it seems they were getting deleted. Not sure if this is fixed in 12.04.

I don't have all the answers for you, maybe oldfred will. He knows much more about gpt + EFI than me.

Ah ok that makes more sense, I'll create that partition now and try a few things, thanks.

---

### Post by darkod on 2012-04-27
> **JB1234 said:**
> Hmmm, that doesn't seem relevant unless I'm missing something. That article describes how to convert a GPT disk into an MBR disk from within windows if the drive is empty, firstly I can't get into windows and secondly it's installed on the disk in question.

From what I can gather from a few other sites on a modern system with a UEFI motherboard Windows 64bit actually *requires* a GPT disk.. now I'm even more confused!

Yes, for EFI boot and windows you NEED gpt table. It will not work with msdos.

On another note, ubuntu with gpt needs the small bios_grub partition with or without EFI since grub2 doesn't fit on the MBR. I am not 100% sure about the EFI part but people create it just in case.

You could delete your linux partition from live mode and create first the small bios_grub partition with parted and then start the install.

---

### Post by oldfred on 2012-04-27
Most UEFI systems will boot in BIOS/MBR mode, but gpt is the newer (slightly) better partitioning system.

I do not know how to repair a Windows UEFI system if Windows will not auto repair it. I have some links that may help. 

Grub2 had several bugs with dual booting Windows. And one was it overwrote the efi FAT32 and made it FAT16. It looks like yours still is FAT32, but does not now have the Windows efi boot loader.

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

Someone posted this as the Windows efi files, these may be elsewhere on Windows partition or Windows CD:

/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

You have the grub/Ubuntu
/boot/efi/EFI/BOOT/bootx64.efi

I do not know if sda2 has more Windows boot files but believe it should 

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.
Post #76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
efi\Microsoft\Boot\bootmgfw.efi

Someone also posted this on how to use the UEFI to add a boot entry for Ubuntu. You may be able to do the same for Windows, but I do not know which folder to look into.

It looks like most of the repairs you have done assume MBR as they have installed boot loaders to the protective MBR. That will not cause a problem on its own. You do not need a bios_grub partition with efi, but do have to have it with Ubuntu & BIOS with gpt partitioning.

---

### Post by JB1234 on 2012-04-27
> **darkod said:**
> Yes, for EFI boot and windows you NEED gpt table. It will not work with msdos.

On another note, ubuntu with gpt needs the small bios_grub partition with or without EFI since grub2 doesn't fit on the MBR. I am not 100% sure about the EFI part but people create it just in case.

You could delete your linux partition from live mode and create first the small bios_grub partition with parted and then start the install.

Ok thanks for clarifying that for me :)

A couple of questions though..

If I do that will it fix Windows / allow the repair process to detect it? 

You mentioned that the Windows EFI files had likely been deleted so I would I be better off just wiping the whole drive and starting again (I can restore the windows install from an image I made) but this time creating the bios_grub partition from the live cd before I install Ubuntu?

---

### Post by JB1234 on 2012-04-27
> **oldfred said:**
> Most UEFI systems will boot in BIOS/MBR mode, but gpt is the newer (slightly) better partitioning system.

I do not know how to repair a Windows UEFI system if Windows will not auto repair it. I have some links that may help. 

Grub2 had several bugs with dual booting Windows. And one was it overwrote the efi FAT32 and made it FAT16. It looks like yours still is FAT32, but does not now have the Windows efi boot loader.

dual boot efi windows and efi linux 
[http://ubuntuforums.org/showthread.php?t=1890048](http://ubuntuforums.org/showthread.php?t=1890048)

Someone posted this as the Windows efi files, these may be elsewhere on Windows partition or Windows CD:

/boot/efi/EFI/Microsoft/Boot/bootmgfw.efi
/boot/efi/EFI/Microsoft/Boot/bootmgr.efi
/boot/efi/EFI/Microsoft/Boot/memtest.efi

You have the grub/Ubuntu
/boot/efi/EFI/BOOT/bootx64.efi

I do not know if sda2 has more Windows boot files but believe it should 

Windows Recommended UEFI-Based Disk-Partition Configurations
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)
Change the booting style of Windows Vista or 7 x86_64 versions from BIOS-MBR mode to UEFI-GPT mode without formatting or reinstalling
[http://www.insanelymac.com/forum/lofiversion/index.php/t186440](http://www.insanelymac.com/forum/lofiversion/index.php/t186440)
Windows installs the efi bootloader to (ESP)/EFI/Microsoft/Boot/ which is identical to (WINDOWS_SYSTEM_PART)/boot/microsoft/ incase of BIOS systems.
The dir mainly consists of bootmgfw.efi, bootmgr.efi, memtest.efi and 'bcd'.
Post #76
[http://ubuntuforums.org/showthread.php?t=1719851&page=8](http://ubuntuforums.org/showthread.php?t=1719851&page=8)
efi\Microsoft\Boot\bootmgfw.efi

Someone also posted this on how to use the UEFI to add a boot entry for Ubuntu. You may be able to do the same for Windows, but I do not know which folder to look into.

It looks like most of the repairs you have done assume MBR as they have installed boot loaders to the protective MBR. That will not cause a problem on its own. You do not need a bios_grub partition with efi, but do have to have it with Ubuntu & BIOS with gpt partitioning.

Thanks for all the info! I'll go through it now... it could take some time though :)

EDIT: Just realised it's quarter to one in the morning so think I'll leave it for tonight and go over it all in the morning! Thanks again guys :)

---

### Post by oldfred on 2012-04-27
Found this link.

[http://alasdaircs.wordpress.com/2011/08/23/sandy-bridge-uefi-windows-7-x64-sp1-cmos-settings-wont-boot/](http://alasdaircs.wordpress.com/2011/08/23/sandy-bridge-uefi-windows-7-x64-sp1-cmos-settings-wont-boot/)

Basically it says you can boot the Windows DVD in BIOS mode and then it runs BIOS repairs or you can boot the DVD in UEFI from UEFI directly and it will run UEFI repairs.

---

### Post by JB1234 on 2012-04-29
> **oldfred said:**
> Found this link.

[http://alasdaircs.wordpress.com/2011/08/23/sandy-bridge-uefi-windows-7-x64-sp1-cmos-settings-wont-boot/](http://alasdaircs.wordpress.com/2011/08/23/sandy-bridge-uefi-windows-7-x64-sp1-cmos-settings-wont-boot/)

Basically it says you can boot the Windows DVD in BIOS mode and then it runs BIOS repairs or you can boot the DVD in UEFI from UEFI directly and it will run UEFI repairs.

I noticed that too through trial and error, it still didn't work though :(

I deleted all the windows related partitions in the end which made the system boot straight into Ubuntu as normal, but for some reason 'Windows Boot Manager' was still a boot option in the BIOS.

I spent a large part of yesterday trying various installation methods as discussed in your links etc, none of which gave me a working dual-boot. Here's the basic gist of what I tried and the result;

1) Deleted all drive partitions and restored Win7 image; 
unable to boot into windows, black screen with blinking cursor.

2) Deleted all drive partitions and installed Win7 (64 bit) from cd;
Black screen with blinking cursor mid way through install, install would not complete.

3) Deleted all drive partitions and installed Ubuntu 12.04 (64 bit) from cd (taking care to create the recommended partitions first);
Worked perfectly in every regard.

I'd seen comments suggesting that despite the usual method of installing Windows then Ubuntu the opposite may work better with UEFI systems so...

4) Attempted to install Win7 (64 bit) alongside Ubuntu;
Black screen with blinking cursor mid way through install, install would not complete. I could also no longer boot into Ubuntu, even after deleting windows partitions, reinstalling grub and using default repair + purge and reinstall from boot-repair live cd.

5) Deleted all drive partitions and installed Ubuntu 12.04 (64 bit) from cd;
Worked perfectly in every regard.

So at present I have a perfectly good Ubuntu 12.04 installation (so at least I can work!), but no way of installing Win7 on the system at all. 

I used the same disc to reinstall Win7 on my old system as well which is working ok so I can use the windows applications I need on that for now (not ideal but ok as a temporary fix), it's no good for gaming though due to hardware issues :(

At this point I really wish I didn't need a dual boot system but two work related apps just don't work well in vms... and I'm kind of addicted to Eve Online & Unreal Tournament :redface:

Strangely 'Windows Boot Manager' is still a boot option in the BIOS, it's as though some trace of the windows boot loader is actually being held by the BIOS itself and preventing successful re-installation... very odd indeed.

I'm going to do some more digging and hopefully come up with a new plan of attack, I'll keep this thread going and update if / when I make progress or find any relevant information.

Thanks again to those who have helped so far, I'll keep an eye on the thread in case anyone posts with any helpful information or comes with any more ideas on where to go from here.

---

### Post by oldfred on 2012-04-29
Do not know if this works for UEFI systems or not but you can run the Boot-info report to see details of your system.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

---

### Post by JB1234 on 2012-04-29
> **oldfred said:**
> Do not know if this works for UEFI systems or not but you can run the Boot-info report to see details of your system.

Boot Repair:
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)
You can repair many boot issues with this or Create BootInfo report & post the link to a run of boot info script so we can see your exact configuration.

I've been using this, if you look back over the thread you'll see the results from my initial attempt at dual boot, posted at the request of darkod. 

In my experiences so far it seems very hit or miss with regards to UEFI systems, running it now shows no trace of the 'Windows Boot Loader' that my BIOS claims is still available to boot (just the Ubuntu partitions you'd expect to see), selecting that option from the boot menu actually loads Ubuntu!

---

### Post by Cyborganism on 2012-04-29
Hi guys,

See further down at TL;DR for how I installed my dual boot UEFI/GPT pc.

I've been a long time lurker, but after purchasing a new computer just last week, I realized technology had changed and now modern motherboards use this thing called EFI or UEFI?

Yeah... And what's that? Hard drives need a new partitioning format? GPT? The hell? I'm a software engineer and have been putting together PCs with dual boot Linux and Windows for a long time, but this new stuff made me feel like a freakin' noob. Even worse, nobody seems to know how the hell this new stuff really works. All the usual grub2 tricks don't work either because of this new partitioning scheme.

Well I stumbled across a tiny little thread last night while pulling my hair out and here's what I learned. If your motherboard uses UEFI, you HAVE to install Windows and Linux with GPT partitioning. From what I understood (and correct me if I'm wrong, please!), this scheme creates a large GPT type partition taking up the entire disk, kind of like an extended partition. But, in that GPT partition, you have 2 small partition at the start of the disk and then the other regular partitions. The first partition is something like a fat32 100mb partition used to a GPT table that holds parition GUIDs with their addresses (GPT means GUID Partition Table). It's basically the new MBR! The second one is a raw unformatted partition of about 128mb to hold the EFI boot loader used by the BIOS to boot your OS. (I guess that's where the Windows boot loader is installed? As well as the new grub2-efi?) It is **_VERY IMPORTANT_** that if you install Windows 7 with UEFI/GPT, you **_HAVE _**to install Ubuntu by booting in the x64 install CD in UEFI mode. (See your BIOS these boot options) This will launch the proper UEFI/GPT installation procedure for Ubuntu. Otherwise your Windows won't boot anymore. Even if it's ona different hard drive. ALL drives must use that partitioning scheme.

**TL;DL**

Anyway, for my setup I used 2 different SATA drives. One containing the Windows 7 x64 installation and the second for my x64 Ubuntu installation. My motherboard is a Gigabyte H61M-DS2 which uses UEFI. The BIOS has a boot menu that shows up when I press F12 at boot time and lets me select from what device/GPT boot manager to boot from.

First, I unplugged my Ubuntu designated hard drive and kept only the Windows 7 one plugged in and installed Windows by booting on the install DVD in UEFI mode through the boot menu. Windows created the whole GPT partitioning schema and the OS booted normally. This added a Windows Boot Manager option in my BIOS.

Then I unplugged my Windows 7 hard drive and plugged in my Ubuntu hard drive. Again, when I booted I chose to boot the Ubuntu 64bit desktop install cd in UEFI mode. (The CD also boots in the old fashion regular boot cd mode but you must avoid, otherwise it will install Ubuntu with the old MBR partitioning scheme which will render the Windows installation unbootable on the other hard drives.) There was a black and white text-only grub boot menu. I editted the "Start Ubuntu" or "Install Ubuntu" entry and added "NOMODESET" to the entry and pressed F10 to boot with those options. (I was getting a black screen with no video output otherwise) Finally, I just installed Ubuntu as if there was no other OS and used the Guided-use entire disk option for at the partitioning screen. This automatically created the GPT style partitioning scheme and installed grub2-efi properly. It also added the Ubuntu boot option in my BIOS.

Finally, I plugged in both hard drives and using the BIOS boot menu using F12 I was able to choose either the Windows Boot Manager or Ubuntu to boot in either OSes without any problem.

That's my solution for my particular setup.

---

### Post by darkod on 2012-04-29
One idea, if it fits with your plans, is to use the standard BIOS boot and not EFI. Some boards will have the option to disable EFI boot.

Personally I don't see much benefit from it, and at the moment there are many issues dual booting with it. Since many manufacturers prefer and lobby for MS it's a question how long will it take until EFI boot can dual boot fine.

But I might be wrong about EFI not having any benefits, I don't know too much about it.

---

### Post by JB1234 on 2012-04-29
Cyborganism, your reaction sounds very similar to mine and likewise I've been building systems for many years, I won't say how many though as it will make me sound like a dinosaur ;)

If I'd tried this initially I suspect it would have worked as you describe, I'd have happily put WIn7 on my data drive rather than the ssd with Ubuntu as I don't use it anywhere near as often, the trouble now is that I simply cannot get Win7 to install at all so until I figure that one out I've hit a dead end.

It sounds like a good temporary solution until grub works well with UEFI though so hopefully I'll get a chance to try it soon, thanks for posting.

darkod, I tried that today on another drive (removing the one I was using previously) and it doesn't seem to be an option, neither OS will install properly without UEFI, I just get a black screen and blinking cursor (mid way through WIn7 install and right at the beginning of Ubuntu install). 

It's hard to say whether this was initially the case or a result of the BIOS 'hanging onto' the 'Windows Boot Manager' option which for some reason I can't seem to get rid of despite deleting every single partition on the disk.

Hopefully I'll get some time next weekend to work on this but for now I need my working install of Ubuntu to get some work done.

---

### Post by JB1234 on 2012-06-14
Ok so over one month on I've essentially given up on this, a traditional Windows & Ubuntu dual-boot is just not possible using a GPT / UEFI system using grub, the only way to get a working dual boot (at present) is to install to separate disks (one in the system at a time) and then fit both drives and select which one to boot each time from the BIOS.

After giving it some thought I decided to just ditch the whole dual boot idea and use a virtualized Windows within Ubuntu instead. With the VM on my SSD it actually runs better than a straight install on my old system and amazingly all the Windows apps I need run fine, unreal tournament works flawlessly with WINE and I've even managed to get Eve Online working! It was a blessing in disguise in the end as the new setup is much more flexible and convenient :)

I'll keep this thread open for now though as I'll be periodically trying a dual boot setup again on my kids new system ;)

---

### Post by raj727 on 2012-06-23
After reading this thread, I'm having second thoughts about a dual boot system.

I currently have two PC's I'm thinking of dual booting with Ubuntu 12.04.  Both currently only have Windows 7 (64 bit).

PC#1 has the following:

Motherboard: ASUS P8Z77-i (ivy bridge chipset) with UEFI
SSD: 120GB with 60GB allocated to Windows 7 and the rest un-allocated
HD:  None

PC#2 has the following:

Motherboard: Z68MA-ED55(B3) (sandy bridge chipset)
SSD: 40GB with all of it allocated to Windows 7
HD:  None

I attempted to install Ubuntu 12.04 on PC#1 but my install did not recognize Windows 7 on the PC and so I terminated the install.  The install process did recognize the NTFS file system but not the Windows 7 operating system.

I am purchasing a 120GB SSD for use in PC#2.  My plan was to put Ubuntu on that SSD and then have operating systems on two separate SSD's and boot using the BIOS options.

I'm reluctant to go through the problems encountered in the thread.  Does anyone have any options for PC#1?  

Is there a better option for PC#2?

---

### Post by darkod on 2012-06-23
> **raj727 said:**
> After reading this thread, I'm having second thoughts about a dual boot system.

I currently have two PC's I'm thinking of dual booting with Ubuntu 12.04.  Both currently only have Windows 7 (64 bit).

PC#1 has the following:

Motherboard: ASUS P8Z77-i (ivy bridge chipset) with UEFI
SSD: 120GB with 60GB allocated to Windows 7 and the rest un-allocated
HD:  None

PC#2 has the following:

Motherboard: Z68MA-ED55(B3) (sandy bridge chipset)
SSD: 40GB with all of it allocated to Windows 7
HD:  None

I attempted to install Ubuntu 12.04 on PC#1 but my install did not recognize Windows 7 on the PC and so I terminated the install.  The install process did recognize the NTFS file system but not the Windows 7 operating system.

I am purchasing a 120GB SSD for use in PC#2.  My plan was to put Ubuntu on that SSD and then have operating systems on two separate SSD's and boot using the BIOS options.

I'm reluctant to go through the problems encountered in the thread.  Does anyone have any options for PC#1?  

Is there a better option for PC#2?

I wouldn't say you need to give up. There are success stories for UEFI dual boot on the same disk.

Possibly you might need to do some additional manual steps, but I wouldn't say it's impossible.

I don't have UEFI myself, but from reading threads here and people's problems, I would say the most important points are:
1. Install your win7 in UEFI mode (you might already have this installed). That would mean the disk is with GPT table since win7 can work with UEFI only on GPT.
2. Before starting the ubuntu install, boot into live mode and create the small 1MB partition with NO filesystem on it, and with the bios_grub flag. Ubuntu needs this on GPT disks. I am still not sure if it needs it when using UEFI or not, but doesn't hurt having a small 1MB partition anyway.
3. Just in case, copy the windows boot files that are on the EFI System partition, in case grub2 deletes them.
4. Boot the ubuntu cd in UEFI mode. as specified in one post on this thread. That will make sure ubuntu is installed in UEFI mode.
5. After the install, check the EFI System partition. If the windows boot files aren't there, copy them back.
6. Go into BIOS or UEFI OS manager or what ever it's called, and make an entry for ubuntu if it doesn't do that automatically.  Many posts mention you need to do this in BIOS, so it's not related to ubuntu.

That's it. See if your work paid off.

If you have the option to do this in virtual box first, you can try it there as a test.

---

### Post by raj727 on 2012-06-23
Darkod.  Thanks for your reply.

I don't have an advanced understanding of Ubuntu although I've been using it for a while.

I noticed in the BIOS in PC#1, there is three icons in the boot sequence.  DVD, UEFI and HHD.  I'm not sure what this means?  Did you mean, in point 1 of your reply. that I should have installed Windows 7 with UEFI first in the boot sequence?  If I am able to boot with the UEFI icon as first in the boot sequence, does that mean I've installed in UEFI mode?

In point 2, would I create the 1MB partition at the start of the un-allocated section of the SSD before using the rest of the SSD for Ubuntu?

In point 3, I assume I can copy the files using the liveCD and save them on a memory card?

In point 4, I'm not sure what UEFI mode is?

---

### Post by darkod on 2012-06-23
Yes, if you can boot with the UEFI icon probably win7 is in UEFI mode. You can check this very easily. Boot with the ubuntu cd in live mode, and in terminal run:
```
sudo fdisk -l
```

If the first partition on the SSD is of type EFI System partition, win7 is installed in UEFI mode.

Yes, you would create the 1MB partition at the start of the unallocated space. Just make sure there is no filesystem. For that, it's best to create it with parted. I am not sure graphical tools like Gparted can create partitions with no filesystem. If you need help with this you can ask beofre doing it. I was also using Gparted a lot because it's graphical but later realized how much more possibilities the simple command line interface has, with the parted command. In some cases it's really helpful and does the job faster.

Yes, you can copy the files using liveCD to a memory card, usb stick, what ever...

As for UEFI mode, people have reported that UEFI boards have two different devices in the BIOS boot devices. For example, you would have cd-rom(bios/normal) and cd-rom(uefi). You need to move cd-rom(uefi) to be first, so that when it boots the ubuntu cd it does that in UEFI mode. The cd can be booted in both, the standard bios mode, and the new uefi mode. It seems how you boot it, depends how it will install.

The same applies for win7. People have reported that if you have installed win7 in UEFI mode, and you need to repair something for example. If you boot the win7 dvd in the normal bios mode, it will not be able to repair it because it's not booted in uefi.

---

### Post by raj727 on 2012-07-21
darkod

Sorry I've been away and did not have a chance to try to set up a dual-boot installation until now.

I was trying to copy the windows boot files on a memory stick as you suggested but can't seem to locate them.  Do you know where they would be?

The EFI partition doesn't seem to show up as a folder in Nautilis (I think that's the name of the program that displays the contents of various drives).

---

### Post by darkod on 2012-07-21
> **raj727 said:**
> darkod

Sorry I've been away and did not have a chance to try to set up a dual-boot installation until now.

I was trying to copy the windows boot files on a memory stick as you suggested but can't seem to locate them.  Do you know where they would be?

The EFI partition doesn't seem to show up as a folder in Nautilis (I think that's the name of the program that displays the contents of various drives).

I have no idea. I would expect part of the files to be on the EFI partition, and some of them (one file for example) to be on the win7 partition.

Are you sure you are using UEFI? We are not talking whether the board has the option, but whether win7 was installed as UEFI.

---

### Post by raj727 on 2012-07-21
I'm fairly certain.  In the boot up BIOS, the UEFI (SSD) icon shows up first.  Then the SSD icon and then the DVD icon.

The liveCD was booted using the UEFI DVD icon first. 

Is there someway to confirm I installed Windows 7 in UEFI mode?

Also, I started the Ubuntu install, but stopped when it did not detect any other operating systems.

---

### Post by darkod on 2012-07-21
Boot the ubuntu cd in live mode, and in terminal check the disks layout with:
sudo parted -l (small L)

Look carefully, it will display the partition table type for each disk. For the win7 disk it should be gpt because win7 can't work on msdos table in UEFI mode. So, if you have msdos table you know for sure win7 is not in UEFI.

If it looks like UEFI but the boot files are not on the EFI partition, I really don't know what to say.

When looking at the boot order, don't forget that even if SSD UEFI is first, then SSD normal, it would still boot in normal BIOS mode. First it checks for UEFI, doesn't find it, continues down the list and next is the same SSD only in normal BIOS boot mode. This is just an assumption.

---

### Post by raj727 on 2012-07-21
This is what I got:

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot
 2      106MB   240MB   134MB                Microsoft reserved partition  msftres
 3      240MB   62.9GB  62.7GB  ntfs         Basic data partition
 4      62.9GB  62.9GB  1049kB                                             bios_grub


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$

---

### Post by oldfred on 2012-07-22
This may be the problem:
> 
Error: Can't have a partition outside the disk!                           You have an efi partition and the Microsoft reserved partition so you have UEFI/efi boot with Windows. But partition errors can cause many problems.

repair gpt:
[http://www.rodsbooks.com/gdisk/repairing.html](http://www.rodsbooks.com/gdisk/repairing.html)


Edit - removed fixparts link as it looks like it is only for MBR or repairing MBR with gpt backups still in partition.[]("http://www.rodsbooks.com/fixparts/")

---

### Post by raj727 on 2012-07-22
I read over the link but I'm not sure what command I would use to fix the problem?

---

### Post by oldfred on 2012-07-22
I have never had to repair, but gdisk is pretty smart. You may just need to load gdisk, review partitions to see what it says and write (rewrite current table).

What does this say? Change sda to your drive if not sda.

gdisk /dev/sda

If it does not auto repair then you might need r, i, v and if ok then w to write.

---

### Post by raj727 on 2012-07-22
I tried the command in terminal but it said I did not have the program.  I went to install it and got this response:

ubuntu@ubuntu:~$ sudo gdisk
sudo: gdisk: command not found
ubuntu@ubuntu:~$ gdisk
The program 'gdisk' is currently not installed.  You can install it by typing:
sudo apt-get install gdisk
You will have to enable the component called 'universe'
ubuntu@ubuntu:~$ sudo apt-get install gdisk
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package gdisk
ubuntu@ubuntu:~$ gdisk
The program 'gdisk' is currently not installed.  You can install it by typing:
sudo apt-get install gdisk
You will have to enable the component called 'universe'

---

### Post by oldfred on 2012-07-22
I use synaptic

sudo apt-get install synaptic

or:

Software Sources and Download from to set more local repository:
gksu software-properties-gtk &

And either way you have to check off to include universe.

---

### Post by raj727 on 2012-07-28
I installed gdisk using synaptic.  I then ran gdisk in terminial trying different names for the drive.  I got these messages:

ubuntu@ubuntu:~$ sudo gdisk
GPT fdisk (gdisk) version 0.8.1

Type device filename, or press <Enter> to exit: gdisk/dev/sda
Problem opening gdisk/dev/sda for reading! Error is 2.
The specified file does not exist!
ubuntu@ubuntu:~$ sudo gdisk
GPT fdisk (gdisk) version 0.8.1

Type device filename, or press <Enter> to exit: sda
Problem opening sda for reading! Error is 2.
The specified file does not exist!
ubuntu@ubuntu:~$ sudo gdisk
GPT fdisk (gdisk) version 0.8.1

Type device filename, or press <Enter> to exit: disk/dev/sda
Problem opening disk/dev/sda for reading! Error is 2.
The specified file does not exist!

---

### Post by oldfred on 2012-07-28
Try this:

sudo gdisk -l /dev/sda

and this:

sudo parted /dev/sda unit s print
or
sudo parted -l

---

### Post by raj727 on 2012-07-28
This is what I got:

ubuntu@ubuntu:~$ sudo gdisk -l /dev/sda
GPT fdisk (gdisk) version 0.8.1

Partition table scan:
  MBR: protective
  BSD: not present
  APM: not present
  GPT: present

Found valid GPT with protective MBR; using GPT.
Disk /dev/sda: 234441648 sectors, 111.8 GiB
Logical sector size: 512 bytes
Disk identifier (GUID): 96FAD121-2DC4-409F-88F9-70A81A31417B
Partition table holds up to 128 entries
First usable sector is 34, last usable sector is 234441614
Partitions will be aligned on 2048-sector boundaries
Total free space is 111559533 sectors (53.2 GiB)

Number  Start (sector)    End (sector)  Size       Code  Name
   1            2048          206847   100.0 MiB   EF00  EFI system partition
   2          206848          468991   128.0 MiB   0C01  Microsoft reserved part
   3          468992       122882047   58.4 GiB    0700  Basic data partition
   4       122882048       122884095   1024.0 KiB  EF02  
ubuntu@ubuntu:~$

---

### Post by oldfred on 2012-07-28
If you have Windows and gpt partitioning you have to have installed with UEFI. Also the efi parition as the first partition shows that it is UEFI.

You do not need the bios_grub partition shown as ef02 in gparted if in UEFI mode.

How Windows installs:
Older Windows info on gpt - 2008 updated 2011
[http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx](http://msdn.microsoft.com/en-us/windows/hardware/gg463525.aspx)
Microsoft suggested partitions including reserved partition for gpt & UEFI:
[http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx](http://technet.microsoft.com/en-us/library/dd744301%28WS.10%29.aspx)

Lots of technical info if interested:
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface)
[https://wiki.archlinux.org/index.php/UEFI](https://wiki.archlinux.org/index.php/UEFI)
[https://wiki.archlinux.org/index.php/GPT](https://wiki.archlinux.org/index.php/GPT)
[https://wiki.archlinux.org/index.php/Grub2](https://wiki.archlinux.org/index.php/Grub2)

Some examples from other threads:
UEFI dual boot trouble: Win7x64 - Ubuntu 12.04 LTS amd64
[http://ubuntuforums.org/showthread.php?t=2003442](http://ubuntuforums.org/showthread.php?t=2003442)
GUIDE: (U)EFI installation Also full install post *52 superfreak pg.6
[http://ubuntuforums.org/showthread.php?t=1958383](http://ubuntuforums.org/showthread.php?t=1958383)
UEFI screen shots with choice to boot
[http://ubuntuforums.org/showthread.php?p=12030957#post12030957](http://ubuntuforums.org/showthread.php?p=12030957#post12030957)
Asus UEFI instructions (except efi should be first partition, but must not have to be)
[http://ubuntuforums.org/showthread.php?p=11842855](http://ubuntuforums.org/showthread.php?p=11842855)

Do SSD need customization?
[http://ubuntuforums.org/showthread.php?t=1981478](http://ubuntuforums.org/showthread.php?t=1981478)
[https://wiki.archlinux.org/index.php/Solid_State_Drives](https://wiki.archlinux.org/index.php/Solid_State_Drives)

---

### Post by raj727 on 2012-07-28
I continued with the following commands and seemed to get the same error message I got originally.

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot
 2      106MB   240MB   134MB                Microsoft reserved partition  msftres
 3      240MB   62.9GB  62.7GB  ntfs         Basic data partition
 4      62.9GB  62.9GB  1049kB                                             bios_grub


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 


Do I still have the same problem?

---

### Post by oldfred on 2012-07-28
The sr0 is just the CD, but I do not see the issue that it is saying, but I am more familiar with that in MBR disks. And often related to the new 4K drives where they get mixed up with 512.

This gives a bit more detail.

sudo parted /dev/sda unit s print

Normally outside disk type error is some partitions end sector is beyond the last sector of the drive. Then the partition just needs an update to fix that.

Did gdisk report any errors?

---

### Post by raj727 on 2012-07-28
ubuntu@ubuntu:~$ sudo parted /dev/sda unit s print
Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sda: 234441648s
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start       End         Size        File system  Name                          Flags
 1      2048s       206847s     204800s     fat32        EFI system partition          boot
 2      206848s     468991s     262144s                  Microsoft reserved partition  msftres
 3      468992s     122882047s  122413056s  ntfs         Basic data partition
 4      122882048s  122884095s  2048s                                                  bios_grub

ubuntu@ubuntu:~$ sudo parted -l
Model: ATA OCZ-VERTEX3 (scsi)
Disk /dev/sda: 120GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt

Number  Start   End     Size    File system  Name                          Flags
 1      1049kB  106MB   105MB   fat32        EFI system partition          boot
 2      106MB   240MB   134MB                Microsoft reserved partition  msftres
 3      240MB   62.9GB  62.7GB  ntfs         Basic data partition
 4      62.9GB  62.9GB  1049kB                                             bios_grub


Warning: Unable to open /dev/sr0 read-write (Read-only file system).  /dev/sr0
has been opened read-only.
Error: Can't have a partition outside the disk!                           

ubuntu@ubuntu:~$ 


I tried to install ubuntu 12.04 but it still doesn't recognize Windows 7 on my machine.  The installation process asked if I wanted to wipe the drive and install 12/04.

---

### Post by oldfred on 2012-07-28
Use Windows to shrink the Windows partition, not the installer. Then reboot Windows so it can run chkdsk and recognize its new size.

With UEFI you should boot in UEFI mode not BIOS/legacy mode. Then it will install in UEFI mode.

Have you tried liveCD in test mode to make sure your system works ok? Then use gparted to see what it says about your drive and if any warning icons on left side click on them for explanation.

---

