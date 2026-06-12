---
title: "Will it be easier to fix 8.10, or reinstall 8.04?"
date: 2008-11-18
forum: Installation &amp; Upgrades
---

### Post by Nicole on 2008-11-18
Hi,

I upgraded this afternoon to 8.10, from 8.04 - a decision I'm already deeply, deeply regretting!

I use a Dell XPS M1330, and am not the most technical of people, though I've managed to make Ubuntu work well for me over the last few years. The lesson I will take from this is: don't fix something that's not broken! The major problem is that my wireless internet (which worked flawlessly under 8,04) won't work now - although the light at the top shows that the wireless bit (see? lack of technical, sorry...) *itself* is working - and it does work when I booted into Vista to check.

Having finally dug out an ethernet cable (hence typing this) my network manager doesn't seem to recognise it (although it obviously works) - if I keep 8.10, is there a way to get a nicer network manager? This doesn't seem to be a step forward, from the perspective of someone like me - I'm probably missing its fabulous features, but it just looks horribly user-unfriendly, unlike the one in 8.04.

I've got a separate /home partition. Is it going to be easier to reinstall 8.04? I'm happy to do that, since I'm hardly deeply invested in 8.10, but if there's some relatively easy solution to make Ubuntu 8.10 work well, that would be better - I've googled for the last 2 hours and can't find anything that helps - this might be because I'm googling for the wrong thing, I suppose, but I've tried anything I can think of and am now stuck...

Any advice at all gratefully received - I never realised how much I relied on the Internet! I read up on this before I upgraded, read a whole load of glowing reviews and decided to give it a shot - I won't make that mistake again...

If there's more information you need from me to sensibly help, my apologies - please let me know and I'll happily provide it.

Many thanks to you all,

Nicole

---

### Post by dabl on 2008-11-18
Without knowing the first fact about your wireless chip, I'll boldly assert that it can be made to work correctly in 8.10.  Maybe it needs firmware downloaded and installed, or maybe you have to manually configure the /etc/network/interface file, and possibly also /etc/wpa_supplicant/wpa_supplicant.conf file.

If you open the console and do ```
lspci
``` you will learn the make and model of the chip.  Then if you search this forum, probably in "hardware and laptops" and/or "networking and wireless", you should be able to discover what the driver is and what the configuration needs to be.  :)

And yes, you also could just re-install 8.04 in the same partition that it was previously in, if you're sure it will automatically configure everything.  :)

---

### Post by Rohan Kapoor on 2008-11-18
Have you checked the restricted drivers section?

---

### Post by Nicole on 2008-11-18
Thank you both! I'll do some more searching dabl, and darth, do you know offhand how  I find the restricted drivers section? (In 8.04, I thought there was a menu item in System>Preferences/Admin, but can't find similar here...)

This shouldn't be as difficult as it seems at the moment, I'm sure!

Your patience is much appreciated!

---

### Post by Nicole on 2008-11-18
Never mind, am an idiot, found drivers section - will give that a shot now...

ETA: Except, it won't open. I click on it, it does nothing. Is there a way (and I can't really believe I'm asking this) to do this through the terminal, since it appears not to want to do it normally?

---

### Post by dabl on 2008-11-18
This should help:

