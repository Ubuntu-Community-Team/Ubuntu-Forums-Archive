---
title: "UEFI install help please"
date: 2015-10-29
forum: Installation &amp; Upgrades
---

### Post by timmy8 on 2015-10-29
Now i have done a UEFI install of Arch distro, And Mint Linux with 2 or 3 OS's on the grub menu. But for Ubuntu a little strange on how this is done if anybody can help me out.

I installed Ubuntu 15.10 like this for UEFI like i was told by a friend who helped me out and was the right way to go. 

Just showing what i did on Arch and Mint for example then will get to the Ubuntu

 ```
  FAT32 /boot/efi
   ext4    /root
   swaplinux  if i choose too
```


Now for Ubuntu in gparted is how i do it but there is no ```
/boot/efi
``` or in the install. So i just left it as FAT32 for boot. Like this

```
FAT32  /boot  added the "/boot" with gparted and just left it since there was no /boot/efi in the commands
ext4    /root
swaplinux
```

So Ubuntu started up fine but didn't get a UEFI grub screen like the other distro's. I want to install the Ubuntu MATE 15.10 with it so since there is no /boot/efi when i do the install would i just leave the FAT32 and not change anything like i did before and just add the ext4 and install it. Because usually in the installer i have to specify the /boot/efi but Ubuntu does not have it so would i just use /boot when in UEFI like before. Also will now the grub come into play now since i installed another OS since there is none on the first UEFI install

Thank you please help and thank you in advance

---

### Post by Bucky Ball on 2015-10-29
*Thread moved to **Installation & Upgrades**.*

---

### Post by Dennis N on 2015-10-29
When you install Ubuntu, you don't specify the mount point for the EFI system partition like you do in Fedora or Arch. You just set the boot flag on the EFI system partition. That's all. Ubuntu will find it and automatically mount it at /boot/efi.

In your display, don't mount the ext4 partiton for the OS at /root - the correct designation is / 

There is a place to specify the boot loader location when you use the "Something Else" option for Installation method, but it is non-functional with UEFI installs. It appears to offer a choice, but the boot loader will install to the EFI system partition on the first disk (sda) regardless. So you can just leave it as is.

Linux Mint uses the same installer as Ubuntu, so the above applies to it as well. I have read that Linux Mint Debian Edition is an exception, but I'm not 100% sure about that.

---

### Post by oldfred on 2015-10-29
Your ESP - efi system partition is FAT32.
But in Linux a /boot partition has to be Linux formatted often ext2 or ext4, but for most desktops you do not need a /boot partition. LVM or LVM with encryption which are full drive installs do have a /boot partition and erase entire drive.

After install you will have a /EFI/ubuntu folder in the ESP. 
But from inside Ubuntu is it mounted with fstab as /boot/efi or seen then as /boot/efi/EFI/ubuntu.

As Dennis N says, the boot loader choice in Something Else install option does not work with UEFI.
I have installed a second install to sdb drive, even during install is says it is installing grub to sdb, but overwrote my ubuntu folder in my working install in sda's ESP.

---

### Post by timmy8 on 2015-10-29
> When you install Ubuntu, you don't specify the mount point for the EFI  system partition like you do in Fedora or Arch. You just set the boot  flag on the EFI system partition. That's all. Ubuntu will find it and  automatically mount it at /boot/efi.

In your display, don't mount the ext4 partiton for the OS at /root - the correct designation is / 

There is a place to specify the boot loader location when you use the  "Something Else" option for Installation method, but it is  non-functional with UEFI installs. It appears to offer a choice, but the  boot loader will install to the EFI system partition on the first disk  (sda) regardless. So you can just leave it as is.

Linux Mint uses the same installer as Ubuntu, so the above applies to it  as well. I have read that Linux Mint Debian Edition is an exception,  but I'm not 100% sure about that.


