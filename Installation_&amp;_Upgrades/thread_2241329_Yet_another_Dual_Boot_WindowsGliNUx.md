---
title: "Yet another Dual Boot Windows/GliNUx"
date: 2014-08-25
forum: Installation &amp; Upgrades
---

### Post by Trad_dog on 2014-08-25
[B]Yet another Dual Boot Windows/GliNUx: 
OEM shipped Windows OS, Raid, EFI, Windows 8.1, Kubuntu 14.04.[/B]

 
In this post, GliNUx stands for the GNU/Linux Operating system. The GliNUx that has been used in this report is actually Kubuntu 14.04 LTS.  

 To follow these loose instructions, you may find useful to have at hand:
- a small USB pen drive (to hold the RAID driver)
- a large (at least 32GB) USB (preferably 3.0) drive
- a large external hard drive for the System backups.
Then, a lot of time and patience (that's where the Finish would involve "sisu", I guess) are compulsory ingredients.  
 **Context**

 It had become too easy to switch machines to Free Software in the past few years. So my new laptop arrived a couple of months ago, I took a look at Windows 8, waved it bye-bye and plug my GliNUx DVD into the drive. That&#8217;s when my journey started. The ordeal has been such that I thought reporting a few of its stages might help some other fellow traveller. I do not dwell into details really here. For one thing, I am not an expert. Then this is intentionally giving a rapid overview of what kind of issues you might run into. It is meant to be read along with other (better) reports. 
The first surprise is that when I rebooted into the live DVD, I was taken straight to the Microsoft&#8217;s OS again. Changing the boot order was not possible. If you arrived here, you probably know already about Secure Boot. You cannot access the BIOS any more. 
The BIOS has been supplanted by the Extensible Firm Interface (EFI or UEFI for Unified). So the era of naive live boot with a USB GliNUx into any computer and the freedom (power) it gave is over. That took me quickly to Rod Smith&#8217;s excellent site and tools. Which I duly followed. You first need to deactivate the Secure Boot (from Windows, hold the Shift key while selecting Restart. Go to Troubleshoot > Advanced Options: UEFI Firmware Settings.)
**Getting ready for the worst (...is not an easy exercise)**

Before proceeding, I prepared a recovery drive so as to keep my current OS out of trouble. I proceeded as carefully as possible as I was trying to build an embryonic workable knowledge in the face of the Tsunami of new information that came with the advances and changes in all the OS and hardware I was dealing with. After several days of prudent experiments, one step took me over the edge: no boot. I smiled proudly and plug my USB recovery drive into the laptop: to find out it had been a vain effort although the reasons where specific to my machine (the second drive behaves in a flimsy way and my RAID was lost but I did not know that at the time). 
At any rate, it might be useful at this stage for people upgrading after several years to know that the recovery/backup program from the Redmond firm has no less than four components: 
 the Recovery Disk functionality, the Backup System one, the File history (think "Time Machine" on Mac OS) and another service for saving restore points on your local drive. To really protect yourself, you probably want to prepare a Recovery Disk (in Windows 8x -> Start View, search &#8220;Recovery&#8221; and select &#8220;Create a recovery drive&#8221;). That should give you a way of booting back into your system, if you are lucky. Besides you should prepare a system backup (Start View, search &#8220;File History&#8221; and choose &#8220;Save a backup&#8230;&#8221;). Confusingly, the System backup which makes a monolithic binary image of your system to be restored in one single go is accessible in the bottom left corner of the application which allows you to back-up individual files -- it is confusing because the details are actually subtly but relevantly different). While performing this latter operation,  if  you  come  across an error about lack of space, this is probably unrelated to your target drive. We shall come back to the issue later on but for the time being, you might want to check that one of your partitions planned for backup does not respect one of the following constraint: for partition smaller than 500kb, the free space on the partition should be at least 50MB. For larger partitions, you need 300Mb. The likely culprit is the Recovery partition. I suggest you save it independently somewhere else and delete its content. This is already saved on a drive by the previous Recovery Disk operation. So no worries.  
 **Nature of the Dual Boot described here**

 There are score of dual boot description out there. You need to make sure you read first the most relevant one for your case. Here we address the simultaneous issues of:
- OEM Microsoft Windows (as a side point)
- dual boot Windows 8.1 and Kubuntu 14.04
- EFI system
- Fake (through the Intel Rapid Storage implementation) Raid system 
The last point is probably the most pertinent. If you are not booting on a Raid, the task is easier. Now, in my case, I had not paid enough attention to the spec of my machine and I had not realised my SSD drive from which I was booting was not a 256GB SSD but actually a 2x128Gb raid array. This caused a large part of  the issues and the blur while reading other reports out there. By the way, the reason for the RAID 0 is not only that  128Gb drives are cheaper as I thought initially. The reason why the manufacturer engineered such a solution is that it is also FASTER. Which may or may not be a element in your decision to break the Raid array or not. Installing the two OS on two different drives of same size would have been a considerably easier task as it turns out. But if like me, you think "let's see if I can do it", take courage: it has become lately easier and cleaner (if not transparent as we always initially feel it should be), thanks to the effort of anonymous developers all over.  
 **The issues for the layman**

 The RAID technology (writing on several drives simultaneously) is still undergoing developments and implementations. The outcome of these efforts is not one but 3 distinct implementations of the concept so far: the so called hardware, software and "fake" RAID. The hardware RAID means that a piece of hardware takes care of managing the array. The two other ones delegate the task to the OS and ultimately to your chip. In order to read and write on any Raid array, as for any other devices, the OS needs a specific driver. As it turns out, the drivers for the former are less standardised than for other type of hard drives (hdd) or solid state drives (ssd). So both Windows and GliNUx needs to load these drivers before being able to boot the system proper (specialists might object to my use of vocabulary or, altogether, to my representation of the concepts here. Feel free to correct). The software RAID and fake Raid are actually relatively close concepts. The software RAID has been present in GliNUx for a very long time, implemented in the dmraid branch of the larger family of the dm (device mapper) tools and more recently into the mdadm (multiple devices admin) function, an interface dedicated to RAID specifically. The fake (BIOS) raid seems to be more recent and has been implemented by several firms, under different labels and branding. Intel Rapid Storage Technology (IRST, formerly Intel Matrix Storage Management (IMSM)) and Nvidia RAID technology are the ones I came across. These have been supported by dmraid but the preferred interface in GliNUx (meaning actively developed and endorse by the vendors) is through the mdadm. This is what this presentation uses to deal with the RAID part. Beware that not all GliNUx distribution seems to ship the recent version of mdadm that supports this implementation. 
The EFI specification, on the other hand, changes the way a computer sees and uses partitions are represented as well as the procedure it boots from these. If you know nothing of these (as I did) and are really in a hurry, it might be useful to get some acronyms out of the way. The EFI separates two concepts that used to be linked in many personal computers since the 1980s and the advent of the MBR (Master Boot Record) specification: the way partitions are layed out on a specific device and the way a computer starts its operating system (init/boot process). To start with, in modern computers from now on and until the next technology comes along, the way the partition are represented is now through the GPT (GUID Partition Table: see Rod Smith's excellent documentation on the subject). Besides, the EFI specifies (loosely I think) how an OS should boot. From several thousand light years away, a specific partition  (ESP for EFI System Partition, most often a small FAT32 formatted partition) should be present somewhere on your device. From the information gathered in the specific directories of this ESP partition, the boot loader should do a relatively high level job of finding where the boot-able systems are.
 **Setting up the Raid**

 This step should not be necessary. In all likelihood, the Raid has been set up by your OEM and is up and running. If the raid is not available on your machine, however, or you want to start from scratch, you have two avenues to set it up. The first one is directly through the BIOS, the other is by launching first a GliNUx install.  
 I assume the BIOS option here. Depending on your BIOS, you may have a simple set up option for the Sata controller in the Advanced tab or you may enter a more thorough console by typing Ctr+I and access the Intel Rapid Storage Technology console. Choose to create the drive and add the devices that should be included in the RAID.  
 The GliNUx route involves launching a live version of GliNUx, downloading the latest version of mdadm and issuing an instruction similar to (slightly more info in the GliNUx section of this report):
  ```
sudo mdadm --create /dev/md/imsm --metadata=imsm --raid-devices=2 /dev/sda /dev/sdb
```
 The imsm identifier for the metadata is for Intel Matrix Storage Management-type of metadata, assuming this is the one you have.  
 **Getting your Microsoft Windows ready**

 If you have a (OEM) Windows operating system and are happy with it, from Windows, shrink your partition to allow for sufficient room for your GliNUx root and swap partitions. You can create your Recovery Drive and prepare a System Backup. 
 If you have to proceed to a clean Windows install, on the other hand,  here is a few pieces of advice.
Assess what RAID implementation you have. Assuming you have passed the secure boot hurdle, you should be able to access the BIOS (press DEL or some other key just after powering on the computer). Look through the tabs in your BIOS (usually the "Advanced" one). In my case, the Raid is an Intel RST implementation. Go to the RAID provider web site and download the driver. Store it on a FAT formatted UBS drive. 
 Besides, as I write this tutorial, Microsoft has messed up with his system backup (and as said you should have one). In order for the File History System Back Up to work properly, the steps are simple though. If involves creating 3 partitions, in that order:
- a recovery one of at least 500MB. Formatted NTFS
- an ESP. Rod Smith suggests 550MB: don't be cheap. Formatted FAT32.
- a Windows partition. Size to your liking. Formatted NTFS. 
That's it. This is easily done from a Live GliNUx distribution with Gparted but you'll need to go through the mdadm procedure described later. Alternatively, you can do it from a command line within the Windows that you can access by typing Shift+F10 on the screen where you are asked to choose the device on which to install Windows. You can then enter the diskpart command line executable (by default the Command terminal is in Administrative mode) and create your partition by typing a bunch of instructions (this is what I did) or read a predefined script (probably easier and safer). There are readily available examples of scripts or command lines available on the internet. 
Install your system. You might need to install the drivers from your OEM web site. This will take several hours and numerous re-boots. Once you have recovered a full fledged OS, take a breath and save this valuable job. Create a Recovery Drive on  a USB large drive (will help if you cannot boot): see above. Then, create a full System Backup (will help if your working Windows operating system or its partition is damaged).  
 **Installing (K)Ubuntu 14.04**

 Installing Ubuntu on EFI has been available for at least one or two versions. Whether these installations were compatible with a dual boot is unclear to me. I would strongly suggest to download the latest version of Ubuntu iso file.
 Burn the iso or install it on a UBS drive. Make sure than in your Bios you either set the precedence of the CD or USB drive higher than the hard drive or at the boot, hit F11 and choose to boot from your removable Ubuntu device.
 Choose to Try Ubuntu &#8211; that is do not try to install it now. The reason is currently GliNUx does not have pre-installed a Raid driver. Open a terminal (F2+Konsole). Then install mdadm and gparted :
 ```
$>sudo apt-get install mdadm gparted
```
 Enter/OK twice when prompted.
 If you were to launch gparted now you would notice that the Windows partition is not visible and that instead of one disk, you have two or several individual devices. Bear in mind that these disks have all the informations necessary (metadata) necessary to enter the array and that your controller is ready to reveal the array. You are just missing the driver to be able to see it in GliNUx. In a terminal , type :
 ```
$>sudo mdadm &#8211;assemble &#8211; scan  
```
 or :
 ```
sudo mdadm -As
```
 when you have done it a dozen of times...
 This will go through all potentially available Raid-enable devices and will active them in GliNUx.
 In Gparted, refresh the devices and now you should have your drive showing up in the drop-down menu with all the Microsoft Windows partitions.  
 Where you have created space on the device, create a  GliNUx primary partition (ext 4 should be a good choice) as well as a swap one.  
 You are ready to install. Launch the Install Ubuntu 14.04 :
 - Choose to download updates (not sure but I believe the current distribution crashes at the Grub install, which did not happen when I downloaded the updates. I am wondering if there has not been a patch since the iso was put on the internet).
 - On the Partition tab, choose manual.
 - on the next screen : click to install on the primary partition you have just created, leaving the root partition where it is.
 - Importantly, choose to install grub on the root of your RAID array (not one of the components!)
 Proceed through the installation normally.  
 You are almost done. At this stage, you should be able to boot individually either Windows or Ubuntu. And you could stop here, as you can choose which OS to boot through your BIOS (F11 when powering your machine on should give you a menu with a Windows or Ubuntu entry).  
 If you want a somewhat slicker installation, you should set up the multi-boot manager. You can defer the responsibility to the jack-of-all-trades, grub (it will then be both the boot manager and the boot loader). If you have more affinity with the Redmond people, the Windows boot loader can do it and its flash screen will respect the look and fill of a Microsoft Windows machine. Or you can enrol Rod Smiths powerful rEFIND for this task which makes more customisations possible including on its aesthetic flash screen.  
 I choose rEFIND. I started to do it from GliNUx since it was open. You may want to follow the Windows manual installation though as the rest will prove ([http://www.rodsbooks.com/refind/installing.html#windows](http://www.rodsbooks.com/refind/installing.html#windows)). I mounted the ESP partition :
 ```
$>mkdir -p /boot/efi
 $>sudo mount /dev/mapper/isw_rd0 /boot/efi
```
 I then installed the rEFIND package available in the Ubuntu repository :
 ```
$> sudo apt-add-repository ppa:rodsmith/refind
$> sudo apt-get update
$> apt-get install refind   
```
 Please refer to Rod Smith pages for actual commands (this last ones were done by memory) :
 [http://www.rodsbooks.com/refind/installing.html](http://www.rodsbooks.com/refind/installing.html)  
 Badaboum ! The installation partly failed complaining that /dev/sda and /dev/sdb were involved in a Raid array (which is correct). I concluded the rEFIND package was not fully RAID compliant. It did install a /boot/efi/refind directory though, with files in it.  
 To correct the last bit, I booted in Windows and in a command line terminal as administrator (Start Screen->Search->Command, right click, run as Administrator &#8211; make sure you use a standard command line and not a Power Shell, which might take you off track badly) :
 ```
**bcdedit /set {bootmgr} path \EFI\refind\refind_x64.efi**
```
 The hope here is that this post will be a useful complement to more technical and thorough tutorials on the web.

---

