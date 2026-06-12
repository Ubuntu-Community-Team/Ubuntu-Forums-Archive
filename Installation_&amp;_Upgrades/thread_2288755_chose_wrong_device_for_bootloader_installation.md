---
title: "chose wrong device for bootloader installation"
date: 2015-07-29
forum: Installation &amp; Upgrades
---

### Post by inigodenoriega on 2015-07-29
Hi!

I have a new computer, with a SSD and HDD, with no operating  system. The idea is to use the SSD for the operating systems, and the  HDD for data. I installed Win7 64 bit in the SSD, from a USB key.
I  then installed Ubuntu 14.04.2 LTS, partitioning the SSD, reducing space  for Windows and adding the / and /swap partitions in the SSD, for a  total of 4 partitions on that drive. The first partition was very small  in size and at the beginning of the drive, probably done by Windows (I  am not an expert.)
Note that could be important: I had trouble with  the Ubuntu live USB install, and had to edit the GNU-GRUB line adding  "Nomodeset" in order for the screen to show up properly.

I have  the impression that during the Ubuntu installation, when given the  option "Device for bootloader installation," I chose incorrectly. So now  when the PC starts up, the GNU GRUB screen in order to select the  operating system does not show up, and no OS is loaded. The screen does  show up the purplish hue of when Ubuntu loads, but does nothing more.
However, as I said, I am not an expert.

I can start Ubuntu with a live USB, and am able to access both drives and both operating system folders.

I  tried reinstalling Ubuntu with the live USB. During installation it  said it detected the previous Ubuntu, and I chose to completely  overwrite the previous Ubuntu installation, not the Windows one. But the  result was identical: no GNU-GRUB window, and no OS loaded.

What  should I do to be able to place the bootloader correctly, that it  detects both OSs, and also remove the one incorrectly installed (if I  can find it)?

As a last resort, I could format everything and reinstall, but would prefer to try first less drastic measures.

---

### Post by Bashing-om on 2015-07-29
inigodenoriega; Hello;

One can easily (RE-)install grub from the liveUSB.
We need to know the location of grub's config files. We find that out from the output of terminal command:
- Boot the liveUSB "try ubuntu" mode to a terminal - 
```

sudo fdisk -lu

``` 
and install the boot code to the correct device .

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by inigodenoriega on 2015-07-30
Thanks Bashing,

I tried with the boot-repair option, and chose to install it in sda and sdb, with a selection timer of 10 seconds. The grub menu does appear now. It doesn't seem to recognize Windows 7, as the three options it gives are:
1. Ubuntu
2. Advanced options for Ubuntu
3. System setup
-If I choose Ubuntu, a blank screen with the purplish hue appears, as before using the boot-repair. Since it is the default option, if I don't press any button, after the timer expires, I get the same result.
-Under advanced options, the blank screen appears if I choose another  Ubuntu. However, if a recovery mode is chosen, I reach the recovery  menu. I have not tried anything from here.
-If I choose system setup, the following error appears:
error: can't find command `fwsetup'.

In any case, I am getting the idea that this might be an issue of the graphics card.

