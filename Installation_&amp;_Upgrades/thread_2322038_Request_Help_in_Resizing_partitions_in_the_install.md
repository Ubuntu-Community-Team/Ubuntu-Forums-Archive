---
title: "Request Help in Resizing partitions in the installation of Linux Distro Lubantu 15.10"
date: 2016-04-25
forum: Installation &amp; Upgrades
---

### Post by paul258 on 2016-04-25
Hello, I am new to Linux. I have a Toshiba Satellite M45-S265  with windows Vista home 32 bit installed. I made a live boot CD with Linux Distro (Lubantu 15.10 i386.iso). I booted into Linux and it asked to install in the "SOMETHING ELSE" section and to resize my partitions. So that I can install other Linux distros and keep my files .I don't know how to resize the partitions without keeping windows Vista and what partitions to resize. Can anyone give me some assistance. I would appreciate any help given to me . Thank You in advance.

---

### Post by oldfred on 2016-04-25
Boot into Ubuntu live installer and post this:
  sudo parted /dev/sda unit s print 

What are specs of your system? CPU, RAM & Video
Older lightweight systems need good video cards to run Ubuntu with Unity. They either need the gnome-panel or fallback which is menus or Lubuntu or Xubuntu which are lighter weight distributions.

---

### Post by paul258 on 2016-04-26
```
[FONT=&amp]**THE SPECS**

[TABLE="width: 629"]
[TR]
[TH="colspan: 2"]Pricing[/TH]
[/TR]
[TR]
[TD]**Part Number**[/TD]
[TD]PSM40U-07V001[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Battery Information[/TH]
[/TR]
[TR]
[TD]**Battery Chemistry**[/TD]
[TD]Lithium Ion (Li-Ion)[/TD]
[/TR]
[TR]
[TD]**Battery Capacity**[/TD]
[TD]4300 mAh[/TD]
[/TR]
[TR]
[TD]**Maximum Battery Run Time**[/TD]
[TD]2.70 Hour[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Interfaces/Ports[/TH]
[/TR]
[TR]
[TD]**FireWire/i.LINK**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Total Number of USB Ports**[/TD]
[TD]3[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Display & Graphics[/TH]
[/TR]
[TR]
[TD]**Screen Size**[/TD]
[TD]15.40 "[/TD]
[/TR]
[TR]
[TD]**Display Screen Type**[/TD]
[TD]Active Matrix TFT Color LCD[/TD]
[/TR]
[TR]
[TD]**Aspect Ratio**[/TD]
[TD]16:10[/TD]
[/TR]
[TR]
[TD]**Screen Mode**[/TD]
[TD]WXGA[/TD]
[/TR]
[TR]
[TD]**Screen Resolution**[/TD]
[TD]1280 x 800[/TD]
[/TR]
[TR]
[TD]**Graphics Controller Manufacturer**[/TD]
[TD]Intel[/TD]
[/TR]
[TR]
[TD]**Graphics Controller Model**[/TD]
[TD]Graphics Media Accelerator 900[/TD]
[/TR]
[TR]
[TD]**Graphics Memory Capacity**[/TD]
[TD]Up to 128 MB[/TD]
[/TR]
[TR]
[TD]**Graphics Memory Accessibility**[/TD]
[TD]Shared[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Storage[/TH]
[/TR]
[TR]
[TD]**Storage Size**[/TD]
[TD]100 GB[/TD]
[/TR]
[TR]
[TD]**Hard Drive Interface**[/TD]
[TD]Ultra ATA/100 (ATA-6)[/TD]
[/TR]
[TR]
[TD]**Hard Drive RPM**[/TD]
[TD]5400[/TD]
[/TR]
[TR]
[TD]**Optical Drive Type**[/TD]
[TD]DVD-Writer[/TD]
[/TR]
[TR]
[TH="colspan: 2"]General Information[/TH]
[/TR]
[TR]
[TD]**Manufacturer**[/TD]
[TD]Toshiba[/TD]
[/TR]
[TR]
[TD]**UPC Code**[/TD]
[TD]43211503[/TD]
[/TR]
[TR]
[TD]**Manufacturer Part Number**[/TD]
[TD]PSM40U-07V001[/TD]
[/TR]
[TR]
[TD]**Brand Name**[/TD]
[TD]Toshiba[/TD]
[/TR]
[TR]
[TD]**Product Name**[/TD]
[TD]Satellite M45-S265 Notebook[/TD]
[/TR]
[TR]
[TD]**Marketing Information**[/TD]
[TD]the Satellite M45-S265 is highly mobile, outperforming many desktops with technology designed specifically for mobile PCs. It includes a 15.4" wide-screen TruBrite display to make images brighter and more vivid. Enjoy notebook-optimized Intel Centrino Mobile Technology, Microsoft Windows XP Operating System, 100GB hard drive, and integrated high speed wireless LAN, all in one sleek chassis. The DVD-SuperMulti optical drive reads and writes to the most popular CD and DVD formats, making it perfect for movie making, or file archiving and exchange.[/TD]
[/TR]
[TR]
[TD]**Product Model**[/TD]
[TD]M45-S265[/TD]
[/TR]
[TR]
[TD]**Product Type**[/TD]
[TD]Notebook[/TD]
[/TR]
[TR]
[TD]**Manufacturer Website Address**[/TD]
[TD]http://www.toshiba.com[/TD]
[/TR]
[TR]
[TD]**Product Line**[/TD]
[TD]Satellite[/TD]
[/TR]
[TR]
[TD]**Product Series**[/TD]
[TD]M45[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Memory[/TH]
[/TR]
[TR]
[TD]**Standard Memory**[/TD]
[TD]512 MB[/TD]
[/TR]
[TR]
[TD]**Maximum Memory**[/TD]
[TD]2 GB[/TD]
[/TR]
[TR]
[TD]**Memory Technology**[/TD]
[TD]DDR SDRAM[/TD]
[/TR]
[TR]
[TD]**Memory Standard**[/TD]
[TD]DDR333/PC2700[/TD]
[/TR]
[TR]
[TD]**Number of Total Memory Slots**[/TD]
[TD]2[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Miscellaneous[/TH]
[/TR]
[TR]
[TD]**Package Contents**[/TD]
[TD]Satellite M45-S265 Notebook
AC Adapter
Lithium-Ion Battery[/TD]
[/TR]
[TR]
[TD]**Additional Information**[/TD]
[TD]**Multimedia Features:**
**Direct 3D Sound**
**DirectSound**
**Direct Music**
**MIDI (playback) Support**
**Sound Volume (by dial)**[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Network & Communication[/TH]
[/TR]
[TR]
[TD]**Wireless LAN**[/TD]
[TD]Yes[/TD]
[/TR]
[TR]
[TD]**Wireless LAN Manufacturer**[/TD]
[TD]Intel[/TD]
[/TR]
[TR]
[TD]**Wireless LAN Model**[/TD]
[TD]PRO/Wireless 2200BG[/TD]
[/TR]
[TR]
[TD]**Wireless LAN Standard**[/TD]
[TD]IEEE 802.11b/g[/TD]
[/TR]
[TR]
[TD]**Ethernet Technology**[/TD]
[TD]Fast Ethernet[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Physical Characteristics[/TH]
[/TR]
[TR]
[TD]**Height**[/TD]
[TD]1.4"[/TD]
[/TR]
[TR]
[TD]**Width**[/TD]
[TD]14.2"[/TD]
[/TR]
[TR]
[TD]**Depth**[/TD]
[TD]10.6"[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Processor & Chipset[/TH]
[/TR]
[TR]
[TD]**Processor Manufacturer**[/TD]
[TD]Intel[/TD]
[/TR]
[TR]
[TD]**Processor Type**[/TD]
[TD]Pentium M[/TD]
[/TR]
[TR]
[TD]**Processor Model**[/TD]
[TD]730[/TD]
[/TR]
[TR]
[TD]**Processor Speed**[/TD]
[TD]1.60 GHz[/TD]
[/TR]
[TR]
[TD]**Cache**[/TD]
[TD]2 MB[/TD]
[/TR]
[TR]
[TD]**Bus Speed**[/TD]
[TD]533 MHz[/TD]
[/TR]
[TR]
[TD]**Chipset Manufacturer**[/TD]
[TD]Intel[/TD]
[/TR]
[TR]
[TD]**Chipset Model**[/TD]
[TD]915GM Express[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Software[/TH]
[/TR]
[TR]
[TD]**Operating System**[/TD]
[TD]Windows XP Home with SP2[/TD]
[/TR]
[TR]
[TH="colspan: 2"]Input Devices[/TH]
[/TR]
[TR]
[TD]**Pointing Device Type**[/TD]
[TD]TouchPad[/TD]
[/TR]
[TR]
[TH="colspan: 2"]I/O Expansions[/TH]
[/TR]
[TR]
[TD]**Expansion Slot Type**[/TD]
[TD]CardBus Type II[/TD]
[/TR]
[/TABLE]

[/FONT]
```[FONT=&amp]
[/FONT]

