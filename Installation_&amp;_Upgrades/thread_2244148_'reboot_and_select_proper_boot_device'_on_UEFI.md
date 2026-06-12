---
title: "'reboot and select proper boot device' on UEFI"
date: 2014-09-14
forum: Installation &amp; Upgrades
---

### Post by JDAIII on 2014-09-14
I am having issues installing Ubuntu Gnome 14.04 on my efi enabled laptop. I got the OK from work to wipe windows and install linux over the weekend, after trying at least a dozen distros in VMs over the last few weeks, I settled on Ubuntu Gnome 14.04. I disabled fastboot in windows, then created a live usb with unetbootin, then rebooted, disabled fastboot in the bios and changed boot order to USB first.  Then I ran the install ubuntu gnome and during the install process, I created new partition table. Yes, I toasted windows because I felt like it, and guess what, it felt goood. I made the following: swap partition 20GB, efi partition 200MB, logical ext4 as / 100 GB, and logical ext4 as /home 360GB. I finish the installation and click reboot now and it reboots into Ubuntu Gnome as it should. I installed some software, my preferred shell and terminal and then I decided to restart the machine to try out my settings and I receive a message that says : 
reboot and select proper boot device 
or insert boot media in selected boot device and press a key.

Now I have been searching forums for the last 4 hours and googling every derivation that I can of this. My laptop is a toshiba S55-A5236. It has efi. I have tried using it's CRM(if memory serves) option which was the other option in the bios where it had UEFI. When I tried that all options with my live usb came up with a linux prompt asking for my login and password. I have gone back to UEFI but still not booting after the first restart.

