---
title: "Ubuntu 7.04 Install on Dell Inspiron 1520, EVERYTHING has gone wrong"
date: 2007-07-20
forum: Installation &amp; Upgrades
---

### Post by sting14ray on 2007-07-20
I've been trying to install Ubuntu on my Dell Inspiron 1520 laptop, and I'm getting boatloads of errors.  I used the text based install for 7.04 because the standard wasn't working (X11 and video cards errors), and now I can login to the system with the vesa drivers. :(

I would like to:
Increase the resolution of the display (1024 x 768 x 16 bit)
Get my ethernet card and wireless card working
      Be able to access the internet
Have it be able to view my DVD-RW (at least read if not write)


The system currently dual boots into Vista also, and I found ltools for if I need to copy files from my working Vista to Ubuntu.

This is my second day working with linux, so please bear my noobness.
I first tried to get my nics working and found the how-to on the forums, however, I keep getting errors that are due to the build-essential package not being installed apparently (what I've gathered from the other forums).  Using either the terminal or Synaptic, I'm prompted to insert the installation CD, but that doesn't work either because the optical drive can't be mounted.
For the CD, I'm getting the "unable to mount the selected volume; /dev/hdc are unavailable".

My setup:
Core 2 Duo T7300 (2.0 Ghz, 4 MB)
2 GB Ram
120 GB Hard Disk
Dell 1390 Wireless Card (Broadcomm)
Integrated Ethernet (also Broadcomm I think)
Nvidia 8400M GS (128 MB)

Any help would definitely be appreciated,  #-o

Thanks.

---

### Post by Rocket2DMn on 2007-07-20
please post the outputs of
```
sudo fdisk -l > fdisk_output.txt
``` (note that is a lowercase L, not a 1 [one])
and
```
lspci > lspci_output.txt
```
These will save the outputs of those commands to text files, you can transfer them to your internet computer with a floppy disk or USB flash drive, then post them here.  They will probably be in your $HOME folder, type "pwd" in terminal to get your current location on the drive.

---

### Post by Pumalite on 2007-07-20
Deleted.

---

### Post by sting14ray on 2007-07-20
The lspci output:
 > 00:00.0 Host bridge: Intel Corporation Mobile Memory Controller Hub (rev 0c)
00:01.0 PCI bridge: Intel Corporation Mobile PCI Express Root Port (rev 0c)
00:1a.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #4 (rev 02)
00:1a.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #5 (rev 02)
00:1a.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #2 (rev 02)
00:1b.0 Audio device: Intel Corporation 82801H (ICH8 Family) HD Audio Controller (rev 02)
00:1c.0 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 1 (rev 02)
00:1c.1 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 2 (rev 02)
00:1c.3 PCI bridge: Intel Corporation 82801H (ICH8 Family) PCI Express Port 4 (rev 02)
00:1d.0 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #1 (rev 02)
00:1d.1 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #2 (rev 02)
00:1d.2 USB Controller: Intel Corporation 82801H (ICH8 Family) USB UHCI #3 (rev 02)
00:1d.7 USB Controller: Intel Corporation 82801H (ICH8 Family) USB2 EHCI #1 (rev 02)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev f2)
00:1f.0 ISA bridge: Intel Corporation Mobile LPC Interface Controller (rev 02)
00:1f.1 IDE interface: Intel Corporation Mobile IDE Controller (rev 02)
00:1f.2 SATA controller: Intel Corporation Mobile SATA AHCI Controller (rev 02)
00:1f.3 SMBus: Intel Corporation 82801H (ICH8 Family) SMBus Controller (rev 02)
01:00.0 VGA compatible controller: nVidia Corporation Unknown device 0427 (rev a1)
03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
03:01.0 FireWire (IEEE 1394): Ricoh Co Ltd Unknown device 0832 (rev 05)
03:01.1 Generic system peripheral [0805]: Ricoh Co Ltd R5C822 SD/SDIO/MMC/MS/MSPro Host Adapter (rev 22)
03:01.2 System peripheral: Ricoh Co Ltd Unknown device 0843 (rev 12)
03:01.3 System peripheral: Ricoh Co Ltd R5C592 Memory Stick Bus Host Adapter (rev 12)
03:01.4 System peripheral: Ricoh Co Ltd xD-Picture Card Controller (rev 12)
0c:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01)



And the fdisk output:

> 
Disk /dev/sda: 120.0 GB, 120034123776 bytes
255 heads, 63 sectors/track, 14593 cylinders
Units = cylinders of 16065 * 512 = 8225280 bytes

   Device Boot      Start         End      Blocks   Id  System
/dev/sda1               1          11       88326   de  Dell Utility
/dev/sda2              12        1317    10485760    7  HPFS/NTFS
/dev/sda3   *        1317        9805    68183040    7  HPFS/NTFS
/dev/sda4            9806       14594    38460635    f  W95 Ext'd (LBA)
/dev/sda5           14267       14594     2620416   dd  Unknown
/dev/sda6   *        9806       14078    34322841   83  Linux
/dev/sda7           14079       14266     1510078+  82  Linux swap / Solaris

Partition table entries are not in disk order


Thank You

---

### Post by Rocket2DMn on 2007-07-20
> 03:00.0 Ethernet controller: Broadcom Corporation BCM4401-B0 100Base-TX (rev 02)
0c:00.0 Network controller: Broadcom Corporation Dell Wireless 1390 WLAN Mini-PCI Card (rev 01) 
looks like your LAN card and Wireless are detected.  They may just need to be enabled.

To get your resolution fixed, have you tried
```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo dpkg-reconfigure xserver-xorg
```
this wil take you through a setup of hardware, please read, don't just enter your way through.  When you get to the resolutions page, use TAB to move through the options and use SPACEBAR to select your monitor's max resolution and everything less than that.  You will then restart the Xserver (the GUI) by doing CTRL+ALT+BACKSPACE.  After you login again, you can select the correct resolution from System->Preferences->Resolution (or Screen Resolution - I'm not in front of my Ubuntu box to check).

Sadly, I don't see your DVD drive there, but we might get to that once internet is established.  What have you tried to get your ethernet and wireless working?

---

### Post by sting14ray on 2007-07-20
I went through the xserver configuration utility, and it gave error messages about the server failing to start, so I just copied the xorg.conf.backup back to xorg.conf and I'm back at 1024x768 (monitor supports 1440x900).  I'm pretty sure this is a driver error and it requires either the Envy package (which I can't install) or the new Nvidia G86 family drivers.  

I went through the how-to at [http://ubuntuforums.org/showthread.php?t=297092&](http://ubuntuforums.org/showthread.php?t=297092&) for the ethernet and wireless.  Unfortunately I can't get build-essentials and so can't install/compile???  ndiswrapper.  If it's just a matter of enabling them, how would I do that?

Thanks

---

### Post by Rocket2DMn on 2007-07-20
You can always download packages onto your PC with internet and transfer them to your Ubuntu PC with a flash drive:
[http://packages.ubuntu.com/feisty/devel/build-essential](http://packages.ubuntu.com/feisty/devel/build-essential)
And so on and so forth.
Good luck

---

### Post by Pumalite on 2007-07-20
If you could 'plug' into a LAN somewhere, you could then to to System>Administration>Software Sources and untick the CD as a source. You could then try the Terminal again or Synaptic, making sure you have all other sources checked.

---

### Post by sting14ray on 2007-07-20
I copied over the new build-essentials and tried using dpkg -i on it, it gave me dependency errors so I"m going to dl and copy those over and install those first.  I also tried using the lan and it gave me dhcp errors, so I have to either enable/install drivers for that too.  But as for now, I'm going to leave work and try to enjoy my fri. night and maybe get some food.

Thanks again to everyone for their time.  I'll post again if these steps don't work.  Still have no idea what to do about my optical drive.

Thanks

---

### Post by alex1974 on 2007-08-03
Got my Inspiron 1520 three days ago and went through a guide at [http://ubuntuforums.org/index.php?t=501195&pp=75](http://ubuntuforums.org/index.php?t=501195&pp=75)
So far everything seems to work but wlan.

For the optical drive try 

[COLOR="SlateGray"]sudo gedit /etc/modules
[/COLOR]
and add the following line:

[COLOR="SlateGray"]piix[/COLOR]

worked for me. I didn't changed DMA and I/O settings as proposed.
For the wlan. Has someone a solution?
Lan and wlan card are detected. The signal is at 100% but still no connection.
iwconfig eth1 shows:
eth1  IEEE 802. 11g ESSID: "xxxx"
           Mode:Managed Frequency:......
           ....
it seems to work
How to enable it?

Thanks,
Alex

---