Thank you [**[COLOR=#000000]Dennis N[/COLOR]**]("http://ubuntuforums.org/member.php?u=321222"). Yes i know root is just / i was just letting people know that&#8217;s what it was that&#8217;s all.  There isn't a /boot/efi. flag in gparted or the installation so i just put the /boot flag on the FAT32 in gparted

---

### Post by timmy8 on 2015-10-29
> **oldfred said:**
> Your ESP - efi system partition is FAT32.
But in Linux a /boot partition has to be Linux formatted often ext2 or ext4, but for most desktops you do not need a /boot partition. LVM or LVM with encryption which are full drive installs do have a /boot partition and erase entire drive.

After install you will have a /EFI/ubuntu folder in the ESP. 
But from inside Ubuntu is it mounted with fstab as /boot/efi or seen then as /boot/efi/EFI/ubuntu.

As Dennis N says, the boot loader choice in Something Else install option does not work with UEFI.
I have installed a second install to sdb drive, even during install is says it is installing grub to sdb, but overwrote my ubuntu folder in my working install in sda's ESP.


FAT32 is right for efi right.  I don't have a /EFI/ubuntu folder I'm not sure what you mean here oldfred

Thanks for your help  				 				 					 						 	[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711")

---

### Post by timmy8 on 2015-10-29
OK so  i thought my install of Ubuntu was in UEFI. But it looks like its not. Ubuntu is in my boot menu when using UEFI so not sure what I&#8217;m doing wrong here

sudo efibootmgr
efibootmgr: EFI variables are not supported on this system.

---

### Post by oldfred on 2015-10-29
How you boot install media is how it then installs.
A flash drive should have two boot options in UEFI boot menu. 
One usually is something like UEFI:name of flash drive for UEFI boot and the other is just the name of the flash drive which would be for BIOS boot.

This shows the screens you see:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by timmy8 on 2015-10-29
> **oldfred said:**
> How you boot install media is how it then installs.
A flash drive should have two boot options in UEFI boot menu. 
One usually is something like UEFI:name of flash drive for UEFI boot and the other is just the name of the flash drive which would be for BIOS boot.

This shows the screens you see:
 Shows install with screen shots. Both BIOS purple accessibility screen & UEFI black grub menu screen
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)


That is an old guide and needs to be updated for newer versions of Ubuntu. I have looked at that doesn't help much.

I know which is UEFI on my USB that’s not a problem. Its installation for UEFI that is it didn't go to UEFI apparently. Although the Ubuntu was in my boot menu for UEFI but isn't according to this it should list something 

 sudo efibootmgr
efibootmgr: EFI variables are not supported on this system. 		


When i did the installation I set UEFI boot to FAT32 but put the /boot flag in gparted when i was partitioning. I think that was the problem. But there is no /boot/efi in gparted or the installer so what do i do

---

### Post by oldfred on 2015-10-29
You only partition with gparted. It only can assign the ESP when you add a boot flag to a FAT32 partition.
All install partitions choices & formats are set with the Ubuntu installer.

       UEFI install,windows 8 with Something Else screen shots
[URL="http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html"]http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html
[/URL]
 But do not create any partitions with Windows disk tools.
[http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html](http://www.dedoimedo.com/computers/dual-boot-windows-8-ubuntu.html)
[URL="https://help.ubuntu.com/community/DiskSpace"]https://help.ubuntu.com/community/DiskSpace
      [/URL]
 Something Else install, but prefer larger / of 20 or 25GB. Not showing Windows
[http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware]("http://www.tecmint.com/ubuntu-15-04-installation-on-uefi-firmware/")      [ ]("https://help.ubuntu.com/community/DiskSpace")  [ ]("http://www.everydaylinuxuser.com/2014/05/install-ubuntu-1404-alongside-windows.html")

---

### Post by Dennis N on 2015-10-30
> sudo efibootmgr
efibootmgr: EFI variables are not supported on this system.

Doesn't look good. That should give you some output, something like this:

Mine:
```
dmn@Zotac:~$ sudo efibootmgr
[sudo] password for dmn: 
BootCurrent: 0000
Timeout: 1 seconds
BootOrder: 0000,0002,0004,0005,0001,0003
Boot0000* Manjaro
Boot0001* Fedora
Boot0002* ubuntu
Boot0003* ubuntu
Boot0004* UEFI OS
Boot0005* UEFI OS
```

I really don't think you booted the flash drive in UEFI mode since your install apparently is not in UEFI mode. In any case, you should go back and try again. And you can't choose the mount point of the EFI system partition - Ubuntu does it for you automatically. All you get to choose is the partition to mount at /  

You can also look at /boot and see if it contains a folder named efi. If it is missing, you are not in UEFI mode.

Good Luck.

---

### Post by timmy8 on 2015-10-30
Those guides are useless** oldfred. **There[**[COLOR=#C61919][B]**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") is no /boot/efi so how do i make this work UEFI.  I added the EFI system and alls i got when rebooting was a black screen. SO please tell me how this is done in your own words. Thank you

---

### Post by timmy8 on 2015-10-30
I did click UEFI mode [**[COLOR=#000000]Dennis N[/COLOR]**]("http://ubuntuforums.org/member.php?u=321222") on my USB i know what UEFI is. I have been using it on manjaro and LInux mint with no problems. So not sure what I&#8217;m doing wrong

---

### Post by oldfred on 2015-10-30
Best to see details of your install to know what to repair.
You can run from live installer or any of your other installs if similar to Ubuntu.

       Post the link to the Create BootInfo summary report. Is part of Boot-Repair:
[https://help.ubuntu.com/community/Boot-Info](https://help.ubuntu.com/community/Boot-Info)

Also if black screen, are you booting but not getting grub menu? Escape will show grub menu, press if during UEFI boot screen.
What video card/chip?

---

### Post by timmy8 on 2015-10-30
OK Thank you  				 				 					 						 	[**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") sorry i doubted you :D  I think i got it now i have a efi file in boot and I&#8217;m on Ubuntu 15.10. Ubuntu starts without a grub screen it just loads in to Ubuntu. 

I tried seeing what this said and get this

efibootmgr
Timeout: 1 seconds
No BootOrder is set; firmware will attempt recovery. Which is odd to me its supposed to say something else right i should have a grub screen right.

This is only Ubuntu 15.10 on hard drive nothing else. I also have a video on its way so you guys here can see what i did and i booting in UEFI the right way

Thank you

---

### Post by timmy8 on 2015-10-30
Here's my video [**[COLOR=#C61919][B]oldfred**[/COLOR][/B]]("http://ubuntuforums.org/member.php?u=852711") on installing Ubuntu 15.10
[URL="https://www.youtube.com/watch?v=4lMnM5cNafg"]
https://www.youtube.com/watch?v=4lMnM5cNafg[/URL]


Sorry left this out : Boot Repair info

[http://paste.ubuntu.com/13016233/](http://paste.ubuntu.com/13016233/)

---

### Post by oldfred on 2015-10-30
Video a bit hard to watch. 

So is system ok now? You can change thread to solved.
I thought I saw both Asus & Asrock? Which is it?

If you only have Ubuntu, grub assumes you want to boot Ubuntu.
If you want grub menu, you have to press escape key during UEFI, or before grub fully loads.

I prefer smaller / (root) partition typically 25GB and use rest of drive as data. Or you could make it /home if not familiar with fstab and mounting and configuring a data partition.

Other Asrock threads.
  Asrock Z97 w/Core i7 5775C tried the "CPU OC Fixed Mode" of the ASRock UEFI setup.
[http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode](http://www.phoronix.com/scan.php?page=news_item&px=Core-i7-5775C-OC-Fixed-Mode)
ASRock Z97
[http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6](http://www.phoronix.com/forums/showthread.php?102720-ASRock-Z97-Extreme6)
ubuntu 14.04 on asrock Z87 extreme 4 or pro 4 
[http://ubuntuforums.org/showthread.php?t=2216079](http://ubuntuforums.org/showthread.php?t=2216079)
Some have issues with Asrock and its asmedia ports
UEFI, Windows on SSD, Ubuntu on HD ASRock Z77 Pro4 motherboard
[http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/](http://www.linuxbsdos.com/2012/10/10/dual-boot-windows-7-and-ubuntu-12-04-on-a-pc-with-uefi-board-ssd-and-hdd/)
ASRock UEFI bios + Ubuntu Server = operating system not found  Install to flash drive
[http://ubuntuforums.org/showthread.php?t=2153123](http://ubuntuforums.org/showthread.php?t=2153123)
AsRock Z77 Windows always reset to default
[https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order](https://wiki.archlinux.org/index.php/Unified_Extensible_Firmware_Interface#Windows_changes_boot_order)

---

### Post by timmy8 on 2015-10-30
Video a bit hard to watch. 

So is system ok now? You can change thread to solved.
I thought I saw both Asus & Asrock? Which is it?

If you only have Ubuntu, grub assumes you want to boot Ubuntu.
If you want grub menu, you have to press escape key during UEFI, or before grub fully loads.

I prefer smaller / (root) partition typically 25GB and use rest of drive as data. Or you could make it /home if not familiar with fstab and mounting and configuring a data partition.


> Video a bit hard to watch. 

So is system ok now? You can change thread to solved.
I thought I saw both Asus & Asrock? Which is it?


Watch the video again oldfred. Its not that hard to watch i ware glasses and is fine to me. Where do you see ASUS in the video there's nothing that says ASUS take another look my friend  



> If you want grub menu, you have to press escape key during UEFI, or before grub fully loads.  There is no grub menu on that i see if you look at the video so what do you mean?



> I prefer smaller / (root) partition typically 25GB and use rest of drive  as data. Or you could make it /home if not familiar with fstab and  mounting and configuring a data partition.



I don't use /home ever now i don't see the need home is in root.  Just root and swap. The way i do it is so i can install multiple OS's planing on installing Ubuntu mate 15.10 ISO. After i straightin this out with the grub menu. I'm just curious why you told me this way

---

### Post by oldfred on 2015-10-31
Especially if installing multiple systems, you want a data partition.
Then you can mount the data partition in all your installs, so you have the same data in all of them. 
When I still had Windows I started with a NTFS shared data partition then added a Linux data partition and when I shut Windows down, I only have my Linux shared data.
My /home inside / is about 2GB and it only is that large because of Picasa in .wine.

       Data can be shared without the possible conflicts of user settings being different in different versions. I only copy some settings from one install to the next, normally. But I have to separately back up /home and the /data partition. Also saves the error of reformating a /home partition accidentally. I never reformat my /data and just configure / for install.

   Splitting home directory discussion and details:
[http://ubuntuforums.org/showthread.php?t=1811198](http://ubuntuforums.org/showthread.php?t=1811198)
[http://ubuntuforums.org/showthread.php?t=1901437](http://ubuntuforums.org/showthread.php?t=1901437)
[http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata](http://ubuntuforums.org/showthread.php?t=1734233&highlight=%2Fdata)
User Morbius1 prefers bind over linking in post #4
[http://ubuntuforums.org/showthread.php?t=2192848](http://ubuntuforums.org/showthread.php?t=2192848)

I had to stop video to see what the Asus is, but it seems to be you SATA drive.

---