If it's any help, the report page from boot-repair:
[http://paste.ubuntu.com/11966977/](http://paste.ubuntu.com/11966977/)

---

### Post by Bashing-om on 2015-07-30
inigodenoriega; Yeah ;

I too think you are on the right track that this is a graphics driver issue.
We need to find out the hardware on the system and match a driver ( most of the time the kernel will do that automagically) and install the appropriate driver. Generally, no big deal.

let's look ! As you can boot to the " recovery console" we can work from that terminal.
As all we are doing presently is looking, no further action to enable the system is required.
So, boot to the "recovery" console -> "enable root terminal";

Now to know what is for hardware. Post back the output of terminal commands:
```

lspci -vnn | grep VGA -A 12

```
to tell us the graphics hardware.

Then we want to know if/what driver is loaded:
```

lshw -C display

```
Of interest here is what is in the configuration line. 
For reference my output:
```

capabilities: pm pciexpress msi vga_controller bus_master cap_list rom
       configuration: driver=radeon latency=0

```
where it shows my loaded driver is a 'radeon' driver (  configuration: driver=radeon ) .

With this information, we see where we go from here.

[INDENT][INDENT]ain't nothing but a thing
[/INDENT][/INDENT]

---

### Post by inigodenoriega on 2015-07-31
Logged in in recovery mode, and the first command gave this as an output (I don't know how to stop the text scrolling, so the previous text is lost):
[ATTACH=CONFIG]263516[/ATTACH]
Sorry for the quality of the photo.
The card is an NVidia [FONT=Geneva][SIZE=2]Gigabyte GeForce GTX 960 (GV-N960WF2OC-2GD).[/SIZE][/FONT]

The second command gave the following:
[ATTACH=CONFIG]263515[/ATTACH]
I think that it's understandable despite the Spanish text. Note that there are at least two places where it gives the line equivalent to the one you state:[INDENT]fabricante: NVIDIA Corporation
[...]
capacidades: pm msi pciexpress vga_controller bus_master cap_list
[/INDENT]
[INDENT]configuración: latency=0
[/INDENT]
[INDENT]fabricante: Intel Corporation
[...]
capacidades: msi pm vga_controller bus_master cap_list
[/INDENT]
[INDENT]configuración: latency=0
[/INDENT]
Probably one is integrated in the processor, the other one is the graphics card.

There does not seem to be a driver loaded.

Hope this gives a lead to follow...

---

### Post by oldfred on 2015-07-31
Boot-Repair says grub2's os-prober cannot find Windows. Did you leave Windows hibernated, or is it Windows 8 with fast start up which is always hibernated. Or did you not reboot after NTFS partition resize as it always needs chkdsk after a resize. 
If so you may need to temporaryly restore the Windows boot loader to correct those issue(s). The reinstall grub. Boot-Repair can restore a Widows boot loader, but cannot do other Windows repairs. Best to have a Windows repair flash drive. From grub you cannot get to f8 in time to get to Windows repair console, and grub only boots working Windows. And you may not always be able to use f8 even if directly booting Windows.

       How to restore the Ubuntu/XP/Vista/7 bootloader 
[https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader](https://help.ubuntu.com/community/RestoreUbuntu/XP/Vista/7Bootloader)
[URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System
[/URL]
 f8 to get to repair install screen, if you can start to boot
[http://www.sevenforums.com/tutorials/666-advanced-boot-options.html](http://www.sevenforums.com/tutorials/666-advanced-boot-options.html)
[URL="http://www.sevenforums.com/tutorials/681-startup-repair.html"]http://www.sevenforums.com/tutorials/681-startup-repair.html
      [/URL]
 Windows 7 repair USB, Also Vista if service pack installed
[http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/](http://www.intowindows.com/how-to-repair-windows-7-from-usb-flash-drive-repair-without-installation-dvd-disc/)
[http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html](http://www.webupd8.org/2010/10/create-bootable-windows-7-usb-drive.html)
Windows 8 UEFI repair USB must be FAT32, not for reinstall, just repairs
[http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html](http://www.eightforums.com/tutorials/2855-system-repair-disc-create-windows-8-a.html)

You are showing UEFI capable hardware but all installs are in BIOS boot mode. The fwsetup may only work when booting into grub with UEFI. But UEFI and BIOS are not compatible, so you need to always boot in BIOS mode since all installs are BIOS.

You show two video modes Intel & nVidia. But then should not have any Radeon driver. Purge that.

Is video two separate video (different ports?) or nVidia Optimus that switches one video port?
If separate have you tried booting with just Intel. New Intel versions also often need boot parameters like nVidia needs nomodeset to boot.       
 # Usually nVidia or AMD work with this:
nomodeset
# Usually Intel works with one of these:
i915.modeset=0
i915.i915_enable_rc6=1
video=1280x1024-24@60  # but change to your monitor size  not 1280x1024
video=VGA-1:1280x1024-24@60  # but change to your monitor size

Is the new nVidia 960 a Maxwell based card?  I know the 750/970/980 are and have issues needing a very new kernel, support software & nVidia driver.        
 The GTX 970/980 Maxwell GPUs Light Up With Nouveau On Linux 3.19
[http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg](http://www.phoronix.com/scan.php?page=news_item&px=MTg4NTg)
NVIDIA GeForce GTX 970/980: Windows vs. Ubuntu Linux Performance 2015 note versions ppas used to update
[http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1](http://www.phoronix.com/scan.php?page=article&item=nvidia_maxwell900_winlin&num=1)

    [URL="https://help.ubuntu.com/community/Grub2/Installing#Fixing_a_Broken_System"]
[/URL]

---

### Post by inigodenoriega on 2015-08-02
Thanks, Oldfred, that's a lot of information.

The Windows was a standard Windows 7 I installed previously and was working fine, making full use of screen resolution and so on. I then installed Ubuntu and had the issue with the grub menu not showing up, so I used a Ubuntu liveUSB to reinstall grub, but it seems to have "lost" Windows, and does not permit to boot into Ubuntu, only in recovery mode.

I have not installed any Radeon drivers. I am unable to identify them either.

If I understand correctly, you suggest to take the following steps:
1. Reinstall Windows bootloader, to recover access to Windows.
2. Restore grub, hopefully this way it will "keep" the Windows option.
3...
From then on, I'm not sure what to do.

If I boot with a liveUSB and use nomodeset, I have low screen resolution, and am unable to change the resolution. With the grub that I have reinstalled (the one that doesn't show Windows), if I boot into standard Ubuntu, I get the black screen crash. If I use the recovery mode, the highest resolution I get is 1024x768.

Do you think I should download and install (I'll search other threads on how to do it) specific nVidia drivers, to see if I can then be able to boot the "default" Ubuntu? There seems to be a Linux x64 (AMD64 / EM64T) driver in the manufacturer's page, version 352.30:
[http://www.geforce.com/drivers/results/87650](http://www.geforce.com/drivers/results/87650) this
Do you think this will be a) compatible with the system and b) permit to solve the issue?

It does seem that the graphics card is a Maxwell-based one.
[http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-960](http://www.geforce.com/hardware/desktop-gpus/geforce-gtx-960)

---

### Post by oldfred on 2015-08-02
You need nomodeset to boot into lower quality graphics. Recovery mode uses nomodeset by default.
       At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

    
Some other Maxwell nVidia driver issues, may show older drivers. If specific version shown make sure you change to use most current that ppa has, it may have several.

 Maxwell 750 - kernel 3.15 or newer required
[http://ubuntuforums.org/showthread.php?t=2214805](http://ubuntuforums.org/showthread.php?t=2214805)
[http://ubuntuforums.org/showthread.php?t=2265505](http://ubuntuforums.org/showthread.php?t=2265505)
Usually better to use PPA.
[http://ubuntuforums.org/showthread.php?t=2252908](http://ubuntuforums.org/showthread.php?t=2252908)
[http://ubuntuforums.org/showthread.php?t=2257506](http://ubuntuforums.org/showthread.php?t=2257506)



But the Maxwell based nVidia seem to need the very newest nVidia driver, but best to add a ppa which is a private repository (make sure reliable) and then it installs the newest. Best not to download a driver directly from nVidia.

Radeon is AMD video, not nVidia.

Several different ppa's mentioned in different threads. Not sure if one better than other.
       Install Nvidia 340.24 from ppa:xorg-edgers/ppa
[http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/](http://www.sysads.co.uk/2014/07/install-nvidia-340-24-driver-ubuntu-14-04/)
14.04 drivers for Nvidia GeForce GT 730 desktop board - 
[http://ubuntuforums.org/showthread.php?t=2240702](http://ubuntuforums.org/showthread.php?t=2240702)
PPA for nVidia mamarley pps
[http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945](http://ubuntuforums.org/showthread.php?t=2256437&p=13185945#post13185945)
[https://launchpad.net/~mamarley/+archive/ubuntu/nvidia](https://launchpad.net/~mamarley/+archive/ubuntu/nvidia)
All the current drivers xorg-edgers PPA
[https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages](https://launchpad.net/~xorg-edgers/+archive/ubuntu/ppa/+packages)
Oibaf PPA discusion
 [http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1](http://www.phoronix.com/scan.php?page=article&item=ubuntu_1310_oibaf&num=1)

---

### Post by inigodenoriega on 2015-08-03
Thanks again. I have found a way that seemingly has solved the issue, so I now post it.

One of the times I rebooted the computer, the option to load Windows magically appeared in the grub menu (duplicated, both in sdb1 and sdb2) :confused:. I have tried sdb1, and it works. So there's no longer need to reinstall the Windows bootloader. I haven't got a clue why this happened, I didn't do any installing or uninstalling. 

From the current post and other posts, I see how you are not very keen on downloading directly from the manufacturer's webpage. I have seen in several posts that the results can be disastrous, and since it is a manual install it doesn't update later automatically as software installed through the software centre.

However, I found the following post, and the method described worked fine:
[http://ubuntuforums.org/showthread.php?t=2263316](http://ubuntuforums.org/showthread.php?t=2263316)
I used a 64-bit version, and during installation it did give point out some 32-bit errors which don't do much to ease my mind, but it. I now have the full 1920x1080 resolution. I haven't yet tried games or anything too taxing, but for the moment everything seems ok.

---

### Post by oldfred on 2015-08-03
Glad that worked, but since directly from nVidia, you will have to reintegrate it into kernel with every new kernel update. 
If you reboot before updating then you will have issues with new kernel. Older one should work.
I have seen that newer versions may have a -dkms option that resolves that issue when installing nVidia driver. Did you use that?

>  The '--dkms' option, with driver versions 3.04.xx and later, will check that 'dkms' is installed and offer the option to register the driver with dkms, so the kernal module gets updated automatically when a new kernal is installed. and does not need to be manually re-installed.



The advantage of a ppa is that it is seen just as another repository and the update process automatically runs the full updates to integrate driver into new kernel.

---

