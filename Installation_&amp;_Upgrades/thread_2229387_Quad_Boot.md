---
title: "Quad Boot"
date: 2014-06-12
forum: Installation &amp; Upgrades
---

### Post by kakashi_12 on 2014-06-12
Want to turn my Triple Boot into a Quad Boot. I will definitely start with a clean slate and re-install all OS's and format all partitions. What order should I install?....

Windows XP
Windows 7 Professional (64 bit)
Windows Server 2008
Linux, Ubuntu 12.04 (Lucid Lynx)


(Ya ya, I know. I should update to a newer version of Ubuntu. I like this one though.)
What do you think, what order? Thanks.

---

### Post by QIII on 2014-06-12
Hello!

I'd get the partitions in order first, and then maybe go to the [Windows 7 forums]("http://www.sevenforums.com/") to get advice on how to do the Windows stuff.

Then install Ubuntu (take care with your partitions) last.

---

### Post by oldfred on 2014-06-12
Install all Windows in primary partitions and use 4th primary as the extended for Ubuntu, swap and shared data NTFS partition. 
Why install XP? It may be dangerous to use on Internet.

 To get each MS to have its own boot loader make a second primary NTFS partition and set its boot flag on, then install the 2nd product in it. Multibooters, Pictures here worth 1000+ words - Vista but all Windows with BIOS/MBR
