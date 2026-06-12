---
title: "Black screen with blinking cursor after trying to install Lubuntu"
date: 2017-07-10
forum: Installation &amp; Upgrades
---

### Post by alexander.vk on 2017-07-10
Hi,

I'm not very experienced and don't understand many things but here's what happened

After having multiple issues with windows 10 (it got completely corrupted after trying to reset and didn't work) I decided to try lubuntu again. I've installed it on another computer before. The last time i installed it, I decided to keep windows xp on the old laptop and just have both operating systems.

This time, while trying out lubuntu I went to the installation app while just trying out lubuntu and during the process i was asked if i want to unmount some sort of partition. Can't remember the exact name but it was something like mmls maybe. I clicked on the X at the message to close it and proceeded with the installation. the installation screen changed and i was asked if i wanted to erase the disk and just install ubuntu on a clean disk (it was the first option) and i selected that one. After proceeding i get another error message telling me i need to reboot in order for it to work. (I guess maybe this means i didn't quite finish the installation) I rebooted and all i see is a black screen with a white blinking cursor. Also, after changing bios settings again, it turns out it did indeed wipe out windows 10. Just says no bootable drive found. After changing back, again, black screen white cursor. 

Fine, I didn't want windows 10. But why doesn't it boot from the card now? I unmounted the SDHC card onto which i loaded lubuntu earlier and did the same process - making a bootable drive using rufus to see if maybe the card got affected. 

It didn't change anything. Hope I haven't bricked my netbook.

Thanks for the help

---

### Post by oldfred on 2017-07-10
What brand/model system.
And more importantly what video card/chip.

Black screen often is a video driver issue and you may need nomodeset.
But if only Ubuntu will not normally see grub menu as system knows you just want to boot Ubuntu.

Did you install in UEFI or BIOS/CSM boot mode?

If UEFI you have to press escape (perhaps more than once) from UEFI screen. You may need also to cold boot or full shutdown, not a reboot. 
If BIOS you have to hold shift key from BIOS until grub menu appears.

       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters) 

Some systems also need other boot parameters.

---

