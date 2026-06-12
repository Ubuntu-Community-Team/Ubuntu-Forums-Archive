---
title: "Dual Boot Installation on second SSD"
date: 2017-12-07
forum: Installation &amp; Upgrades
---

### Post by poor-yorick on 2017-12-07
Hello,

I'm trying to install Ubuntu 16.04 alongside Windows 10 Pro. I followed this guide: [https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/](https://itsfoss.com/install-ubuntu-1404-dual-boot-mode-windows-8-81-uefi/) 

I have two SSDs, a 120 GB in SATA 0 on the MB with the Windows installation, and a 60 GB in SATA 2 on the MB that used to have Windows installed. I want to install Ubuntu on the 60 GB SSD.


[LIST=1]
[*]Make a backup of Windows
[*]Create a bootable USB ([https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0](https://tutorials.ubuntu.com/tutorial/tutorial-create-a-usb-stick-on-windows#0))
[*]Delete volumes on second SSD so it is 100% unallocated space (see photo 1)
[*]Disable fast boot in Windows
[*]Disable secure boot in BIOS
[*]Shutdown, insert USB, F9 in BIOS, select boot from the USB
[/LIST]

I got the purple screen with the 5 dots loading, but after ~30 sec it went to a black screen and started printing errors about SQUASHFS and blk_update_request (see photo 2). Can someone help show me where I went wrong and what I can do? Thank you!

Photo 1
[IMG]https://drive.google.com/file/d/14wJ_oHnfy6JslpBsEd3g9kkHnuduacftNQ/view?usp=sharing[/IMG]
[https://drive.google.com/file/d/14wJ_oHnfy6JslpBsEd3g9kkHnuduacftNQ/view?usp=sharing](https://drive.google.com/file/d/14wJ_oHnfy6JslpBsEd3g9kkHnuduacftNQ/view?usp=sharing) 

Photo 2 (sorry it's a little blurry)
[https://drive.google.com/file/d/1Gj_sk6Q10AghQSBcS8VM1YUoyAY3L5B26A/view?usp=sharing](https://drive.google.com/file/d/1Gj_sk6Q10AghQSBcS8VM1YUoyAY3L5B26A/view?usp=sharing)
[IMG]https://drive.google.com/file/d/1Gj_sk6Q10AghQSBcS8VM1YUoyAY3L5B26A/view?usp=sharing[/IMG]

---

### Post by oldfred on 2017-12-07
What brand/model System?
What video card/chip?

Your Windows drive looks like the standard partitions for a BIOS/MBR install, but shows an efi (ESP - efi system partition) which is for UEFI/gpt partitioning.
However you have installed Windows BIOS or UEFI, is the preferred way to install Ubuntu.
But if new UEFI hardware generally both systems should be UEFI installs.

Post this:
sudo parted -l

Windows only installs in BIOS boot mode to MBR(msdos) and only in UEFI boot mode to gpt (GUID) partitioned drives.

 BIOS & UEFI Windows partitions, note system has totally different format  & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx)
[https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations](https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations)

---

### Post by poor-yorick on 2017-12-07
> [COLOR=#000000]oldfred[/COLOR]
[COLOR=#000000][INDENT]**Re: Dual Boot Installation on second SSD**
What brand/model System?
What video card/chip?

Your Windows drive looks like the standard partitions for a BIOS/MBR install, but shows an efi (ESP - efi system partition) which is for UEFI/gpt partitioning.
However you have installed Windows BIOS or UEFI, is the preferred way to install Ubuntu.
But if new UEFI hardware generally both systems should be UEFI installs.

Post this:
sudo parted -l

Windows only installs in BIOS boot mode to MBR(msdos) and only in UEFI boot mode to gpt (GUID) partitioned drives.

BIOS & UEFI Windows partitions, note system has totally different format & meaning between BIOS & UEFI
[https://msdn.microsoft.com/en-us/lib...=vs.85%29.aspx]("https://msdn.microsoft.com/en-us/library/windows/hardware/dn898504%28v=vs.85%29.aspx")
[https://msdn.microsoft.com/en-us/lib...Configurations]("https://msdn.microsoft.com/en-us/library/windows/hardware/dn898510%28v=vs.85%29.aspx#RecommendedPartitionConfigurations")[/INDENT]
[/COLOR]


What brand/model system
[LIST]
[*]It's for Ethereum mining
[*]Motherboard: BioStar TB250-BTC+
[/LIST]
What video card
[LIST]
[*]6 Sapphire Radeon RX470 4GB Samsung Memory Mining Edition (no display outputs)
[*]Connection to monitor is using IGFX from Intel Celeron G3900 LGA 1151
[/LIST]

I will research the two microsoft links. I've seen BIOS/UEFI and MBR mentioned before but am not familiar with them. Same with disk partitions and formatting - mildly familiar but not great. I am comfortable with Ubuntu/command line use, I have Ubuntu in a virtual machine on my main laptop, but that installation went so smoothly, so I was surprised with these issues. Since this is all new hardware (Aug/Sep 2017), I thought it would be compatible.

Can you explain where to run "sudo parted -l"? I want to make sure I don't overwrite the drive that Windows is on.

---

### Post by yancek on 2017-12-07
> 
Can you explain where to run "sudo parted -l"? I want to make sure I don't overwrite the drive that Windows is on. 		

You can't in your current situation.  You would need to be able to boot to the Ubuntu Desktop from the DVD or flash drive you are using to install Ubuntu and run it in a terminal.  Did you do an md5 checksum to verify the download of the Ubuntu iso?  As indicated above, your image from windows shows you have an EFI partition so you would need to also install Ubuntu EFI which is explained at the link below, the official Ubuntu documentation on the subject.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by poor-yorick on 2017-12-08
Thank you oldfred and yancek for all that info! I'm not in a rush so I'm going to take some time to read through it and understand. I want to understand it, not put on a band-aid. I will update here if this solves it.

I did not do an md5 checksum on the ISO and deleted the file from my Windows machine. I may format the USB and download/checksum a new ISO.

Thank you!

---

### Post by oldfred on 2017-12-08
Do not know if any of these are similar enough or not. Most issues are by brand and then whether Intel or AMD, so may apply.

 Gigabyte Z170 Nvidia 970 16.04   UEFI Settings required                         
[http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04)
[https://ubuntuforums.org/showthread.php?t=2341704](https://ubuntuforums.org/showthread.php?t=2341704)
Gigabyte H170
[http://ubuntuforums.org/showthread.php?t=2312650](http://ubuntuforums.org/showthread.php?t=2312650) 
      
 Gigabyte P34G Ultrablade turn off 3d graphics
[http://ubuntuforums.org/showthread.php?t=2198177](http://ubuntuforums.org/showthread.php?t=2198177)
[http://overtond.blogspot.fr/2013/10/ubuntu-on-gigabyte-p34g-ultrablade.html](http://overtond.blogspot.fr/2013/10/ubuntu-on-gigabyte-p34g-ultrablade.html)

If not familar with UEFI, see link in my signature. It is a lot but has simple steps to install, and then links to more details if you do not understand or need more info on a step.

---

### Post by poor-yorick on 2017-12-10
Success! Thank you everyone for your help!

---

### Post by KillerKelvUK on 2017-12-28
Hey @poor-yorick, I'm interested to know what the problem was and how you solved it.  Looking to get the same mobo for eth mining so any tips would be appreciated?

---

### Post by poor-yorick on 2017-12-28
Hi KillerKelvUK,

I'll do my best, it was a few days of tinkering so I can't promise step-by-step instructions, but can put together the resources I used.

In Windows, go to Disk Management and set aside enough space for Ubuntu. If you only have one SSD/HDD you will need to shrink the Windows volume and format as GPT. If you will install Ubuntu on a second disk, delete all the partitions so that it's unallocated space, formated as GPT ([https://drive.google.com/file/d/1DqXy4uTGKnvJInJTl2wD2S9ZxtIE73uz3w/view?usp=sharing](https://drive.google.com/file/d/1DqXy4uTGKnvJInJTl2wD2S9ZxtIE73uz3w/view?usp=sharing))

Still in Windows, disable Fast Startup. ([http://www.rodsbooks.com/linux-uefi/](http://www.rodsbooks.com/linux-uefi/))

In BIOS, go to the Boot menu and disable CSM Support and Fast Boot.

Create a UEFI bootable USB stick. ([https://www.vanstechelman.eu/content/creating-an-uefi-bootable-linux-usb-stick](https://www.vanstechelman.eu/content/creating-an-uefi-bootable-linux-usb-stick)) 

I followed these two sites for the installation. Make sure to choose "Something Else" instead of "Erase disk and install Ubuntu," even if you have a separate disk for it.
1. Has more info on what to do in Disk Management in Windows, but does not allocate swap space for Ubuntu. [https://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/](https://www.tecmint.com/install-ubuntu-16-04-alongside-with-windows-10-or-8-in-dual-boot/) 
2. I followed this for the Ubuntu drive partitioning. [https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/](https://itsfoss.com/install-ubuntu-dual-boot-mode-windows/) 

Other resources I found useful:
[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI) 
[https://ubuntuforums.org/showthread.php?t=2147295](https://ubuntuforums.org/showthread.php?t=2147295) 

Good luck getting started!

---

### Post by KillerKelvUK on 2017-12-28
Thanks :)

In your OP the 2nd screenshot with the SQUASHFS errors do you think was down to bad installation media i.e. your bootable USB stick?  

Did you have to change the Biostar boards UEFI about or update the UEFI altogether?  Heard rumours about these boards being buggy and Biostar was working on a new UEFI to resolve but haven't gotten to the bottom of this yet?

---

### Post by poor-yorick on 2017-12-28
I had done an MD5 checksum so the ISO wasn't bad, but I did use an MBR image. Changing the USB to GPT, formatting the second disk as GPT, and disabling CSM Support in the Biostar BIOS were the three major changes that got me there I think.

---

### Post by KillerKelvUK on 2017-12-29
Perfect, thanks for the details!

---