[http://www.multibooters.co.uk/multiboot.html](http://www.multibooters.co.uk/multiboot.html)
More tech info - BIOS boot process & some UEFI
[http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html](http://homepage.ntlworld.com./jonathan.deboynepollard/FGA/windows-nt-6-boot-process.html)

---

### Post by kakashi_12 on 2014-06-14
Need XP for certain application support. Applications that are hardware reliant and do not work in a virtual machine.
I do not plan on using XP on the internet. I plan on disabling all internet/network connections within the XP OS.

I only want one boot loader. But as of right now (on my triple boot) I have two boot loaders. Which is unfortunate. I have BCD (Boot Configuration Data) from Windows 7 and I have GRUB2. Wish I could use one or the other only, preferably a Linux loader. I've even tried using LILO or some other Linux loader. Unsuccessful.

What do you mean
"4th primary as the extended for Ubuntu, swap and shared data NTFS partition."  ???
Primary or Extended partition? Which one, only can be one or the other. And if I have a Swap and Data NTFS partition, do they need to be Extended Partitions?
There is only 4 Primary partitions available, right? Or is that 4 Primary per HDD?

---

### Post by oldfred on 2014-06-14
It is 4 primary partitions per hard drive. The extended partition is a primary partition that is just a container for as many logical partitions as you want to add or have space available.

Windows only boots from one primary NTFS partition with the boot flag from the drive set as bootable in BIOS. And every additional install of Windows moves its boot files into that one primary and has no boot files of its own, so grub will not see those installs. 
See link to mulltiboot site above for details.

If the other installs of Window are in primary partitions you can move boot flag and repair them to include boot files. Then grub can directly boot them. If Windows is in a logical partition you will not be able to boot it from grub as you cannot add the boot files or do the repair to add the boot file.

 [https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)


 [https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by kakashi_12 on 2014-06-14
Ok, just looked over my own notes of my triple boot and from what I read about Windows. They said oldest Windows OS first. So, the order I have it in at the top is correct.
And according to my notes when I did my triple boot, I actually had to unplug the HDD with Linux on it so BCD (100 MB partition) would not overwrite it. Then plug it back in after install of Win7. Then I went and made the HDD with Linux on it the Primary Boot Device.
Since I have 3 Win OS's and 1 Linux OS, maybe I should use BCD instead of GRUB. Not sure what your thoughts are. Whatever is easier to edit!
I have 3 separate HDD's. So making all Primary shouldn't be an issue (except Swap should be extended of course).

---

### Post by oldfred on 2014-06-14
I do not know Windows BCD, my last Windows was XP.
With multiple drives you want to keep the Windows boot loader in the MBR of the Windows drive and grub in the MBR of the Ubuntu drive.
Again if you repair the Windows installs by first moving boot flag and run Windows repairs then that partition will directly boot from Windows MBR. But then grub can find the boot files and let you boot each Windows install directly.

Did you review the multiboot site, it explains Windows booting and MBR and PBR booting in general.
 A user who installed two windows & it worked to boot from grub directly
[http://ubuntuforums.org/showthread.php?t=1271600](http://ubuntuforums.org/showthread.php?t=1271600)
Another user who disconnected and used a second drive 
[http://ubuntuforums.org/showthread.php?t=1334346](http://ubuntuforums.org/showthread.php?t=1334346)

---

### Post by kakashi_12 on 2014-06-15
Ok, yes I read them both. I don't fully understand how to remove a boot flag. It sounds complicated with gparted? I don't understand how Linux labels drives (sda, sdb, sda2, etc.).
Can't I just go into BIOS and tell it which HDD's are not bootable?
I think it'd be BEST if I test this ALL out in a Virtual Machine first before doing it for real!

---

### Post by oldfred on 2014-06-15
With gparted you just right click on a partition and set the boot flag. You  can only have one boot flag per hard drive and for Windows it must be a primary partition.
In Windows you set boot flag with the set active command, as Windows calls it the active partition or the one you boot from.

Drives are sda, sdb, sdc etc, partitions are a number or sda1, sda2. No confusion if in Windows a "d" drive is really second partition in the first drive like sda2 or a partition on a second drive like sdb1.

 GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

[https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions](https://help.ubuntu.com/community/HowtoPartition/OperatingSystemsAndPartitions)
[https://help.ubuntu.com/community/HowtoPartition](https://help.ubuntu.com/community/HowtoPartition)
[https://help.ubuntu.com/community/PartitioningSchemes](https://help.ubuntu.com/community/PartitioningSchemes)

---

### Post by kakashi_12 on 2014-06-16
I'm kinda screwed now and need help.
I am trying to change the boot flag from Linux. Built in utility called Disk Utility. When I clicked the 100 MB partition and choose "bootable" to set the boot flag and said "Apply". Now it just sits there Applying, spinning the wheels. Won't finish. I've waited several minutes.
Then I went to set the Linux partition to non-bootable to get rid of the boot flag from there. Now that one just sits there too.
I'm afraid to reboot, since it hasn't finished applying the settings. I've logged out and back in to see if the app would reset, but it's still just spinning wheels.

Should I have UNflagged the one partition, before setting the flag for another?
Should I have put the boot flag on the 100 MB partition or on the Windows partition itself?
Afraid to reboot. How do I fix to set a boot flag?!?!?

---

### Post by oldfred on 2014-06-16
It should not take long at all.

What does this show? One boot flag per hard drive.

sudo parted -l

You can use command line, example is sda2 change sda or 2 if not sda2
 set boot flag on for sda2 (off on others)
sudo sfdisk -A2 /dev/sda
sudo parted /dev/sdb set 2 boot on

---

### Post by kakashi_12 on 2014-06-16
Model: ATA WDC WD6402AAEX-0 (scsi)
Disk /dev/sda: 640GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs
 2      106MB   206GB  206GB  primary  ntfs
 3      206GB   640GB  434GB  primary  ntfs         boot


Model: ATA WDC WD3200AAKX-0 (scsi)
Disk /dev/sdb: 320GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End    Size    Type      File system     Flags
 1      1049kB  307GB  307GB   primary   ext4            boot
 2      307GB   320GB  13.0GB  extended
 5      307GB   320GB  13.0GB  logical   linux-swap(v1)

---

### Post by kakashi_12 on 2014-06-16
huh, i don't understand your commands.

---

### Post by oldfred on 2014-06-16
If you want to move boot from sda3 to sda1 which looks like a typical 100MB boot partition.

I just changed 2 to 1 as example was for sda1 but this is now for sda1. 
sudo sfdisk -A1 /dev/sda
or:
sudo parted /dev/sdb set 1 boot on

You can confirm change by rerunning parted and see that boot moves from sda3 to sda1. You also have a boot flag on sdb1.

---

### Post by kakashi_12 on 2014-06-16
where is the boot flag set right now? According to the results I just posted.

---

### Post by oldfred on 2014-06-16
Number  Start   End    Size   Type     File system  Flags
 1      1049kB  106MB  105MB  primary  ntfs
 2      106MB   206GB  206GB  primary  ntfs
 3      206GB   640GB  434GB  primary  ntfs         [COLOR=#ff0000]boot[/COLOR]

---

### Post by kakashi_12 on 2014-06-16
why does it list a size 3 times for each drive. i really don't understand which drive or partition is which.

edit...
Nvm. I got it now. There are different columns. The whole top section is for one drive and the bottom section is for the 2nd drive.
The way I see it, the bootflag was never moved. I can reboot.

---

### Post by kakashi_12 on 2014-06-16
Ok, I rebooted. I'm fine now. No changes.

I'm still trying to understand how to set the boot flag. I want to switch it from Linux to Windows. Make it use Windows Boot Loader.
And I'm currently trying to work with EasyBCD Edit to add Linux to it. There is an option that says "Write to MBR", but not sure if I click it if it will go to the 100 MB partition or to the Linux partition which is currently set as active.
That's why I wanted to change the boot flag first.

---

### Post by oldfred on 2014-06-16
Only a few here use EasyBCD.
With two hard drives you should have grub installed to the MBR of sdb, so you can boot from it directly and let you choose system to boot. But you have to repair install each Windows so each has boot files, not just the one partition with the boot flag.

       [URL="https://neosmart.net/EasyBCD/"]https://neosmart.net/EasyBCD/
[/URL]
 [http://neosmart.net/blog/](http://neosmart.net/blog/)
[http://neosmart.net/wiki/display/EBCD/Linux](http://neosmart.net/wiki/display/EBCD/Linux)
[http://neosmart.net/wiki/display/EBCD/Ubuntu](http://neosmart.net/wiki/display/EBCD/Ubuntu)

[URL="https://neosmart.net/EasyBCD/"]
[/URL]

---

### Post by kakashi_12 on 2014-06-16
I found out I can just use "Grub Customizer" instead of EasyBCD. Trying to....
As of now, the PC boots to GRUB2.
You can then boot into Linux
OR boot into BCD Loader. From BCD, you can boot into Server 2008 or Windows 7.
I'd like to be able to have only ONE boot loader. How can I disable one or the other and only use one?

When I went to edit my entries and add more with Grub Customizer:
I added sda2 (should be Server 08)
and added sda3 (should be Win7)

When I select my new entries:
sda2 displays an error when I choose it (BOOTMGR is missing. Press Ctrl Alt Del). I do this and it reboots. Server 08 loads fine through BCD.
sda3 loads BCD instead of Windows 7.

---

### Post by kakashi_12 on 2014-06-16
I just installed GParted. And I'm really confused.
Why do I see a Boot Flag for each Drive?
I just want to be able to choose whether to boot into GRUB2 or into BCD. But there is a flag for each drive.

I went into BIOS to try to change the Primary Boot Device, Drive order. And it didn't matter which one I made first. I switched them around and it still boot to GRUB2 instead of BCD.
Is it possible to have more than one MBR? Is there one for each drive?

I'm so confused now.

---

### Post by oldfred on 2014-06-17
Did you look at the multibooters site?

Every hard drive has a MBR. Every drive should have one boot flag on a primary partition. But grub does not use a boot flag, Windows has to have a boot flag.

But in BIOS you set which drive to boot from. Then when BIOS turns control to MBR, a Windows boot loader looks for the partition on that drive with the boot flag and jumps to the PBR or partition boot sector. The PBR will then say to boot with ntldr or bootmgr. 
So another install in another drive can be selected from BIOS to boot a totally different system. 
Most system have a one time boot key, where you can select another device to boot from.

My flash drives all look like added hard drives so each of them also has a MBR. And to boot my flash drive, I click f12 on my system as a one time boot key to choose which hard drive to boot from.

---

### Post by kakashi_12 on 2014-06-17
No, I didn't see the link for it.
Linux does not have a boot flag? I saw it set to the ext3 partition in Gparted.

---

### Post by kakashi_12 on 2014-06-17
I haven't even started fresh yet, partitioning everything and starting clean.
I guess my problem is, I want to get the boot loader working right first before I start over.
I want there to be only one boot loader.
GRUB2 won't load Server 08 (says BOOTMGR is missing). Although BCD loads Server 08 just fine.
BCD, I can't get to load first because GRUB2 loads first.
Maybe a fresh install would help though.
Is there a way to install Ubuntu without a boot loader so I can use BCD?
Or to disable BCD so I can use GRUB?

---

### Post by kakashi_12 on 2014-06-17
[http://paste.ubuntu.com/7659570/](http://paste.ubuntu.com/7659570/)

Not sure if that helps. I now see that there are 2 MBR's. One for each drive. GRUB2 is on one of the MBR's and BCD on the other MBR of the other drive.
Can I just wipe one of the MBR's? That way I'll only have one boot loader?

---

### Post by oldfred on 2014-06-17
System only boots from the one hard drive you specify in BIOS to boot from. So only one MBR is in use at one time.
But EasyBCD will chain load to the other copy of grub. You have to have grub installed for EasyBCD to find it. It actually uses grub4dos which is an old version of grub for use with NTFS partitions.

Are you trying to use 10.04? That is obsolete except for sever version. You need to install 12.04 or 14.04.

If you move boot flag to sdb2 and run Windows repair to add bootmgr and BCD then grub can boot all 3 installs of Windows.

But you have grub installed to the MBR of your Windows drive and the Windows boot loader installed to the MBR of the Ubuntu drive. It should be the other way around.
Use Boot-Repair's Advanced mode and choose your Ubuntu install and install grub to sda. And chose Windows and install Windows boot loader to sdb.

See post #3 again please.

---

### Post by kakashi_12 on 2014-06-18
That makes sense. I thought that might have happened. Not sure how I accomplished that.
I thought 12.04 (which ever version is Lucid Lynx) was LST (Long Term Support) meaning 3 years.

Maybe it would be best if I just start from scratch like I originally planned.
I can install all Windows OS's on one HDD with the other HDD unplugged.
Then install Linux OS on the other HDD and have the Windows HDD unplugged.
Then specify which one I want to load first in BIOS.

I was thinking of installing Linux fresh, but choose in the install options not to install GRUB, then that way I can use just Easy BCD to add Linux.
But you're telling me that GRUB is required for Linux to run? Or that BCD uses and creates GRUB4DOS to run it?

---

### Post by oldfred on 2014-06-18
Grub is required for Linux to boot. It is both a boot manager which lists boot options with grub.cfg and a boot loader which is required to boot a system.
In Windows the BCD is the boot menu ( as it has list of bootable devices) and bootmgr is the boot loader which also loads the BCD (I believe).

Your 10.04 Lucid desktop has expired, server version is supported for about another year.
[http://ubuntuforums.org/showthread.php?t=2229730](http://ubuntuforums.org/showthread.php?t=2229730)

       12.04 LTS 	Precise Pangolin  released April 2012 	supported until April 2017

            14.04 LTS 	Trusty Tahr  released April 2014  supported until 	April 2019

You have to have grub installed. I think EasyBCD suggests installing grub2 to a PBR or partition boot sector so it can chain load using a grub4dos chain boot entry. But better to chain to a MBR on another drive as if grub2 is forced into a PBR it has to convert to blocklists or hard coded addresses. That cripples grub as any update to grub may move file on drive and hard coded location needs update or you have to reinstall grub again. So using EasyBCD makes grub less reliable. But since you have another MBR use that not a PBR and you will have less issues.
But still better to keep Windows on Windows drive MBR so you can directly boot it anytime, and use grub in the MBR of the Ubuntu drive to boot. It will boot Windows in most cases without issue. 
A few just use the BIOS one time boot key to choose which system to boot when they have multiple MBRs.

---

### Post by kakashi_12 on 2014-06-18
Sounds like that's my best/easiest bet. Turning on the option for BIOS to prompt be to choose a boot device.
And when I install my OS's, I'll have plug HDD plugged in at a time. Less headache and less research.

.... Just tested out trying to set the 'prompt' in BIOS to prompt me which device to boot. But I either didn't set the right option or it isn't working. Maybe it's because my other MBR is messed up and only one is working. Guess I'll have to find out when I reformat all. Or maybe my BIOS needs updated to do that option.
ASUS P7P55D-E Motherboard.

---

### Post by kakashi_12 on 2014-06-18
I see an option where I can select boot device (Press F8) and it allows me to select a HDD. But I can't make it stay on the screen to prompt the user and wait for a response.
I have to set the boot priority. It won't allow me not to.

---

### Post by kakashi_12 on 2014-06-19
Read the whole page about multi-booting. Very informative and very helpful. 3rd party boot managers sound pretty promising. Just not sure if you're suppose to install the OS's first then the boot manager or the boot manager first then the OS's.

---

### Post by oldfred on 2014-06-19
Unless you have a bootable device, hard drive or flash drive the boot options will not show it. So if you have not configured any additional  boot devices, boot screen may not have anything to show other than default.

I started configuring multi-boot before most of the scripts appeared. And since I started to learn grub2 after not originally liking it, I found it to be like when you have a hammer everything looks like a nail. I use grub2 for everything. 
So I manually install grub to any device that is not a full install. But any full system install includes grub.

You can use this procedure for either BIOS or UEFI and for any second device.
       Flash drive to boot in UEFI or BIOS - sudodus
[https://help.ubuntu.com/community/Installation/UEFI-and-BIOS](https://help.ubuntu.com/community/Installation/UEFI-and-BIOS)
aHowto help USB boot drives - sudodus
A tool that helps boot some computers from [other] USB boot drives - Chainloader
[http://ubuntuforums.org/showthread.php?t=2196858](http://ubuntuforums.org/showthread.php?t=2196858)
Howto make USB boot drives 
[URL="http://ubuntuforums.org/showthread.php?t=1958073"]http://ubuntuforums.org/showthread.php?t=1958073

      [/URL] Install to external drive. Also any second drive.
Also shows combo box with location of grub2 boot loader
[https://help.ubuntu.com/community/Grub2/Installing](https://help.ubuntu.com/community/Grub2/Installing)
Does not hightlight changing boot loader to sdb, but shows other install screenshots:
[http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot](http://askubuntu.com/questions/312782/how-to-install-ubuntu-on-separate-hard-drive-in-a-dual-boot)
[http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option](http://askubuntu.com/questions/274371/install-on-second-hard-drive-with-startup-boot-option)
Install 14.04 Something Else explanation and screenshots (note boot load to VM, most may install to MBR of drive sda, or sdb)
[http://www.tecmint.com/ubuntu-14-04-installation-guide/](http://www.tecmint.com/ubuntu-14-04-installation-guide/)
And you want this screen to choose where to install the grub2 boot loader which is only available with Something Else or manual install
[https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29](https://help.ubuntu.com/community/Grub2/Installing#Installing_Ubuntu_to_a_Specific_Partition_.28.22Something_Else.22.29):

    [URL="http://ubuntuforums.org/showthread.php?t=1958073"]
[/URL]

---

### Post by kakashi_12 on 2014-06-25
Currently testing everything out a virtual machine for now.
While I'm thinking of it, if I run a bootable disk/program called Kill Disc, will it wipe MBR? If not, how do I wipe MBR. Is there a Linux tool to wipe MBR's? Because I've heard Windows tools don't wipe MBR that have GRUB written to them.

---

### Post by oldfred on 2014-06-25
MBR has two parts. First part is boot code and that you never really have to overwrite as installing a new boot loader for a new system will do that. But second part of MBR is the partition table, rarely would you want to overwrite that.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)

---

### Post by kakashi_12 on 2014-06-26
I don't want to restore. I want to wipe clean MBR's so that I can start fresh!

---

### Post by kakashi_12 on 2014-06-26
Finally, SUCCESS! I've been trying to figure out how to fix this for years!
How to get only ONE boot loader and not both BCD and GRUB. Finally got it (done in Virtual first, will do for real probably next week or so)!
Thanks for everyone's help so far! Reading the info on the Multi-bootloader site REALLY helped me to understand things.
I LOVE Linux, but I've made my decision to use BCD as the Boot Menu/Loader. I have 3 Windows OS's and 1 Linux OS. Plus it seemed to work better.
Found that (like the multi-boot loader site suggested). It is best to install GRUB to the PBR and not the MBR. I found that was the one of the mistakes I was making all along, was that by default it was overwriting the Windows MBR instead of using it's OWN.

I can follow these instructions (applies to 1 HDD):
[http://www.youtube.com/watch?v=xlTgaWs9BD0](http://www.youtube.com/watch?v=xlTgaWs9BD0)

Above instructions more so apply to when you only have on HDD in the PC. Since I have multiple HDD's, see below....

[U]Final Resolution:
[/U]
a. Plug in one HDD only! Leave the 2nd HDD unplugged from MotherBoard.
b. Load Linux disc and install, Create ext4 partition (Primary partition), mount point is /
c. Create swap (Primary partition). Install Linux!
d. install and open Grub Customizer.
e. 2nd tab, uncheck options to look for other OS's and show boot menu
f. 1st tab, refresh, save. Exit. Reboot. Verify that menu is gone. Shutdown.
g. Unplug Linux HDD from MB and plug in the blank HDD to MB.
h. Install XP, Win 7, SP1 (for Win7), then Win Serv 08, (in that order).
(note: after installing XP, immediately disable network adapter!)
i. Shutdown. Plug both drives into MB.
j. Boot into BIOS and make Win HDD first boot device.
k. Boot into Win7, Install Easy BCD
l. Modify entries (names and order), Save button
m. Add New Entry, Select Linux tab, choose GRUB2 from drop down menu, name OS, choose the partition where Linux is (this is also where GRUB is), Add.
n. Review, when done modifying BCD, do NOT write MBR. Just save and exit.
o. Reboot and test all boot entries!
p. plug in 3rd HDD and set up an Extended Partition with a Logical Volume. Use this for Personal Data only.

---

### Post by kakashi_12 on 2014-07-05
> **kakashi_12 said:**
> 
While I'm thinking of it, if I run a bootable disk/program called Kill Disc, will it wipe MBR? If not, how do I wipe MBR. Is there a Linux tool to wipe MBR's? Because I've heard Windows tools don't wipe MBR that have GRUB written to them.


Answer = Yes.
I ran Kill Disc on my physical PC. I had to do it in 2 steps to wipe both drives.
After both HDD's were wiped clean, I booted to Ubuntu Repair Disc and created a Boot Summary.
When reading the boot summary, it said.....
 => No boot loader is installed in the MBR of /dev/sda.
 => No boot loader is installed in the MBR of /dev/sdb.

[http://paste.ubuntu.com/7752944/](http://paste.ubuntu.com/7752944/)

:)

---