Other things that I have tried:
1. boot-repair which gave me the following links: ( the only three times that I decided to take pics with my camera. tried this a dozen times)
[http://paste.ubuntu.com/8339849](http://paste.ubuntu.com/8339849)
[http://paste.ubuntu.com/8339576](http://paste.ubuntu.com/8339576)
[http://paste.ubuntu.com/8339130](http://paste.ubuntu.com/8339130)
2. tried efibootmgr
Specifically after I installed ubuntu gnome and it booted fine, then I restarted and it gave me the reboot and select proper boot device so I booted into the live usb and installed efibootmgr and ran 'sudo efibootmgr BootCurrent' and I saw that my hard drive was not listed. I saw three entries for my network devices, my usb dthumb drive, and my cd-rom, but no hard drive. My efi partition was set as sda1 so I decided to give 'sudo efibootmgr -c' a try. I then ran 'sudo efibootmgr BootCurrent' again and it now listed linux in 0000. Rebooted same issue. However when I booted back into liveusb and I ran 'sudo efibootmgr BootCurrent' it no longer shows linux in the list at all let alone 0000.
3. tried copying the contents of the /boot/efi folder to the /boot/efi folder on my / partition.

ubuntu-gnome@ubuntu-gnome:~$ sudo efibootmgr BootCurrent
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0000,0000,0000,0000,0004,0002,2003,2001,2002,0003
Boot0001* UEFI: Network Card 
Boot0002* UEFI: Network Card 
Boot0003* UEFI: SanDisk U3 Cruzer Micro 8.02
Boot2001* EFI USB Device
Boot2002* EFI DVD/CDROM
Boot2003* EFI Network

Ideas:
1. I'm not sure where, probably in boot repair, I saw something that said there was an issue with me not using GParted to set up my partitions. I could try this. I set them up in the ubuntu installer partition tool.There should be better information as to the proper way to install using UEFI when setting up the partitions. 
2. I wish that I could find instructions on exactly how I should be partitioning my drive. I see a lot of conflicting information and this has made if far from an efficient endeavour.

Partition information:
Device      Type      Mount Point       Size           Used
free space                                      1MB         
/dev/sda1  efi                                  199MB       199MB     
/dev/sda2  swap                              19999MB    0MB
/dev/sda3  ext4       /                       99999MB    1767MB
/dev/sda4  ext4       /home               3599903MB 8842MB

And I have tried pointing the device for boot loader installation to both sda and sda3. Neither worked. Should I be trying sda1 on this?

I am attempting to give as much information as possible since I only have 24 hours to get this machine booting. I would be happy to attempt any suggestions.

Thanks ahead of time if anyone has any suggestions. And again, I tried googling many derivations of this and have searched the forum and other forums.

---

### Post by JDAIII on 2014-09-14
I forgot to note that before the Reboot message comes up, I first see:
Checking media presence....
No media present

I still receive the error when trying to boot the second time after an install, but I changed the boot order in efibootmgr and it seems to have persisted with 0000 however the Ubuntu entry that was at 0000 when I checked this before I rebooted out of the liveusb, is no longer listed under 'sudo efibootmgr BootCurrent'. Before, it showed Ubuntu in place 0000 and on reboot, it persisted my boot order but lost my install from the list. Ideas?

Could it be that the setting is not persisting? Do I need to created a script that Adds it again on reboots and sets it to next boot?

If so, and idea what setting to put for it, brain is fried and not sure if I want to follow this rabbit hole.

---

### Post by fantab on 2014-09-14
You insist that you have EFI/UEFI boot, yet you say you have created an Extended and a logical partitions, which indicates that the HDD is 'msdos' and not GPT as it should be on a UEFI system.
```

parted -l:

Model: ATA SSD2SC480G5LC763 (scsi)
Disk /dev/sda: 480GB
Sector size (logical/physical): 512B/512B
**Partition Table: gpt**

Number  Start   End     Size    File system     Name  Flags
1      1049kB  200MB   199MB   fat32                 boot
2      200MB   20.2GB  20.0GB  linux-swap(v1)
3      20.2GB  120GB   100GB   ext4
4      120GB   480GB   360GB   ext4

```

That confirms that you have GPT table. GPT does not have any primary partition limit... so no Extended/Logical partitions.
On GPT all partitions are primary.

> disabled fastboot in the bios and changed boot order to USB first.
You must change it back to boot your ESP [Efi System Partition] first. In your case this should be /dev/sda1 FAT32.

Boot-Repair has installed Grub in 'MBR' of /dev/sda - this is incorrect on an UEFI machine. Grub should install in the ESP.
This happens because you wrongly boot Ubuntu USB/DVD in BIOS mode... Check your UEFI menu and make sure 'UEFI' boot is enabled.

Also IMO that 20Gb swap is an overkill. 2-4Gb of SWAP is plenty. However, if you Hibernate your machine then, your SWAP should be equal to or more than the RAM in Gib and not Gb.

If I were you I'd set up my HDD as follows:
1. /dev/sda1 500Mb FAT32 ESP 'boot'
2. /dev/sdb2 25Gb Ext4 (/) for Ubuntu root.
3. /dev/sdb3 25Gb Ext4 (Free) in case I want to dual/multi boot with other flavors, versions of Ubuntu or other distros.
4. /dev/sdb4 AllGb Ext4 (/home)
5. /dev/sdb5 2-4Gb SWAP

I'd suggest you reinstall ubuntu.. or run Boot-Repair again but make sure your Ubuntu USB boot in EFI mode: [See here]("https://help.ubuntu.com/community/UEFI#Identifying_if_the_computer_boots_the_Ubuntu_DVD_in_EFI_mode").

---

### Post by JDAIII on 2014-09-14
Thanks for the reply.

Yes, my swap is a bit big, but I doubt that is causing the issue. On my next reinstall, I will knock it down to 16GB to match my RAM. Last time I used linux regularly was in the late 90's which as I remembered, RAM was expensive so swaps were used extensively.

As for my live usb booting into UEFI mode, yes it is. I expected that to be a given in my original post, but I will note thnigs like that in the future. Only once did it boot into bios mode and that is when I disabled UEFI in the bios. It boots in UEFI mode every time I am reinstalling. I am assuming that you are saying that I must set the device for boot loader installation to the EFI drive which I have been setting as sda1.

As for the logical vs Primary partitions being created, I honestly just used the partitioning tool in the ubuntu installer. I changed nothing in that area. I'm using Gparted from the liveUSB, then I am going to install on top of that. 

As for the esp being the first device to boot in the bios, I can make that change. I tried that a few times, but no luck before, however I will incorporate with the other changes.

In regards to boot-repair, I am not sure how I am to run it to install as you have said. I did use the advanced options and select things like UEFI and disable the wait and so forth. I will run again on my next install. I installed at least 15 times yesterday to test different settings/options that I found on forums. I will try what you have suggested.

About the partitioning recommendation that you posted, If I remember correctly (was in the 90's) the swap was supposed to be the first partition that you made because it would load faster. I'm using an SSD so I doubt that matters now days, just curious. I will also not be adding a partition for multibooting. I use VMs extensively and will just create a new VM should I want to try a new distro.

For reasons that would be inconsequential, I am going to make the / 100GB. Just trust me on that. So for the partition settings, I am posting a few pics, and lets hope they come out, First is the creation of the efi partition. If I just make a fat32 partition and tell the installer to install the boot loader there, it bawks at me. So I set up the efi partition using the tool as you see here:
[IMG]http://i31.photobucket.com/albums/c355/cheshireccat/help/Screenshotfrom2014-09-14145938.png[/IMG]

And given that, I have finished creating all of the partitions and am going to install again. If it does not reboot as before, I will use boot-repair and attempt to pint it to sda1 and the efi partition.

[IMG]http://i31.photobucket.com/albums/c355/cheshireccat/help/Screenshotfrom2014-09-14150315.png[/IMG]

When I noticed that the efibootmgr was losing the ubuntu item listed at 0000, do you not think that this was an issue?

---

### Post by JDAIII on 2014-09-14
OK, so I tried a few more things.

First I tried wiping out the partitions and creating them in GParted and then just assigning them a mounting point in the ubuntu install partition tool. I set the partitions here according to fantab's recommendation:

[IMG]http://i31.photobucket.com/albums/c355/cheshireccat/help/Screenshotfrom2014-09-14153012.png[/IMG]

Then I set them in the ubuntu install partition tool as follows.

[IMG]http://i31.photobucket.com/albums/c355/cheshireccat/help/Screenshotfrom2014-09-14153242.png[/IMG]

It bawked at me for not having an efi boot partition, but I continued anyway,

And it gave me the same error yet again. It booted once, then I rebooted and it was giving the error. I went ahead and tried efibootmgr and I ran 'sudo efibootmgr -c' since my efi or boot partition is sda1, then I checked the boot order, then I set nextboot, then I restarted. No luck.

I should note that every time I boot up, I make sure that the bios has the HDD as the first boot device. 

Then I tried boot-repair. Now I remember why last night I had not selected the efi drive for boot repair. Boot-repair would not allow me to select sda1 in any of the three fields. Well, the last one is obvious, but the other two were not going to let me change them. And the MBR tab was greyed out no matter what.

[IMG]http://i31.photobucket.com/albums/c355/cheshireccat/help/Screenshotfrom2014-09-14155850.png[/IMG]


I am open to any and all suggestions as to how to make this work. I've reinstalled 5 times in the last 2 hours to test changes so I'm not hesitant to try anything that requires blowing away the partitions and starting over.

---

### Post by oldfred on 2014-09-14
Please attach screen shots not post in line. You can attach with advanced editor and paperclip icon. 
Not everyone has high speed Internet.

Either partition scheme should be fine. I prefer 20 or 25GB for / (root) and rest for /home or data partition(s). And unless hibernating you actually only need a little swap just in case like 2GB. I have 4GB of RAM and never use swap. If editing videos or some other special cases may larger swap make sense.
But you must have an efi partition for UEFI boot which must be FAT32 with the boot flag. Or have a bios_grub partition unformatted of 1 or 2MB with bios_grub flag for BIOS boot. You actually can configure a system for both with some effort.

You probably have grub still in MBR from a BIOS install. But without a bios_grub partition that will never work. But you do show mounting of /efi partition in fstab, so your install is using UEFI to boot.

New systems have multiple UEFI/BIOS settings and you must be consistent. If your install is BIOS and you turn on UEFI it will not boot. If install is UEFI and you turn on secure boot it will not boot. And many UEFI/BIOS switches are not clear. Some will auto switch by looking for an UEFI boot option in efi partition, then look for BIOS boot using MBR. But not with secure boot on. So make sure your settings are UEFI on, secure boot off, CSM/BIOS/Legacy off. Some when turning UEFI on auto turn off CSM mode.

I thought Toshiba's booted Ubuntu in UEFI mode ok. But HP & Sony modify UEFI to only boot Windows and work arounds are required for those. Those require the Windows folder and Windows efi boot file so we create the Windows folder and rename grub to be the Windows file and it boots Ubuntu thinking it is booting Windows.

Some other Toshiba and issues they had.
 TRIPLE BOOT (with Win 8.1, Linux Mint 17, Ubuntu 14.04) ON A UEFI-BASED SYSTEM - Toshiba Satellite C55T
[http://ubuntuforums.org/showthread.php?t=2240742](http://ubuntuforums.org/showthread.php?t=2240742)
 [SOLVED] 12.10/64 bit Toshiba C55D-A5146 notebook with Win 8.1 pre-installed (14.04 worked)
[http://ubuntuforums.org/showthread.php?t=2216279](http://ubuntuforums.org/showthread.php?t=2216279)
Toshiba Satellite P50 model number: P50-A-01E Haswell processor
[http://ubuntuforums.org/showthread.php?t=2163854](http://ubuntuforums.org/showthread.php?t=2163854)
Turned NIC (Integrated Network Interface Controller) off and then booted off of USB. Was NOT an issue with any Linux distro just a quirk of the laptop.
 Am now running 13.10 daily and everything works. Also had to stick with EFI boot ON, Secure Boot disabled. Wouldn't boot off of any media or HDD when mode set to CSM.
Another users in same thread used Legacy mode and then NIC worked.
Toshiba P50 reset with pin hole on bottom
after tinkering, i found a little pinhole on the bottom of the laptop next to the RAM. used a paperclip to press it and now the BIOS is working again. 
[http://ubuntuforums.org/showthread.php?t=2237148](http://ubuntuforums.org/showthread.php?t=2237148)
Toshiba Satellite P75 intel hd 4600 needed acpi_osi=Linux acpi_backlight=vendor                               
[http://ubuntuforums.org/showthread.php?t=2161204](http://ubuntuforums.org/showthread.php?t=2161204)

---

### Post by ajgreeny on 2014-09-14
The first partition on a GPT formatted disk with UEFI enabled should be a fat32 partition to which you do not assign a mountpoint but leave the installer to do by itself. That will become the efi partition which your installation complained was missing. Mine is just 100MB in size, but I do.not have a dual boot system and do not know how much space windows efi bootloader files need; I don't think it is any more than ubuntu but may be wrong about that.

Next attempt to to install make a fat32 partition if one does not exist but do not do aything else at installation stage to that, just leave it alone, and you may find everything works OK.

---

### Post by fantab on 2014-09-14
In your Gparted screenshot /dev/sda has 'msftdata', an ESP has a 'boot' flag on it. edit: also don't use a 'label' on the partition.
Use Gparted to change the flag.

---

### Post by JDAIII on 2014-09-14
Well, thanks for the reply guys. 

@fantab: I changed the flag to boot, but instead of just changing it, I went ahead and blew away partitions and started again from scratch. 

Here is a screenshot of the new setup, only a link this time so that the last 3 people on the planet without high speed internet can view this page also.
New GParted settings: [http://i31.photobucket.com/albums/c355/cheshireccat/help/Screenshotfrom2014-09-14171423.png](http://i31.photobucket.com/albums/c355/cheshireccat/help/Screenshotfrom2014-09-14171423.png)

Those settings inside Ubuntu advanced partition tool. I went ahead and set the root and home mounting points and set them to format. I didn't touch the ESP and it looks like ubuntu recognized it since I added the boot flag. [http://i31.photobucket.com/albums/c355/cheshireccat/help/Screenshotfrom2014-09-14171710.png](http://i31.photobucket.com/albums/c355/cheshireccat/help/Screenshotfrom2014-09-14171710.png)

@oldfred: thanks for the links. You gave me a lot to try and I'm doing all that now. I'll try disabling the nic during install. I'll be trying to create a windows folder and figure that out. I'm also going to have to try to see if I can clear the MBR from the HDD from previous install of Win 8.1. Wouldn't imaging that being the problem with efi, but will look into it.

A few notes,
I checked the boot list of the bios and it's pretty simple and only lets me select a device not a specific mounted drive like sda1 or sda2. Just the physicall HDD or the cdrom or network.

 I just installed again, with the settings and I rebooted, got the same error, but I checked efibootmgr and I see that there is no listing for my ubuntu install. Now I mentioned this earlier, but nobody has touched on this. Could the issue be that somehow UEFI or the bios is not hooking the boot loader? I emailed a buddy and his reply was that I installed the OS so it's just a matter of getting the bios/UEFI to recognize where it is and putting that information in the bios. Well, there is nowhere in the bios to add that so that is not going to work, but it did get me thinking about the return I got from efibootmgr again. Previously it had a long string for 0000 ubuntu with all of the information about the drive and now there is nothing. Am I focussing on the wrong thing here?

ubuntu-gnome@ubuntu-gnome:~$ sudo efibootmgr BootCurrent -v
BootCurrent: 0003
Timeout: 2 seconds
BootOrder: 0000,0000,0003,2001,2002,2003
Boot0001* UEFI: Network Card     ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(7c0507ffcf1a,0)IPv4(0.0.0.0:0<->0.0.0.0:0,0, 0..BO
Boot0002* UEFI: Network Card     ACPI(a0341d0,0)PCI(1c,3)PCI(0,0)MAC(7c0507ffcf1a,0)030d3c000000000000000000000000000000000000000000000000000000000000000000000000000000004000000000000000000000000000000000..BO
Boot0003* UEFI: SanDisk U3 Cruzer Micro 8.02    ACPI(a0341d0,0)PCI(1d,0)USB(1,0)USB(4,0)HD(1,3f,1e48fc0,0217934c)..BO
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC


Last question, would disabling ACPI be a recommended test?

---

### Post by oldfred on 2014-09-14
There are mulitiple listings in the efi. Boot Current will just be the current. It seems there is a list for secure boot and a list for efi. 
What does this show?

       modprobe efivars
sudo efibootmgr -v

---

### Post by JDAIII on 2014-09-14
@oldfred: 
jd@jd-laptop:~$ modprobe efivars
jd@jd-laptop:~$ sudo efibootmgr -v
BootCurrent: 0001
Timeout: 2 seconds
BootOrder: 0001,0000,2001,2002,2003
Boot0001* ubuntu    HD(1,800,100000,e612f031-69e8-4777-966f-eff5aaa4d0b5)File(\EFI\ubuntu\shimx64.efi)
Boot2001* EFI USB Device    RC
Boot2002* EFI DVD/CDROM    RC
Boot2003* EFI Network    RC



OK, so you can all hate me now. Each time that I have done this, I have been setting a swap drive and configuring the partitions manaually. Well, I wanted to test something with the bios so I did set up the partitions in GParted, but didn't want to bother with the installer so I told it to delete and install on it's own and for shits and giggles, I selected lvm. Well, now it boots every time. rebooted and shutdown, restarted 6 times in the last few minutes. One thing that is funny is I have 16GB of RAM and it made my swap dirve 17GB. I like that because I hibernate when I leave the office since I will inevitably be working from home and it's just easier.

Thanks for all your help, and it sucks that I can't designate a specific partition for my /home, I think that I will live since I do have 500GB on this drive and another 3TB on my server at the office. If I didn't get this installed, myy boss was going to install RHEL on my laptop and I would have had to commit acts of self harm if I had to use RHEL at work and home.

---

### Post by oldfred on 2014-09-14
I do not use LVM, but one of its advantages is that it is easy to change partitions even while booted.

       LVM - Logical Volume Management.
Advantages/Disadvantages LVM Post #9
[http://ubuntuforums.org/showthread.php?t=1586328](http://ubuntuforums.org/showthread.php?t=1586328)
[https://wiki.ubuntu.com/Lvm](https://wiki.ubuntu.com/Lvm)
[https://help.ubuntu.com/community/UbuntuDesktopLVM](https://help.ubuntu.com/community/UbuntuDesktopLVM)
2014_02_22_Preparing Logical Volumes For Ubuntu Installations
[http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html](http://members.iinet.net/~herman546/2014_02_22_Preparing%20Logical%20Volumes%20For%20Ubuntu%20Installations.html)
Issues on very large 19TB LVM ext4 64 bit partition
[http://ubuntuforums.org/showthread.php?t=2213785](http://ubuntuforums.org/showthread.php?t=2213785)
lvm How-To info older:
[http://ubuntuforums.org/showthread.php?t=141900](http://ubuntuforums.org/showthread.php?t=141900)
[http://tldp.org/HOWTO/LVM-HOWTO/index.html](http://tldp.org/HOWTO/LVM-HOWTO/index.html)
[http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html](http://tldp.org/HOWTO/LVM-HOWTO/benefitsoflvmsmall.html)
sudo apt-get install lvm2
sudo vgchange -ay
LVM gui tool:
[http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/](http://www.howtogeek.com/127246/linux-sysadmin-how-to-manage-lvms-with-a-gui/)
sudo apt-get install system-config-lvm

This is for standard partitions, and now you have /mapper/... as your partitions but process would be the same.

 To move /home uses rsync- Be sure to use parameters to preserve ownership & permissions 
[https://help.ubuntu.com/community/Partitioning/Home/Moving](https://help.ubuntu.com/community/Partitioning/Home/Moving)

---

