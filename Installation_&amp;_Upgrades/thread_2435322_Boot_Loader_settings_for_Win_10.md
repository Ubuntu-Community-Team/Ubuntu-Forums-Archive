---
title: "Boot Loader settings for Win 10"
date: 2020-01-19
forum: Installation &amp; Upgrades
---

### Post by hennmann on 2020-01-19
Hi again everybody!
At the present time I have Ubuntu 18.04 and Win 7 on my MSI 970A SLI Krait edition and both are working very well I might add!
A number of months ago I attempted to install both Win 10 and Ubuntu on separate partitions as per the same procedure I followed with my installation of Win 7 and Ubuntu.
The boot info I found is slightly different on Win 10 VS Win 7 and as a result I ended up with an installation where i couldn't boot Win 10 and resorted to going back to the now unsupported Win 7.

Can somebody post a link to where I can get detailed info on setting this up? I strongly suspect the location or description of the Win 10 MBR is not properly installed on my boot loader.

---

### Post by yancek on 2020-01-19
The Ubuntu documentation on dual booting with windows 10 is at the link below.  You need to check to see if your drive is GPT as if it is, you need windows and Ubuntu installed in UEFI mode.

[https://help.ubuntu.com/community/UEFI](https://help.ubuntu.com/community/UEFI)

---

### Post by oldfred on 2020-01-19
If you still have Windows 7, but installed Windows 10, your Windows 10 boot files are probably in the Windows 7 partition and BCD was updated to have both Windows 7 & Windows 10.
With Windows 10 you also have to turn fast start up off. Otherwise grub will not see it nor boot it.
But with Windows boot files in only one partition, grub will only find one Windows to boot. If BIOS, and both installs are in primary partitions, you can add Windows boot files to both installs. One one will boot as Windows uses boot flag, but grub can find both as it only looks for Windows boot files.

May be best to see details, use ppa version with your live installer (2nd option) or any working install,  not older Boot-Repair ISO:
Please copy & paste link to the Boot-info summary report ( do not post report), the auto fix sometimes can create more issues.
 [https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by hennmann on 2020-01-20
Before anybody responded I swapped my SSD with a blank one and did a fresh install of Win 10 and this meger little Atom N455 is handling Win 10 quite well for a small netbook. I decided to start over with everything with things untouched on my SSD I swapped out. 
Right now as it stands I have three formatted partitions, actually 4 as one is a 500 meg system partition but otherwise I have this 1TB SSD partitioned into 3 equal amounts. 
To get things moving along I partitioned all of them with Win 10 and it gave me no other options other than NTFS! Anyway I can format them later using Ubuntu keeping the third as a shared formatted to Fat. 
One thing I do remember quite a while ago is the description for the Win7 bootloader and possibly location was different than in Windows 10. This is perhaps what led to problems and back then I noticed others were having problems mainly with Win 10 install as well. 
On my Desktop PC Win7 Pro is running with Ubuntu 18.04 with a very good operating boot loader. That one will be perhaps an upgrade instead of a clean install on this Netbook. 
This is yet another experiment flogging this gutless Acer Aspire One AO533 to see if the latest Windows 10 version 1903 is better than the 1570 I believe it was back in 2015 to see if it performs better with the latest updates 1903. When it first came out back then I gave it a try but yanked it out and re installed Windows 7 along with Ubuntu. 
Thanks for the links and I will do some reading and it will be safe to say fresh install for both which will make things easier. 
Ubuntu ran quite well albeit a bit slow but very well because this is also a 64 bit netbook even though it was never advertised as such. 
When I get things fully installed and updated in the USB will go and we will see what appears during the boot loader settings and I will let you know what is going on if I run into problems.

---

### Post by oldfred on 2020-01-20
Only use Linux tools for Linux.
Windows cannot create Linux partitions.

Also best not to use FAT32 for any larger partition. It is used for a small ESP for  UEFI boot systems.
FAT32 cannot store a file over 4GB and has no journal so chkdsk can take forever or not work. If you need Windows & Ubuntu to share use NTFS, but with Windows 10, you must have fast start up which is just hibernation off.

If drive is only going to be Linux consider gpt partitioning. Windows requires MBR for BIOS boot, but Ubuntu can boot in either BIOS or UEFI from the newer gpt if you have a 1MB unformatted partition with bios_grub flag for BIOS boot or an ESP - efi system partition for UEFI boot. I suggest both partitions as neither is large if drive may ever be moved to an UEFI system. That saves total reformat, but would require reinstall of grub if changing boot mode.

GPT Advantages (older 2010 but still valid)  see post#2 by srs5694:
[http://ubuntuforums.org/showthread.php?t=1457901](http://ubuntuforums.org/showthread.php?t=1457901)
[https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT](https://wiki.archlinux.org/index.php/GUID_Partition_Table#Advantages_of_GPT)
[http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface](http://en.wikipedia.org/wiki/Unified_Extensible_Firmware_Interface)
[http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr](http://askubuntu.com/questions/629470/gpt-vs-mbr-why-not-mbr)

---

### Post by hennmann on 2020-01-21
Here is the progress of my installation:

I determined whether or not I have BIOS/Legacy or UEFI and BIOS is what I have being on a tail end device.

Given this I decided to download the latest and using Rufus as usual made a USB installer.

When installing I selected "Something else" and chose Ext4 with the nag no root device selected so I set my partition as Root and it was happy.
For my boot loader it gave me the option of my Win10 partition and also my hard drive ID as well so I used that with the assumption this was in case I'm using multiple hard drives?? Whatever the reason it works and I tested booting both and all is well.

Surprisingly it runs a bit slower on this Acer Aspire One AO533 with that crappy little Atom N455 than Windows 10 Pro 64 WTH? One would think it should be faster than a resource hungry Win10 with most things running that I haven't disabled yet as a way of speeding up the system. The only thing I did was select "set windows up for best performance" which is an option on laptop/netbooks for extending battery life if not plugged in. Is this option available for Ubuntu?? Anyway as for the Atom many on the Overclocker's forum ask if they can be overclocked and the response by many was do not due to cooling concerns and one member summed it up quite well by saying "A polished turd is still a turd" 

Now a bit of constructive criticism on the provided links:
First of all for installation the question or suggestion in the instructions should be "Do you have legacy BIOS or UEFI?"  If you have Legacy BIOS go here (hyperlink) If you have UEFI go here(hyperlink)
The reason why I feel this way is the provided links have quite a jumble of information all mixed together creating needless confusion for those who are boldly going where no one has gone before.
You basically have to wade through both one or the other to get to where your going.

I did a google to get info on how to determine that included using the Windows Key&R and type msinfo32 or root around in the BIOS to determine which some might know how to or in my case my BIOS doesn't have any indication or the option to select either/or.

Other than following the links I did a search of Ext3 vs Ext4 and decided to set it to Ext4 and let er rip.

In some ways I'm more used to installation of the early 2000's where during installation you had to entirely set up a host of partitions before you could actually install including a separate / and swap partition along with home, tmp, var, etc.
One thing is for certain some of my hardware is from the early 2000's such as my HP laptop with such a small amount of RAM that even with the smallest or lightest flavors of Puppy Linux it was impossible to run "Live" due to the limits of RAM in megs instead of Gigs so I literally had to set up and enable a swap partition to enable it to run properly.
Sad to say my old CD of Mandrake 7.0 ran extremely well and was easier to install!

Otherwise for this installation of Ubuntu would I be better off starting over and manually setting up partitions as per the good ol days with a swap double the size of my 2GB of RAM? After all I'm possibly limited to 2GB and the only way of determining this is to rip this netbook apart and poking in a 4GB module to see if it will even work.
Also like the other methods of having a smaller dedicated /Root partition, updates are perhaps easier because of additional partitions where things can be saved.
This is how I always set up my Windows with a dedicated hard drive or smaller partition for windows and everything else in different partitions or hard drives in case Windows craps the bed and needs to be reinstalled with everything left intact including drivers and utilities.

---

### Post by oldfred on 2020-01-21
You manual says, this, so it is UEFI:
> CLICK BIOS is a revolutionary UEFI interface
Almost all systems are UEFI since 2012 as Microsoft has required Windows to be installed in UEFI/gpt boot mode. Users still can install in BIOS/Legacy, but that was more for large users who wanted to keep same configuration (Windows 7 typically) but still be able to use newer hardware.

There are a lot of posts if you want to research a bit on slow boot. I do not like snaps, so that is first thing I remove.
Slow Boot --------------------------------
[https://ubuntuforums.org/showthread.php?t=2417453](https://ubuntuforums.org/showthread.php?t=2417453) & 
[https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392](https://ubuntuforums.org/showthread.php?t=2417453&p=13857392#post13857392) & 
[https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html](https://www.dedoimedo.com/computers/ubuntu-beaver-slow-boot.html)
[https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything](https://askubuntu.com/questions/1187117/slow-boot-boot-19-10-tried-almost-everything)

Since MSI and 970, some issues are common to many similar models of MSI and most vendors versions of the 970 chipset.
turns out the IOMMU needs to be enabled in the BIOS. This problems seems to be exclusive to AMD  boards.
Gigabyte Z170 Nvidia 970 16.04   UEFI Settings required                         
[http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04](http://askubuntu.com/questions/792012/nvidia-geforce-gtx970-problem-ubuntu-16-04) & 
[https://ubuntuforums.org/showthread.php?t=2341704](https://ubuntuforums.org/showthread.php?t=2341704)
GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)

MSI UEFI bug work around A75MA-G55 UEFI boot entries disappear 
[http://forum-en.msi.com/index.php?topic=153411.0](http://forum-en.msi.com/index.php?topic=153411.0)
[http://forum-en.msi.com/](http://forum-en.msi.com/)
[https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524](https://bugs.launchpad.net/ubuntu/+source/linux/+bug/1129524)

---

### Post by hennmann on 2020-01-21
Yes my MSI 970A SLI is UEFI but this netbook is 2009/2010 and is Legacy BIOS.
Some of my motherboards such as a Gigabyte AM3 have the option to toggle BIOS or UEFI as well.
After my installation my concern was the size of swap partition and it appears to be 2gb the size of my installed RAM.
One thing I found was if there is very little RAM making a large swap did wonders!
The versions of Lite Linux I tried were simply hopeless if they only allowed the user to install in live and I'm refering to my HP that came out with Windows 2000 with 512 megs of RAM. Live would be perpetually stalled and no direct option of installation was possible making it a step backwards. One older low end hardware I found live gives terrible results compared to just installing it with a larger than installed ram size for the swap.

In my case of having an Atom N455 and 2gb of RAM, would increasing my swap to 3 or 4gb be of any help?

---

### Post by oldfred on 2020-01-21
I missed that you were not installing to the MSI system again.

Better to install Lubuntu or other lightweight version to a lightweight tablet type system.
Light weight flavors
Lubuntu, xubuntu, Ubuntu MATE, Budgie
I typically install gnome-panel or flashback which is like the old gnome2 with top & bottom panels. And is another lightweight configuration.

---