[https://help.ubuntu.com/community/WifiDocs/Adhoc](https://help.ubuntu.com/community/WifiDocs/Adhoc)

Note on the right where there are links to brands of cards.

---

### Post by Rohan Kapoor on 2008-11-18
> **Nicole said:**
> Never mind, am an idiot, found drivers section - will give that a shot now...

ETA: Except, it won't open. I click on it, it does nothing. Is there a way (and I can't really believe I'm asking this) to do this through the terminal, since it appears not to want to do it normally?

I would recommend quiting X (Ctrl-Alt-Backspace). This will then reset X and load the login screen. Log back in and try again from there. I don't have anything to test with right now because I had to re-install 8.04 after 8.10 trashed by Big-Desktop and won't upgrade for a while.

Could you give me the output of the

```
lspci
```

as Dabl suggested.
Sorry, but that's all I can offer.

Thanks.

---

### Post by Nicole on 2008-11-18
typing lspci gives:

> 00:00.0 Host bridge: Intel Corporation Mobile PM965/GM965/GL960 Memory Controller Hub (rev 0c)
00:02.0 VGA compatible controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:02.1 Display controller: Intel Corporation Mobile GM965/GL960 Integrated Graphics Controller (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1c.5 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 6 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI Controller #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI Controller #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation 82801HEM (ICH8M) LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation 82801HBM/HEM (ICH8M/ICH8M-E) SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd R5C832 IEEE 1394 Controller (rev 05)
03:01.1 SD Host controller: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd R5C843 MMC Host Controller (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev ff)
09:00.0 Ethernet controller: Broadcom Corporation NetLink BCM5906M Fast Ethernet PCI Express (rev 02)
0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)
 

I think I'm going to give up on this for now, it's driving me mad and it's getting late here - thanks very much for your efforts in helping!

Nicole

---

### Post by Rohan Kapoor on 2008-11-18
Allright This is what I think; you need to install ndiswrapper, and the drivers for 0c:00.0 Network controller: Intel Corporation PRO/Wireless 3945ABG [Golan] Network Connection (rev 02)

---

### Post by dabl on 2008-11-18
Says here that chip works out of the box:

[https://help.ubuntu.com/community/WifiDocs/Adhoc#Intel](https://help.ubuntu.com/community/WifiDocs/Adhoc#Intel)

Well, I guess they lied!  :lolflag:

Seriously, before you go any further, try again with the "Restricted Hardware" thing, except this time, when you get to the icon, give it one click and then just walk away.  I've noticed (with video drivers) it sometimes has a painfully long lag time, during which it is going out on the 'net and downloading driver files.

If that doesn't work, I found this:

[http://www.linuxtent.com/?p=118](http://www.linuxtent.com/?p=118)

The last paragraph has the steps that work for Hardy -- I'd do those and see if you are closer to success (or maybe all the way).

---

### Post by Nicole on 2008-11-20
Thanks very much for your help guys, but it's still not working. Oddly, they didn't totally lie - if I use the 8.10 live cd, it recognises my wireless, and works fabulously. Which suggests that the upgrade didn't quite work properly. In which case, I suppose the best solution is to reinstall 8.10, over the top of the possibly-corrupt 8.10 I've got now?

This is made a bit more complicated by the fact that I have Vista also on this computer, and a separate /home partition - and the 8.10 live cd installer didn't seem to recognise any of them... Should I be concerned about this, do you think?

Thanks again,

Nicole

---

### Post by dabl on 2008-11-20
Before you re-install, what happens if you open a console window and 

```
sudo modprobe iwl3945
```

and then

```
sudo ifconfig wlan0 up
```

???

Errors would be interesting, if it spits any out.

If it turns out that the module is already installed, then it may be a configuration issue, i.e. /etc/network/interfaces.  If it turns out to be that, then you can boot the 8.10 Live CD and when it is running, open /etc/network/interfaces and see how it configured itself, and then use that configuration in your installed system.  :)

---

### Post by Nicole on 2008-11-20
The first didn't bring up any errors, the second brought up: 

wlan0: ERROR while getting interface flags: No such device

The idea of looking at /etc/network/interfaces when it's working and copying it over is a good one - I (obviously!) hadn't thought of that!

---

### Post by Nicole on 2008-11-20
The only thing in the Live CD version of /etc/network/interfaces was:

auto lo
iface lo inet loopback

Which I've made the version here match, with a view to installing wicd and seeing if that will work (that's what worked with the Live CD, because of the type of encryption on my wireless connection - network-manager wouldn't deal with it, it's too basic, it seems!) But I think the problem is bigger than just the wireless not working properly - the problem is with some of the graphical menus - Hardware Drivers was the first one I noticed that wasn't working properly, but neither is the repositories menu in Synaptic, or the update manager.

I wish I'd never made any changes at all now! It was working so well!

---

### Post by dabl on 2008-11-20
> **Nicole said:**
> 

 neither is the repositories menu in Synaptic, or the update manager.



Sounds like the /etc/apt/sources.list file is also messed up. Which is fixable, but I wonder "what else?".

I would think wicd would straighten out your wireless, but with these other issues, you might get a better overall result by just installing 8.10 from the CD.

---

### Post by Nicole on 2008-11-20
That's my thinking, too. Though I'm concerned about installing from scratch, since the installation CD doesn't seem to recognise that I have existing partitions (one for Vista, one for some random thing vista needs, one for /home and one for the rest of Ubuntu - plus probably some others, they go up to sda8, which is /home) and I definitely don't want to install over Vista and /home - though I can replace home relatively easily, since I've backed up the contents, I'd prefer not to. And reinstalling Vista would be a huge pain.

Am I missing something really obvious that would explain why the installer doesn't notice my partitions? Does it not matter, and I'm over-thinking this? It seems to think that the whole harddrive is one block and the only option it gives me is to set up a new partition table, which it warns me will destroy whatever's on there already - not ideal... But the partitions clearly exist, and ubuntu knows about them and vista knows about them. I hate not knowing what I'm doing!

---

### Post by dabl on 2008-11-20
You're not over-thinking -- Vista's use of TWO partitions by default leaves you stuck with only two more primary partitions available for your Linux system.  Which means, either you live with "/" and swap and that's all, or else you go to Extended + logical partitions.  Since you have /home already on its own partition, I think you must go with an extended partition as the fourth, and then within the extended partition you can put both /home and swap on two logical partitions.  During installation, you can choose your /home partition to be mounted as /home (in other words, you will choose /dev/sdac or whatever its device name is, and then select "/home" as the mount point, but DON'T format that partition).