---

### Post by paul258 on 2016-04-26
[COLOR=#DD4814][COLOR=#C61919][oldfred]("http://ubuntuforums.org/member.php?u=852711"), [/COLOR][/COLOR][COLOR=#111111][FONT=Ubuntu] I ran that command (sudo parted -1) in the Linux terminal, and it responded back with " invalid option--'1' " usage parted [ -hlmsv] [a<align] [DEVICE [COMMAND .   [/FONT][/COLOR]
[TABLE="width: 660"]
[TR="class: comment"]
[TD][TABLE]
[TR]
[TD][/TD]
[/TR]
[/TABLE]
[/TD]
[TD="class: comment-text"]I opened GParted and I have 2 partitions. (Partition 1) :NTFS>> /dev/sda1 >>size:149.04 GiB used : 11.06 unused:137.98GiB. ( Partition 2) : >>UNALLOCATED size: 10.34 [/TD]
[/TR]
[/TABLE]
[TABLE="width: 660"]
[TR="class: comment"]
[TD][TABLE]
[TR]
[TD][/TD]
[/TR]
[/TABLE]
[/TD]
[TD="class: comment-text"][/TD]
[/TR]
[/TABLE]

---

### Post by oldfred on 2016-04-26
For longer text or terminal output, please use code tags.
Easy to add code tags with forum's advanced editor and the # icon, after highlighting.

sudo parted -l
That is an el - lowercase, not a one nor capital I. What font you see can make it difficult to know.
But best to just copy & paste, highlight with mouse, right click. You can copy from here and paste into your terminal.
If using keyboard to paste in terminal you have to use control-shift-v, where in most other places it is just control-v.

If Pentium M better to use a lightweight system.
Your 2GB is on the cusp between 32 bit and 64 bit.
I had/have a laptop from 2006, but it was Intel dual core with 1.5GB of RAM, and ran 64 bit Ubuntu until they converted to Unity. Unity required so much video horsepower that it would barely run. But installed what is now called gnome-panel which was like the old versions of Ubuntu with menus and it worked fine.

Probably better or easier to use Lubuntu or Xubuntu. 
Not sure about Pentium M. There were some early models with with PAE issue. And I think they all report they do not have it, but really do. Some others know that issue better.

 [https://wiki.ubuntu.com/UbuntuFlavors](https://wiki.ubuntu.com/UbuntuFlavors)
Kubuntu, Edubuntu, Xubuntu, Mythbuntu, UbuntuStudio, Lubuntu, Ubuntu GNOME, Ubuntu Kylin, Ubuntu MATE  
[http://lubuntu.me/](http://lubuntu.me/)

---

### Post by paul258 on 2016-04-26
[COLOR=#DD4814][COLOR=#C61919][oldfred]("http://ubuntuforums.org/member.php?u=852711"), I appreciate  telling me how to paste longer linked pages. That command  ([/COLOR][/COLOR][COLOR=#111111][FONT=Ubuntu]sudo parted -l),  I thought was the number( 1 ), not the small letter of ( l).  I have booted into Linux Lubantu 15 and it works just fine. The question I need help in is should I just totally install Lubantu and wipe the windows xp hard drive , or go to the last option of the installation in ("something else") and try to resize the partitions, which I need help and some advice in doing. What option would you choose ?  I appreciate all the advice that I can get Thank You Sir.[/FONT][/COLOR]

---

### Post by Dennis N on 2016-04-26
> **paul258 said:**
> ...I appreciate all the advice that I can get...
If you want to resize your Vista partition to a smaller size, you should probably do it from Vista to preserve its integrity. Follow their recommendations. Then you will get some unallocated space for other uses, like another Linux distro. I recall from XP you needed to defrag before shrinking - not sure about Vista as I never used it.

I have the identical processor, ram, graphics and network adapter on one of my laptops. It will run Lubuntu or Xubuntu very well, but I guess you can already see that since you have Lubuntu installed!

---

### Post by Enigma12 on 2016-04-26
I'll just jump in here and offer my (not extremely knowledgeable) advice. On my desktop running Lubuntu 14.04.4, I have 2 hard drives. The smaller 40 GB one has root and Home, all program files ( I have added at least 12 additional programs to Lubuntu), and quite a few files that will eventually get moved to the second hard drive, where I store ALL documents, music, videos, photos, etc. That 40 GB drive is less than half full, so I could have partitioned it into two 20 GB partitions (root and something else), and it should still work fine. 

How one partitions drives is, in my opinion, a personal decision, after the needed space is created for the OS and programs. I used Gparted on a separate CD to create partitions on a different computer, and it worked fine, so I can't offer any advice on using the "Something Else" option. You can just look at doing that as a learning experience. If you mess it up, do it again in a different way. Learning is valuable. 

As for the Vista on there, Lubuntu became my replacement for XP when that OS lost MS support and became vulnerable to viruses and malware. Although I was quite competent and pleased with XP when I used it for years, I frankly prefer Lubuntu over XP, especially with all the extra capability that I have added to it.

Lastly, and VERY important, make certain that you have at least one complete backup of anything on that hard drive that you want to keep. Installing Lubuntu WILL reformat the hard drive. 

Hope this helps.

---

### Post by oldfred on 2016-04-26
Well XP, is totally obsolete, so you really should not use it to connect to Internet. 
If Vista, I would keep it even thought reported to be one of the poorer versions of Windows. Defrag, shrink with Windows tools and reboot immediately so it can run chkdsk.

But I took me a long time to convert from XP to Ubuntu. And I dual booted for many years, just because of one application. But after using XP just once per week and having many, many updates, and reboot for each and reboot up to 3 to 5 minutes, I finally gave up on XP.

Many wipe Windows, and then find that one app or game and want Windows back, so we generally suggest dual booting until you get to the point of being comfortable with Ubuntu and have found equivalent (but not necessarily the same) apps and learned to use them.

If you only have 2 primary partitions, then you have an available primary to use as an extended partition. The extended partition is a primary partition that is somewhat like a container for as many logical partitions as you want. Windows only boots from primary partition, but Linux works fine from logical partitions. Old MBR partitioned systems have a 4 primary partition limit.

As Enigma12 says:
> How one partitions drives is, in my opinion, a personal decision

If a new user you only need / (root) and swap.
Many then add /home as a separate partition, but then have to use the bit more advanced Something Else install option to create & choose each partition and what it is used for.

Even more advanced is separate data partitions. If planning to dual boot many like a separate shared NTFS data partition, so you do not write into the Windows system partition which can lead to issues. But the NTFS partition has to be done with gparted, either before or after install as installer does not offer NTFS as an option.

[https://help.ubuntu.com/community/DiskSpace](https://help.ubuntu.com/community/DiskSpace)

---