### Post by alexander.vk on 2017-07-11
Acer Aspire R3-131T-C770
Intel Celeron N3050 1.60 GHz
The link below takes you to 4 images taken of the UEFI/BIOS (I'm not entirely sure which one it uses)
[http://www.mediafire.com/folder/1w8qb19b5nx9qdw,1kzillu53p89m11,2xaaraaca59sprh,be3xlsc3c35z46y/shared](http://www.mediafire.com/folder/1w8qb19b5nx9qdw,1kzillu53p89m11,2xaaraaca59sprh,be3xlsc3c35z46y/shared)

Unfortunately i don't know which video card this netbook uses. It was my girlfriend's netbook. When looking online for this model I only find one with a 500GB hard drive, but this one is only a 32gb SSD. If the hard drives are different, perhaps so are the other specs. I can't know for sure unfortunately which video card this one uses. The RAM on this is 4GB however.

Where it says "Boot Mode" I have a select choice between UEFI (which lead me to windows 10 before but now no bootable drives found) and Legacy which is what i used to boot Lubuntu before. P.S. The EMMC 32GHBG4e in the picture is the SDHC card with lubuntu.

I've tried pressing escape, long pressing and holding it during boot to no avail.
Also tried the same with the shift key.

Tried both options during boot and inside the BIOS/UEFI. Nothing seems to make a difference. I can't get to the grub menu unfortunately.

---

### Post by oldfred on 2017-07-11
If you install in UEFI mode, Acer has a unique requirement of setting a UEFI supervisory password and enabling "trust" on the Ubuntu/grub .efi boot files from inside UEFI.

Some threads also mention downgrading UEFI (missing settings), newer ones say upgrade to newest UEFI works. So make sure you have newest UEFI from Acer for your model.

 Acer Aspire R5-417T
[https://ubuntuforums.org/showthread.php?t=2346815](https://ubuntuforums.org/showthread.php?t=2346815)
Acer Trust Settings - details:
[https://ubuntuforums.org/showthread.php?t=2358003](https://ubuntuforums.org/showthread.php?t=2358003)
[https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757](https://ubuntuforums.org/showthread.php?t=2291335&p=13341757#post13341757)
[https://ubuntuforums.org/showthread.php?t=2342323](https://ubuntuforums.org/showthread.php?t=2342323)
[http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742](http://ubuntuforums.org/showthread.php?t=2297947&p=13369742#post13369742)
Acer Cloudbook shows screen for selecting trust
[http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431](http://bernaerts.dyndns.org/linux/74-ubuntu/340-ubuntu-install-acer-aspire-cloudbook-431)
[URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392
[/URL]
 Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162) 

[       ]("http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392")
 Acer Aspire E15 will not dual boot, many details Trust settings in step 35
[http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot](http://askubuntu.com/questions/627416/acer-aspire-e15-will-not-dual-boot) 
    [URL="http://community.acer.com/t5/Predator-Laptops/Dual-Boot-Ubuntu-Win10-Step-by-step-guide/m-p/430392#U430392"]
[/URL]

---

### Post by alexander.vk on 2017-07-12
Thank you so much for the help 

I've set the supervisor password. Downloaded a different version of lubuntu (64bit) and then in uefi settings I've turned on secure boot and added all the efis from lubuntu on the SDHC card as safe exceptions and then it worked. 
I was met with the grub menu and tried the OS before installing. Seems to work just fine. Then however i try to install and all I want is lubuntu, single boot. However I'm met with 2 messages after choosing to erase disk. 
First asks me whether i want to force into UEFI and i click yes. The choice is either that or go back. 
Another is saying how the partitions on the SD Card are going to be changed. I'm confused. I don't want to install it on the SD Card. Why is it saying that? 

Again the choice is only to go back or continue. I have to say, I've done a lot of reading about partitions and swap areas and i still don't understand. Why can't it just install on the hard drive as normal? 

After installation I'm prompted to restart and so i do. After restart instead of seeing a welcome screen i see the same grub menu as before. Try without installation or install. It's like i haven't installed anything at all. 

I take it something is wrong with the drive or partitions so i used GParted and lxterminal to see how many i have. Thought I'd just see 2 or 3 but the result is on the picture. 
Back to the installation, in my old notebook i pressed "something else' and partitioned some space for windows xp and some for lubuntu. There weren't any problems. This time on this newer netbook it tells me there's no root device or something. No matter what i select its the same result. 
I'm clueless at this point.

[https://www.mediafire.com/folder/w0sgsb6m98ld6/Lubuntu_install]("https://www.mediafire.com/folder/w0sgsb6m98ld6/Lubuntu_install")

---

### Post by oldfred on 2017-07-12
Do not see partitions:
post this:
sudo parted -l

---

### Post by alexander.vk on 2017-07-12
Model: Generic SD/MMC Storage Card (sd/mmc)
Disk /dev/mmcblk0rpmb: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: Unknown (unknown)
Disk /dev/zram1: 991MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  991MB  991MB  linux-swap(v1)


Model: SD SD32G (sd/mmc)
Disk /dev/mmcblk1: 31.9GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system  Name                  Flags
 1      1049kB  31.9GB  31.9GB  fat32        Microsoft Basic Data  msftdata


Error: /dev/mmcblk0boot0: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot0: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: Unknown (unknown)
Disk /dev/zram0: 991MB
Sector size (logical/physical): 4096B/4096B
Partition Table: loop
Disk Flags: 

Number  Start  End    Size   File system     Flags
 1      0.00B  991MB  991MB  linux-swap(v1)


Error: /dev/mmcblk0boot1: unrecognised disk label
Model: Generic SD/MMC Storage Card (sd/mmc)                               
Disk /dev/mmcblk0boot1: 4194kB
Sector size (logical/physical): 512B/512B
Partition Table: unknown
Disk Flags: 

Model: MMC HBG4e (sd/mmc)
Disk /dev/mmcblk0: 31.3GB
Sector size (logical/physical): 512B/512B
Partition Table: gpt
Disk Flags: 

Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 2      538MB   27.2GB  26.6GB  ext4
 3      27.2GB  31.3GB  4111MB  linux-swap(v1)

---

### Post by oldfred on 2017-07-12
Does not look like you have hard drive, but just MMC cards. One 4GB and one 32GB as system drive. This seems to be common with these very lightweight or small systems.

---

### Post by alexander.vk on 2017-07-12
You mean i have 2 memory cards acting as my hard drive?

Interesting. Still, any idea why lubuntu won't install on any of them?

---

### Post by oldfred on 2017-07-12
These partitions are typical of your install in UEFI mode:

```
Number  Start   End     Size    File system     Name                  Flags
 1      1049kB  538MB   537MB   fat32           EFI System Partition  boot, esp
 2      538MB   27.2GB  26.6GB  ext4
 3      27.2GB  31.3GB  4111MB  linux-swap(v1)
```

Did you set UEFI supervisory password and enable trust as posted in many threads for every Acer.

---

### Post by alexander.vk on 2017-07-12
Yes yes and yes. Only after the supervisory password and trust enabled did i manage to get the grub menu in the first place. Before that it was just black screen and blinking cursor. 

P. S. I really appreciate all the help you're giving me
Thank you

---

### Post by oldfred on 2017-07-12
So is it fully booting?
Some systems need additional boot parameters, depending on versions of chips & kernel.

       Acer Aspire ES (15 ES1-523-844Y)  works with some settings
[https://ubuntuforums.org/showthread.php?t=2364018](https://ubuntuforums.org/showthread.php?t=2364018)
Acer Aspire ES1-132 cannot able to install kubuntu UEFI missing options, rEFInd
[https://ubuntuforums.org/showthread.php?t=2348269](https://ubuntuforums.org/showthread.php?t=2348269) 

 Boot Parameter required
[http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10](http://askubuntu.com/questions/695805/acer-aspire-es1-311-freezes-regularly-on-ubuntu-gnome-15-10)
Acer E3-112-C0MQ - Bay Trail Issue Boot Parameter required
[http://ubuntuforums.org/showthread.php?t=2326162](http://ubuntuforums.org/showthread.php?t=2326162) 

Some of issues with older versions of Ubuntu have been fixed in newer version. But you can boot and in grub edit to add boot parameters similar to these instructions for adding nomodeset which is usually required with nVidia.
      
 At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)

---

### Post by alexander.vk on 2017-07-18
Hi!

I've finally fixed the issue. Not realising this at first but the issue was that now that lubuntu got installed on the emmc, I needed to manually go into UEFI and add all the EFIs from the emmc as my trusted sources.

What I did to solve the problem:
Reset UEFI settings
added all the EFIs as trusted sources from the bootable SD Card
Installed lubuntu selecting the clean erased disk option
Added all the EFIs from the inbuilt emmc card 

And it worked!

Been using lubuntu for a few days now just to make sure there are no more issues to mention.

A big thank you oldfred for all the help that you have given me. You rock.

---