I use a GParted Live CD, downloaded from Sourceforge to do partitioning -- I don't remember whether the recent Ubuntu Live CDs include a partitioner or not.  Here's the Sourceforge link:

[http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779](http://sourceforge.net/project/showfiles.php?group_id=115843&package_id=271779)

---

### Post by Nicole on 2008-11-20
My grasp of partitioning is, well, not all that... But it seems to me the problem I have is that when it comes to choosing where to install what, I don't have a choice - it treats is as all one unallocated space, except that it's clearly not... [http://ubuntuforums.org/archive/index.php/t-631791.html](http://ubuntuforums.org/archive/index.php/t-631791.html) explains it a bit better than me, he had exactly the same problem (sadly, no solution - but his has pictures, which help clarify!)

---

### Post by dabl on 2008-11-20
Hmmmmm.  That is weird, but I have heard that problem report before.  I suspect that it is an issue with the SATA bus "mode" -- if you go into BIOS and change the mode to "AHCI" or "RAID" or "Legacy IDE" or something else, it might allow the installer to see the partitions.

[http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface](http://en.wikipedia.org/wiki/Advanced_Host_Controller_Interface)

Note the "common problems" section.

But I realize this is not a desired undertaking - and changing that mode setting might cause Vista not to boot.  It's also possible that you could change it, install Ubuntu, and then change it back, and all would be well. No way to tell from here.  :confused:

---

### Post by Rohan Kapoor on 2008-11-20
Are you able to boot Vista? Because you may have corrupted the entire drive.

---

### Post by Nicole on 2008-11-20
Yep, there's no problem booting windows - it's just ubuntu that's... messed up!

Neither the 8.04 nor 8.10 live CDs, nor the 8.10 alternate CD or gparted, can see the partitions - but windows can, and fdisk -l brings up:

> Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes
Disk identifier: 0x08000000

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1   *       14267       14594     2620416    c  W95 FAT32 (LBA)
/dev/sda2              15        1320    10485760    7  HPFS/NTFS
/dev/sda3   *        1321        7084    46299330    7  HPFS/NTFS
/dev/sda4            8367       14594    50019402+   f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown
/dev/sda6   *        8367       10916    20482812   83  Linux
/dev/sda7           14021       14266     1975963+  82  Linux swap / Solaris
/dev/sda8           10917       14020    24932848+  83  Linux


So, they obviously are there. 

I just have no idea at all where to go now - I want to fix it, but can't. I'd settle for taking it back to where it was earlier this week, but apparently can't. Do I have any good options?

---

