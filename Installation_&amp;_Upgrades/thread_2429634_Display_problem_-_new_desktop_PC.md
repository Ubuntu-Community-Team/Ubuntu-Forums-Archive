---
title: "Display problem - new desktop PC"
date: 2019-10-21
forum: Installation &amp; Upgrades
---

### Post by satimis on 2019-10-21
Hi all,

Just finished building a new desktop PC with following configuration:
```

RAM  Corsair Vengeance RGB PRO CMW32GX4M2C3200C16 DDR4 3200MHz 32GB Kit (16GB*2)
CPU  AMD Ryzen 5 3400G YD3400CCPU BOX w/Cooler
Motherboard  ASUS PRIME X570-P/CSM X570,AM4 Socket,USB3.2,PCIe 4.0 M.2 ATX M/B
HDD  Samsung 2TB 860 EVO Series MZ-76E2T0BW 2.5" SATA3 6Gb/s SSD

```

I'm still running an old 25" DELL 3K display (Resolution 2560x1440) and now shopping a >30" 4K display.

I'm now test-building Ubuntu 16.04 desktop on an 180G SSD Drive.  The PC is now up running but it is still working on a [Build-in Display], resolution [1024x768(4:3)].  No other selection is available?

Please advise how to fix the problem.  I need a driver from AMD or from ASUS?

Please advise.  Thanks in advance.

Regards
satimis

---

### Post by Dennis N on 2019-10-21
Drivers for integrated graphics come with the kernel. You may need a newer version of Ubuntu than 16.04 to get a later kernel.

---

### Post by satimis on 2019-10-21
> **Dennis N said:**
> Drivers for integrated graphics come with the kernel. You may need a newer version of Ubuntu than 16.04 to get a later kernel.
Thanks for your advice.

Whether you meant upgrade it to Ubuntu 18.04 ?  I can do it.  This is only a test installation.

On terminal:
========
$ uname -r```

4.15.0-65-generic

```

$ uname -a```

Linux SSD180G 4.15.0-65-generic #74~16.04.1-Ubuntu SMP Wed Sep 18 09:51:44 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

$ lsb_release -a```

No LSB modules are available.
Distributor ID:	Ubuntu
Description:	Ubuntu 16.04.6 LTS
Release:	16.04
Codename:	xenial

```

$ lsb_release -r```

Release:	16.04

```


[https://kernel.ubuntu.com/~kernel-ppa/mainline](https://kernel.ubuntu.com/~kernel-ppa/mainline)
```

......
......
[DIR]	v5.3.1/	2019-09-21 07:32 	- 	 
[DIR]	v5.3.2/	2019-10-01 11:44 	- 	 
[DIR]	v5.3.3/	2019-10-05 16:08 	- 	 
[DIR]	v5.3.4/	2019-10-05 16:35 	- 	 
[DIR]	v5.3.5/	2019-10-07 19:37 	- 	 
[DIR]	v5.3.6/	2019-10-11 18:34 	- 	 
[DIR]	v5.3.7/	2019-10-18 13:17 	- 	 
[DIR]	v5.3/	2019-09-15 23:31 	- 	 

```

I suppose the latest version of linux kernel is```

[DIR]	v5.3.7/	2019-10-18 13:17 	- 	

``` 

Regards
satimis

---

### Post by #&amp;thj^% on 2019-10-21
Installing the HWE stack is simple:

Desktop
```

 sudo apt install --install-recommends linux-generic-hwe-16.04 xserver-xorg-hwe-16.04 
```

Server
```

 sudo apt install --install-recommends linux-generic-hwe-16.04 
```
Which will bring in Kernel "v5.3"

---

### Post by Dennis N on 2019-10-21
I believe 3400G was released earlier this year, so you might need Ubuntu 19.10 to get the latest graphics driver - it uses 5.3 kernels.

---

### Post by #&amp;thj^% on 2019-10-21
> **Dennis N said:**
> I believe 3400G was released earlier this year, so you might need Ubuntu 19.10 to get the latest graphics driver - it uses 5.3 kernels.

Thanks for pointing that out: [https://github.com/M-Bab/linux-kernel-amdgpu-binaries](https://github.com/M-Bab/linux-kernel-amdgpu-binaries)

---

### Post by satimis on 2019-10-21
> **Dennis N said:**
> I believe 3400G was released earlier this year, so you might need Ubuntu 19.10 to get the latest graphics driver - it uses 5.3 kernels.
Hi,

19.10 is not LTS

---

### Post by #&amp;thj^% on 2019-10-21
> **satimis said:**
> Hi,

19.10 is not LTS

Just for fun try to add "**amdgpu.dc=1**" to the boot parameters. For 4.15 kernel.

---

### Post by ubfan1 on 2019-10-21
Neither is the HEW, so you get 9 month support either way on the 5.3 kernel (which I think you need).  In any case, have you updated your firmware?  All sorts of fixes have been recently released.

---

### Post by satimis on 2019-10-22
Hi all,

Thanks for your advice.

I couldn't install the Setup CD, coming with the motherboard, without wine running.

Insert CD on CD Writer it popup
```

Reading "Setup.exe"
Please wait
[Cancel]

```

The CD was runnning and the popup notice was hanging there for prolonged time and closed finally with following warning popup```

An error occurred while loading the archive
[Close]

```

Files on CD (please see screenshot_cd_01.png attached)

CD
Setup.exe

isolinux (folder)```

data (folder)
src (folder)
boot.cat
isolinux.bin
isolinux.cfg

```

data (folder)```

boot.ima

bootmsg.txt;
A Bootable DVD/CD is detected. Press ENTER to boot from the DVD/CD.
If no key is pressed within 5 seconds, the system will boot from next priority device automatically.

memdisk

```

src (folder)```

FDOEMCD.builder.zip
FDOEMCD.source.zip
FDOEMCD.source-tools.zip

```

LinuxDrivers (folder)```

readme.txt;
Note: Please update to the latest Linux Kernel for motherboard chipset and components support.

```

On following ASUS link;
[https://www.asus.com/hk-en/Motherboards/PRIME-X570-P/HelpDesk_BIOS/](https://www.asus.com/hk-en/Motherboards/PRIME-X570-P/HelpDesk_BIOS/)
BIOS & FIRMWARE
Only BIOS
undefined 1201 2019/09/12

No Firmware found.  I already download the BIOS and will update the motherboard BIOS later.

Nothing found on [Driver & Tools]


Is there any way to install Setup.exe without wine ?

Thanks

Regards
satimis

---

### Post by ubfan1 on 2019-10-22
If the setup.exe is not a Windows executable, you might try running it under freedos.  Download a copy from the net.  I've never done this myself.

---

### Post by satimis on 2019-10-22
Hi all,

I have received a discouraging reply in writing from ASUS Technical Support in response to my email in re of resolution problem.  It said that the motherboard PRIME X570-P is for Windows 10 64bit and no software available for Linux.

Then I have to solving the resolution problem myself.

Performed following Tests.

Test-1
====
$ sudo apt install wine

Insert CD on the Writer
Popup```

You have just inserted a medium.  Choose what application to lauch
[Ask what to do ]
-> OK

```

The Popup window closed and nothing happend

Again;
On CD folder
click Setup.exe
popup```

[An error occurred while loading the archive
[close]]

```


Test-2
====
On Terminal upgrade Ubuntu 16.04 to 18.04
&#10219; sudo apt update && sudo apt upgrade
&#10219; sudo reboot
&#10219; sudo do-release-upgrade
.......
.......

It took a while upgrade to Ubuntu 18.04.3 LTS.  After finished rebooted PC.

Ubuntu 18.04 is up running but still the Display resolution is 1020x768 (4:3), no other resolutions are available.

$ uname -r```

4.15.0-66-generic

```

$ uname -a```

Linux SSD180G 4.15.0-66-generic #75-Ubuntu SMP Tue Oct 1 05:24:09 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```


Test-3
====
Found an old WD HDD, 180G, and installed Ubuntu 19.10 on it, using an USB installer.  Installation went throught without problem.  The screen looked as a high resolution one.

After finished and reboot.  It boots to a dark screen finally.

Suggestion would be appreciated.

Regards
satimis

---

### Post by ubfan1 on 2019-10-22
If setup.exe is not a Windows executable, you might be able to run it under freedos (download from the web).

---

### Post by Bashing-om on 2019-10-22
satimis; Hello-

AMD graphics ? You may also consider updating the firmware:
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700)
[https://www.phoronix.com/scan.php?page=news_item&px=AMDVLK-2019.Q4.1-Released](https://www.phoronix.com/scan.php?page=news_item&px=AMDVLK-2019.Q4.1-Released)

These offer enhanced monitor supports, and Yes 19.10 has the better support for newer hardware.

[INDENT]my bit to try and help [/INDENT]

---

### Post by Dennis N on 2019-10-22
I think the CD is for installing Windows drivers. No use to you unless you are installing Windows.
> After finished and reboot. It boots to a dark screen finally.
You may need to add some extra boot parameters to the GRUB_CMDLINE_LINUX_DEFAULT= in /etc/default/grub
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
Someone familiar with AMD boot problems in these recent systems (not me) can probably suggest what to try, and/or you can do some Google research.

---

### Post by satimis on 2019-10-22
> **Bashing-om said:**
> satimis; Hello-

AMD graphics ? You may also consider updating the firmware:
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700)
[https://www.phoronix.com/scan.php?page=news_item&px=AMDVLK-2019.Q4.1-Released](https://www.phoronix.com/scan.php?page=news_item&px=AMDVLK-2019.Q4.1-Released)

These offer enhanced monitor supports, and Yes 19.10 has the better support for newer hardware.

[INDENT]my bit to try and help [/INDENT]
Hi,

Thanks for your advice and links.  I'll try them on Ubuntu 18.04 later.  Now I manage making Ubuntu 19.10 running.  Please see my now posting below

satimis

---

### Post by satimis on 2019-10-22
Hi folks,

Lot of thanks for your continue support.  Now I make Ubuntu 19.04 working.  Wonderful it supports higher resolution on screen.

Ubuntu 19.04
$ uname -r```

5.3.0-19-generic

```

$ uname -a```

Linux WD180G 5.3.0-19-generic #20-Ubuntu SMP Fri Oct 18 09:04:39 UTC 2019 x86_64 x86_64 x86_64 GNU/Linux

```

Screen Resolution:
2560 x 1440 (16.9)
(Remark:  It is the highest resolution of my DELL Display.  I'm prepared purchasing a 4K display)

The CD doesn't work here, autorun having no effect.  It is for Windows.```

[autorun]
open = Bin\Instv2.exe
icon = asus.ico

```

I'll come back after making further test on Ubuntu 18.04

Regards
satimis

---

### Post by satimis on 2019-10-22
Install the latest Linux kernel on Ubuntu 18.04

Steps performed as follows;

1)
Update, upgrade and verify running kernel```

$ sudo apt update && sudo apt dist-upgrade && sudo apt autoremove

$ uname -r
4.15.0-66-generic
```

2)
Install UKUU```

$ sudo add-apt-repository ppa:teejee2008/ppa
$ sudo apt-get update && sudo apt-get install ukuu

```

3)
Upgrading Ubuntu 18.04 kernel to latest version
From Activities -> ukuu
to start "Ubuntu Kernel Update Utility"```

Running Linux 4.15.0.66.75(ubuntu) ~ Linux 5.4.7 available

```

select Linux 5.3.7 v5.3.7 --> click [Install]

after finish
Booting previous kernels (warning window popup)
Screenshot_booting_previous_kernel.png
--> OK

Reboot Ubuntu 18.04

$ uname -r```

5.3.7-050307-generic

```

Wonderful;
Screen resolution 2560 x 1440 (16.9)

Regards
satimis

---

### Post by Dennis N on 2019-10-22
Glad to hear you got it working. The key was getting the latest kernel to support your graphics. Two questions:
1) Test 3 of post #12 with Ubuntu 19.10 apparently failed with 5.3 kernel - booting to dark screen. What was the problem there? How did you correct it?
2) In post #17, did you used the ppa to get that 5.3 in Ubuntu 19.04?

Prompted by your post, I just read this article on ukuu:
[https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)
Based on the information there, I think the best solution would be to use Ubuntu 19.10 where the kernel is fully supported. The wiki link there states this about mainline kernels:
"These kernels are not supported and are not appropriate for production use." That would concern me.

---

### Post by satimis on 2019-10-23
> **Dennis N said:**
> Two questions:
1) Test 3 of post #12 with Ubuntu 19.10 apparently failed with 5.3 kernel - booting to dark screen. What was the problem there? How did you correct it?

I just reinstalled it.  I suppose the first installation was not successful.  The WD 160G hdd is a very old stuff resting on the shelves for long time and also the 8G USB stick is an aged stuff

> 
2) In post #17, did you used the ppa to get that 5.3 in Ubuntu 19.04?
 No, it is the original kernel of the 19.10 ISO

> 
Prompted by your post, I just read this article on ukuu:
[https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu](https://www.omgubuntu.co.uk/2017/02/ukuu-easy-way-to-install-mainline-kernel-ubuntu)
Based on the information there, I think the best solution would be to use Ubuntu 19.10 where the kernel is fully supported. The wiki link there states this about mainline kernels:
"These kernels are not supported and are not appropriate for production use." That would concern me.
Thanks for your information.  I'm also reluctant to run 19.10 because I'll use it as host of VirtualBox.  Next April 20.04 will be out.

I'll perform another 2 tests later;

Test-1
Test Bashing-om's suggestion on Ubuntu 16.04

Test-2
Test Bashing-om's suggestion on Ubuntu 18.04

I'll come back after the tests, posting the test result here.

Furthermore I don't know whether my new PC will support 4K resolution?  I'm now starting shopping a 4K display and will know it afterwards.


satimis

---

### Post by satimis on 2019-10-23
Hi all,

Performed following tests according to the advice of Bashing-om on #14
[https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700](https://www.phoronix.com/scan.php?page=news_item&px=Ubuntu-19.10-Radeon-RX-5700)

Test-1
Install Ubuntu 16.04 desktop on WD160G hdd.  After Ubuntu 16.04 is up running.

On Terminal:-
$ uname -r```

4.15.0-66-generic

```

$ xrandr```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      76.00*

```

$ git clone git://git.kernel.org/pub/scm/linux/kernel/git/firmware/linux-firmware.git
$ cd linux-firmware/
$ sudo cp -va amdgpu/ /lib/firmware/
$ sudo update-initramfs -u

Installation went through without complaint
$ sudo reboot

Still the same screen resolution.

On Terminal
$ xrandr```

xrandr: Failed to get size of gamma for output default
Screen 0: minimum 1024 x 768, current 1024 x 768, maximum 1024 x 768
default connected primary 1024x768+0+0 0mm x 0mm
   1024x768      76.00*

```

$ uname -r```

4.15.0-66-generic

```


Test-2
Install Ubuntu 18.04 on WD160G hdd.  After Ubuntu 18.04 is up running.

To my surprise Ubuntu 18.04 works on;
CPU  AMD Ryzen 5 3400G YD3400CCPU BOX w/Cooler
Motherboard  ASUS PRIME X570-P/CSM X570,AM4 Socket,USB3.2,PCIe 4.0 M.2 ATX M/B

$ uname -r```

5.0.0-32-generic

```

$ xrandr```

Screen 0: minimum 320 x 200, current 2560 x 1440, maximum 16384 x 16384
HDMI-A-0 connected primary 2560x1440+0+0 (normal left inverted right x axis y axis) 553mm x 311mm
   2560x1440     59.95*+
   2048x1152     60.00  
   1920x1200     59.95  
   1920x1080     60.00    60.00    50.00    59.94    30.00    25.00    24.00    29.97    23.98  
   1600x1200     60.00  
   1680x1050     59.88  
   1280x1024     75.02    60.02  
   1440x900      59.95  
   1200x960      59.99  
   1280x800      59.95  
   1152x864      75.00  
   1280x720      60.00    50.00    59.94  
   1024x768      75.03    60.00  
   800x600       75.00    60.32  
   720x576       50.00  
   720x480       60.00    59.94  
   640x480       75.00    60.00    59.94  
   720x400       70.08  

```

Linux kernel 5.0v works on;```

CPU  AMD Ryzen 5 3400G YD3400CCPU BOX w/Cooler
Motherboard  ASUS PRIME X570-P/CSM X570,AM4 Socket,USB3.2,PCIe 4.0 M.2 ATX M/B

```

My only explanation is on previous test on #18 that Ubuntu 18.04 was upgraded from Ubuntu 16.04 and it retented the old kernel version.

My conclusion is;```

CPU  AMD Ryzen 5 3400G YD3400CCPU BOX w/Cooler
Motherboard  ASUS PRIME X570-P/CSM X570,AM4 Socket,USB3.2,PCIe 4.0 M.2 ATX M/B
```
support Linxu Kernel 5.0v

satimis

---

### Post by Dennis N on 2019-10-23
```
To my surprise Ubuntu 18.04 works on;
CPU AMD Ryzen 5 3400G YD3400CCPU BOX w/Cooler
Motherboard ASUS PRIME X570-P/CSM X570,AM4 Socket,USB3.2,PCIe 4.0 M.2 ATX M/B
$ uname -r
5.0.0-32-generic

```
Same kernel as I have. You must have installed a point release, later than 18.04 or 18.04.1. Then you get the more recent kernel.
```
dmn@Sydney:~$ inxi -S
System:    Host: Sydney Kernel: 5.0.0-31-generic x86_64 bits: 64
           Desktop: Gnome 3.28.4 Distro: **Ubuntu 18.04.3 LTS**

```
This motherboard is also Asus, but dating from 2014 (Intel H97 chipset).
Have fun with your new computer. Must be a relief to have everything working.
If I had your board, I would only use NVMe drives to take better advantage of the PCIe 4.0.

---

### Post by satimis on 2019-10-23
> **Dennis N said:**
>  - snip -
Must be a relief to have everything working.

I'm still struggling on font size of Ubuntu 18.04.  I prefer the font size of Ubuntu 16.04.

> 
If I had your board, I would only use NVMe drives to take better advantage of the PCIe 4.0.
I'm now looking at;
Kingston A2000 NVMe PCle SSD 1TB (SA2000M8/1000G)
[https://www.pcworld.com/article/3430765/kingston-a2000-nvme-ssd-fast-and-cheap-at-10-cents-per-gigabyte.html](https://www.pcworld.com/article/3430765/kingston-a2000-nvme-ssd-fast-and-cheap-at-10-cents-per-gigabyte.html)

Its price is acceptable.  2TB is little bid expensive.

satimis

---

### Post by satimis on 2019-10-24
Hi Dennis N,

Just found following 2 articles

1)
NVMe vs SATA: What's the difference and which is faster?
[https://www.microcontrollertips.com/why-nvme-ssds-are-faster-than-sata-ssds/](https://www.microcontrollertips.com/why-nvme-ssds-are-faster-than-sata-ssds/)

2)
Using an NVMe SSD with an HDD
[https://forums.tomshardware.com/threads/using-an-nvme-ssd-with-an-hdd.3296560/](https://forums.tomshardware.com/threads/using-an-nvme-ssd-with-an-hdd.3296560/)
May 16, 2018 #3
```

However...don't be automatically sucked into the "NVMe is OMG faster!" concept.
Yes, they are faster at some tasks. But not 10x faster than an SSD.

And in some uses, 0x faster.

```

satimis

---

### Post by Dennis N on 2019-10-24
You might like this "Explaining Computers" Video on NVMe SSD, SATA SSD,and HD drive speeds. He does some "real world" speed comparisons.
[https://youtu.be/kvHUVcgo8xY](https://youtu.be/kvHUVcgo8xY)

If you have a mixed system like mine with NVMe SSD and SATA SSDs, transferring data between the drives is going to be limited to the SATA speed. The only time I think you can get the fast NVMe speed is when you read and write just on the NVMe drive. My SATA SSD drive is also m.2 so that I can eliminate the power and data cables for all the SSDs. I have no HDDs, so no drive cables at all. 

The 2014 Asus board has just one m.2 slot, so I have to use it for the SATA SSD. The NVMe SSD is plugged into the PCIe 3 x 16 slot using an adapter card.

---

### Post by satimis on 2019-10-24
> **Dennis N said:**
> You might like this "Explaining Computers" Video on NVMe SSD, SATA SSD,and HD drive speeds. He does some "real world" speed comparisons.
[https://youtu.be/kvHUVcgo8xY](https://youtu.be/kvHUVcgo8xY)

If you have a mixed system like mine with NVMe SSD and SATA SSDs, transferring data between the drives is going to be limited to the SATA speed. The only time I think you can get the fast NVMe speed is when you read and write just on the NVMe drive. My SATA SSD drive is also m.2 so that I can eliminate the power and data cables for all the SSDs. I have no HDDs, so no drive cables at all. 

The 2014 Asus board has just one m.2 slot, so I have to use it for the SATA SSD. The NVMe SSD is plugged into the PCIe 3 x 16 slot using an adapter card.
Thanks for your link.  

This will be my first time using PCIe SSD drive.  I suppose I need a PCIe model for my ASUS PRIME X570-P motherboard (fitting into the PCIe slot) as demonstrated on below video;
The fastest SSD for gaming, and one big problem
[https://www.youtube.com/watch?v=ggIjr5Z0N10](https://www.youtube.com/watch?v=ggIjr5Z0N10)

If I'm wrong please advise me.

This PCIe SSD drive is solely running as host of VirtualBox VMs (about 30VMs), no communication with other drive.  There will be only 2 drives on this new PC, the PCIe SSD drive and a WD 4TB HDD which is solely for storage of old data, mainly text and pdf files and photos etc.

I found;
1)
ADATA 2TB XPG SX8200 Pro M.2 2280 ASX8200PNP-2TT-C 3D Nand PCIe Gen3 x4 NVMe 1.3 SSD
ADATA Expands XPG SX8200 Pro Range with 2TB Model
[https://www.anandtech.com/show/14732/adata-expands-xpg-sx8200-pro-range-with-2-tb-model](https://www.anandtech.com/show/14732/adata-expands-xpg-sx8200-pro-range-with-2-tb-model)

2)
Intel 2TB SSD 660p SSDPEKNW020T8X1 M.2 2280 3D2 QLC PCIe NVMe 3.0 x4 SSD
Intel SSD 660p Series
2.0TB, M.2 80mm PCIe 3.0 x4, 3D2, QLC
[https://ark.intel.com/content/www/us/en/ark/products/149403/intel-ssd-660p-series-2-0tb-m-2-80mm-pcie-3-0-x4-3d2-qlc.html](https://ark.intel.com/content/www/us/en/ark/products/149403/intel-ssd-660p-series-2-0tb-m-2-80mm-pcie-3-0-x4-3d2-qlc.html)

Their price is acceptable to me.  Upon receipt of your reply clarifying its mounting/interface I'll shop for them tomorrow.

Thanks in advance.

Regards
satimis

---

### Post by Dennis N on 2019-10-24
Consumer PCIe SSDs usually are sold as m.2 drives and plug into your m.2 connector to access the PCIe bus, A few, like the one in your first video, are larger and plug into a PCIe slot. Regardless of where they plug in, they all use the NVMe drive controller. You would want to get an PCIe NVMe m.2 drive since you have the m.2 connectors. Don't get a SATA m.2 drive! 

The Explaining Computers video showed the difference between PCIe 3.0 and PCIe 4.0 speeds. The second standard is twice as fast. Your board is PCIe 4.0 but supports PCIe 3.0 also (backward compatable). The example drives you link run at PCIe 3.0 speeds. A drive that can run at faster PCIe 4.0 speed is currently rather new and or course more expensive. New Egg currently only shows 23 such drives, but hundreds of PCIe 3.0 drives.

PCIe 3.0 x 4
second number is how many data lanes the drive uses. PCI 3.0 x 4 is theoretically twice as fast as PCI 3.0 x 2.

Watch this video a few times to get all this PCIe stuff straight:
[https://youtu.be/PrXwe21biJo](https://youtu.be/PrXwe21biJo)

---

### Post by satimis on 2019-10-25
Hi Dennis N,

I have following PCIe SSD purchased and installed on the new desktop PC.```

Intel 1TB SSD 660p SSDPEKNW010T8X1 M.2 2280 3D2 QLC PCIe NVMe 3.0 x4 SSD

```

The price of 1TB SSD PCIe NVMe 4.0 x4 is more than double that of PCIe NVMe 3.0 x4.  I'll wait until its price stable than I'll purchase a 2TB SSD PCIe NVMe 4.0 x4 package.

There are 2 kinds of interface;
1. M.2 SSD interface
How To Install M.2 SSD Installation | Intel 600p SSD & Maximus VIII Gene
[https://www.youtube.com/watch?v=NyTiEJ5psEY](https://www.youtube.com/watch?v=NyTiEJ5psEY)

2. HHHL cartridge interface
The fastest SSD for gaming, and one big problem
[https://www.youtube.com/watch?v=ggIjr5Z0N10](https://www.youtube.com/watch?v=ggIjr5Z0N10)

Both of them are on market and ASUS Prime X570-P motherboard takes both of them.  I got M.2 SSD interface.

Now Ubuntu 18.04 desktop is running on the 1TB PCIe 3.0 x4 SSD.  I have installed "gnome-tweak-tool" to fix small fonts problem.

Update motherboard BIOS:
I thinks folks on Ubuntu forum are more knowledgeable than the technical support of ASUS.  I asked them in writing whether I need to update the BIOS of my new motherboard.  If YES then HOW.  I'm now waiting for 2 days without a reply.

Actually I have all steps of updating motherboard BIOS on my database.  I expect to double confirm with them the steps avoiding making the PC unable to boot after updating BIOS.

Now the remaining work for me is to get a new 4K display to pair my new PC.  I am now targeting at;
DELL UP3216Q 32" 4K display;
Dell UltraSharp 32 Ultra HD 4K Monitor with PremierColor - UP3216Q
[https://www.dell.com/en-us/work/shop/dell-ultrasharp-32-ultra-hd-4k-monitor-with-premiercolor-up3216q/apd/210-afln/monitors-monitor-accessories](https://www.dell.com/en-us/work/shop/dell-ultrasharp-32-ultra-hd-4k-monitor-with-premiercolor-up3216q/apd/210-afln/monitors-monitor-accessories)

Its price is NOT cheaper.

Also I'm looking at
Dell UltraSharp 32 4K USB-C Monitor: U3219Q
[https://www.dell.com/en-us/shop/dell-ultrasharp-32-4k-usb-c-monitor-u3219q/apd/210-aqzz/monitors-monitor-accessories](https://www.dell.com/en-us/shop/dell-ultrasharp-32-4k-usb-c-monitor-u3219q/apd/210-aqzz/monitors-monitor-accessories)

The price of the latter is cheaper.

There is no urgency.  I'll make an intensive search first before purchaseing the new 32" 4K display.

I'll come back afterwards

Thanks

Regards
satimis

---

### Post by Dennis N on 2019-10-25
I think you will like the m.2 NVMe SSD. Asus has EZ Flash utility in UEFI setup for upgrading. That's what I used.

---

### Post by satimis on 2019-10-26
> **Dennis N said:**
> I think you will like the m.2 NVMe SSD. 
Yes, it is small in size.  When the price of 4.0 x4 NVMe SSD becomes stable I'll get a 2TB M.2 PCIe SSD.

> 
Asus has EZ Flash utility in UEFI setup for upgrading. That's what I used.
Whether you meant;
To Update the BIOS by USB as described in following article?
[Motherboard] ASUS EZ Flash 3 - Introduction
[https://www.asus.com/us/support/FAQ/1012815/](https://www.asus.com/us/support/FAQ/1012815/)

Current BIOS version of my ASUS motherboard;
$ sudo dmidecode -s bios-version```

0604

```

I already have the latest BIOS download on ASUS website and extracted;
[https://www.asus.com/hk-en/Motherboards/PRIME-X570-P/HelpDesk_BIOS/](https://www.asus.com/hk-en/Motherboards/PRIME-X570-P/HelpDesk_BIOS/)
Extracted file:
PRIME-X570-P-ASUS-1201.CAP

I'm now waiting for the reply from ASUS technical support to my question in writing in re of the steps upgrading BIOS.  It is already 3 days !!!

Regards
satimis

---

### Post by Dennis N on 2019-10-26
> I already have the latest BIOS download on ASUS website and extracted;
[https://www.asus.com/hk-en/Motherboa...HelpDesk_BIOS/](https://www.asus.com/hk-en/Motherboa...HelpDesk_BIOS/)
Extracted file:
PRIME-X570-P-ASUS-1201.CAP
This is from my notes for BIOS upgrade method if you want to give it a try:
------------------------------------------------------------------------
I downloaded the bios file from Asus support. It is a zip file, and you need to save the extracted CAP file to an FAT32 drive with one partition. I started from cold start, F2 to enter bios, plugged in the flash drive. F7 to Advanced Mode, then to Tools. Start EZ Flash tool, and follow the onscreen directions. 

When it was done, the system rebooted, and I was asked to select and read the file again to complete the process. I did so, fixed the boot order, turned off fast boot, selected Other OS to turn off secure boot, saved and exited. My grub menu booted up. Later, I had to go back and re-enable kvm (vt-x) in the cpu tab or else my virtual machine wouldn't work.
--------------------------------------------------------------------------
Support Article I think I used:
[https://www.asus.com/us/support/FAQ/1012815/](https://www.asus.com/us/support/FAQ/1012815/)

---

### Post by satimis on 2019-10-30
> **Dennis N said:**
> This is from my notes for BIOS upgrade method if you want to give it a try:
------------------------------------------------------------------------
I downloaded the bios file from Asus support. It is a zip file, and you need to save the extracted CAP file to an FAT32 drive with one partition. I started from cold start, F2 to enter bios, plugged in the flash drive. F7 to Advanced Mode, then to Tools. Start EZ Flash tool, and follow the onscreen directions. 

When it was done, the system rebooted, and I was asked to select and read the file again to complete the process. I did so, fixed the boot order, turned off fast boot, selected Other OS to turn off secure boot, saved and exited. My grub menu booted up. Later, I had to go back and re-enable kvm (vt-x) in the cpu tab or else my virtual machine wouldn't work.
--------------------------------------------------------------------------
Support Article I think I used:
[https://www.asus.com/us/support/FAQ/1012815/](https://www.asus.com/us/support/FAQ/1012815/)
Hi  Dennis N,

Performed BIOS update as follows;

1)
Download the latest BIOS of ASUS motherboard PRIME X570-P on ASUS Website and depress the file as;
PRIME-X570-P-ASUS-1201.CAP

2)
Format an USB stick as FAT32 and copy "PRIME-X570-P-ASUS-1201.CAP" on it.

3)
Follow the steps on your link;
[Motherboard] ASUS EZ Flash 3 - Introduction
[https://www.asus.com/us/support/FAQ/1012815/](https://www.asus.com/us/support/FAQ/1012815/)

to perform BIOS update.  It went through without problem.  The update time took about 4 minutes to complete as indicated on the "Progressing" bar.

4)
After finished the computer rebooted automatically.  It took a while with the warning popup;```

Don't turn off or reset the computer ......

```

I have to mention here that the computer was switched off automatically finally.  I haven't touched any key.  The computer was on without disconnected from electricity supply.

Then I have to switch OFF/ON the main and booted the computer again
======================================================

5)
Finally the computer booted up and started Ubuntu 18.04 desktop.

6) 
On Terminal ran;
$ sudo dmidecode | less > bios_20191030.txt ```

# dmidecode 3.1
Getting SMBIOS data from sysfs.
SMBIOS 3.2.0 present.
# SMBIOS implementations newer than version 3.1.1 are not
# fully supported by this version of dmidecode.
Table at 0xDA3E8000.

Handle 0x0000, DMI type 0, 26 bytes
BIOS Information
	Vendor: American Megatrends Inc.
	Version: 1201
	Release Date: 09/09/2019
	Address: 0xF0000
	Runtime Size: 64 kB
	ROM Size: 16 MB
	Characteristics:
		PCI is supported
		APM is supported
		BIOS is upgradeable
		BIOS shadowing is allowed
		Boot from CD is supported
		Selectable boot is supported
		BIOS ROM is socketed
		EDD is supported
		5.25"/1.2 MB floppy services are supported (int 13h)
		3.5"/720 kB floppy services are supported (int 13h)
		3.5"/2.88 MB floppy services are supported (int 13h)
		Print screen service is supported (int 5h)
		8042 keyboard services are supported (int 9h)
		Serial services are supported (int 14h)
		Printer services are supported (int 17h)
		ACPI is supported
		USB legacy is supported
		BIOS boot specification is supported
		Targeted content distribution is supported
		UEFI is supported
	BIOS Revision: 5.14

Handle 0x0001, DMI type 1, 27 bytes
System Information
	Manufacturer: System manufacturer
	Product Name: System Product Name
	Version: System Version
	Serial Number: System Serial Number
	UUID: 1CF18EF1-8664-F6CA-F79F-04D9F57D0E40
	Wake-up Type: Power Switch
	SKU Number: SKU
	Family: To be filled by O.E.M.

Handle 0x0002, DMI type 2, 15 bytes
Base Board Information
	Manufacturer: ASUSTeK COMPUTER INC.
	Product Name: PRIME X570-P
	Version: Rev X.0x
	Serial Number: 190753869002923
	Asset Tag: Default string
	Features:
		Board is a hosting board
		Board is replaceable
	Location In Chassis: Default string
	Chassis Handle: 0x0003
	Type: Motherboard
	Contained Object Handles: 0

Handle 0x0003, DMI type 3, 22 bytes
Chassis Information
	Manufacturer: Default string
	Type: Desktop
	Lock: Not Present
	Version: Default string
	Serial Number: Default string
	Asset Tag: Default string
	Boot-up State: Safe
	Power Supply State: Safe
	Thermal State: Safe
	Security Status: None
	OEM Information: 0x00000000
	Height: Unspecified
	Number Of Power Cords: 1
	Contained Elements: 0
	SKU Number: Default string
...... 
```


Lot of thanks for your help.

The remaining work for me is to purchase a 4K >32" display.

I have read several online documents;
- Go curved or flat display.
- Comparing different model and makers, such as Dell, Asus, Samsung, ViewSonic etc.
- Paying more for a height adjustment model ?
etc.

My preference is a 40" 4K display but I couldn't sort out the problem of the overhead cabinet on my desk.

I'll come back afterwards.

Remark:
Up to now I haven't received any reply from ASUS Technical Support re steps of update BIOS concerned.

Regards
satimis

---

