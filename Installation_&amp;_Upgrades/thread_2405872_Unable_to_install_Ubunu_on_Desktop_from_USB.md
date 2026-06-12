---
title: "Unable to install Ubunu on Desktop from USB"
date: 2018-11-12
forum: Installation &amp; Upgrades
---

### Post by praywwjd2004 on 2018-11-12
I am using a USB to try and install Ubuntu on my desktop. I have already wiped the hard drive using DBan. I am able to boot from usb and get to the install screen. However when I go thru the steps to install Ubuntu it says that it requires 8.6GB of storage and that I only have 7.6GB of storage. That means that it is not seeing my 1TB internal Harddrive it is only seeing the 8GB usb drive that I am using to try and install from. I am able to go back and use the other option to try Ubuntu before installing it and that works just fine.

Any idea why it is not seeing my 1TB internal Hard drive that I just wiped?
What troubleshooting steps can I try?

I am using a Gateway desktop model # SX2840-01.

---

### Post by mitesh.agrwl on 2018-11-12
Hi,

Please run the command **inxi -Fz** and paste the output here.

---

### Post by praywwjd2004 on 2018-11-12
I tried running the command but received the following output:


ubuntu@ubuntu:~$ inxi -Fz

Command 'inxi' not found, but can be installed with:

sudo apt install inxi

---

### Post by praywwjd2004 on 2018-11-12
[INDENT] 					I tried running the command but received the following output:


ubuntu@ubuntu:~$ inxi -Fz

Command 'inxi' not found, but can be installed with:

sudo apt install inxi 				[/INDENT] 			
  			   		
 			 			 			 				 					


I tried a few different ways to install inxi but buth was unsuccessful see below:

sudo apt install inxi

ubuntu@ubuntu:~$ apt-get install inxi 
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?


Also:

ubuntu@ubuntu:~$ apt-cache search inxi 
ubuntu@ubuntu:~$ sudo apt-add-repository ppa:unit193/inxi && apt-get update
 inxi :: a full featured system information script

inxi is a fork of infobash 3.02, the bash sys info script by locsmif

    inxi, the universal, portable, system info script for irc.
    Tested with Irssi, Xchat, Konversation, BitchX, KSirc, ircII,
    Quassel, Gaim/Pidgin, Weechat, KVIrc and Kopete.
    Original infobash author and copyright holder:
    Copyright (C) 2005-2007 Michiel de Boer a.k.a. locsmif
    inxi version: Copyright (C) 2008-9 Scott Rogers & Harald Hope
    Further fixes (listed as known): Horst Tritremmel <hjt at sidux.com>
    Steven Barrett (aka: damentz) - usb audio patch; swap percent used patch
 More info: [https://launchpad.net/~unit193/+archive/ubuntu/inxi](https://launchpad.net/~unit193/+archive/ubuntu/inxi)
Press [ENTER] to continue or Ctrl-c to cancel adding it.

Ign:1 cdrom://Ubuntu 18.10 _Cosmic Cuttlefish_ - Release amd64 (20181017.3) cosmic InRelease
Hit:2 cdrom://Ubuntu 18.10 _Cosmic Cuttlefish_ - Release amd64 (20181017.3) cosmic Release
Hit:4 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic InRelease       
Hit:5 [http://archive.ubuntu.com/ubuntu](http://archive.ubuntu.com/ubuntu) cosmic-updates InRelease
Hit:6 [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) cosmic-security InRelease              
Get:7 [http://ppa.launchpad.net/unit193/inxi/ubuntu](http://ppa.launchpad.net/unit193/inxi/ubuntu) cosmic InRelease [15.4 kB]  
Ign:8 [http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04](http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04)  InRelease
Get:9 [http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04](http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04)  Release [996 B]
Get:10 [http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04](http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04)  Release.gpg [189 B]
Get:11 [http://ppa.launchpad.net/unit193/inxi/ubuntu](http://ppa.launchpad.net/unit193/inxi/ubuntu) cosmic/main amd64 Packages [616 B]
Ign:10 [http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04](http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04)  Release.gpg
Get:12 [http://ppa.launchpad.net/unit193/inxi/ubuntu](http://ppa.launchpad.net/unit193/inxi/ubuntu) cosmic/main Translation-en [308 B]
Reading package lists... Done                                                  
W: GPG error: [http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04](http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04)  Release: The following signatures were invalid: 449A7266E28E147F438E5B57A41001039EC56A71
E: The repository 'http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04  Release' is not signed.
N: Updating from such a repository can't be done securely, and is therefore disabled by default.
N: See apt-secure(8) manpage for repository creation and user configuration details.
ubuntu@ubuntu:~$ echo 'deb [http://ppa.launchpad.net/unit193/inxi/ubuntu](http://ppa.launchpad.net/unit193/inxi/ubuntu) trusty main' > /etc/apt/sources
bash: /etc/apt/sources: Permission denied


Do you have any other suggestions?

---

### Post by praywwjd2004 on 2018-11-12
I am currently in Live Ubuntu, I opened Terminal [ctrl+alt+T], and ran the following commands:
sudo parted -l
sudo fdisk -l

Here is the output:

ubuntu@ubuntu:~$ sudo parted -l
Model:   (scsi)
Disk /dev/sda: 7812MB
Sector size (logical/physical): 512B/512B
Partition Table: msdos
Disk Flags: 

Number  Start   End     Size    Type     File system  Flags
 1      1049kB  7812MB  7811MB  primary  fat32        boot, lba


ubuntu@ubuntu:~$ sudo fdisk -l
Disk /dev/loop0: 1.8 GiB, 1905549312 bytes, 3721776 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop1: 87.9 MiB, 92123136 bytes, 179928 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop2: 140.9 MiB, 147722240 bytes, 288520 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop3: 2.3 MiB, 2355200 bytes, 4600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop4: 13 MiB, 13619200 bytes, 26600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop5: 14.5 MiB, 15208448 bytes, 29704 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop6: 3.7 MiB, 3878912 bytes, 7576 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes


Disk /dev/loop7: 42.1 MiB, 44183552 bytes, 86296 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes




Disk /dev/sda: 7.3 GiB, 7811891200 bytes, 15257600 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: dos
Disk identifier: 0x2b549395

Device     Boot Start      End  Sectors  Size Id Type
/dev/sda1  *     2048 15257599 15255552  7.3G  c W95 FAT32 (LBA)


This shows that it is not seeing my Internal 1TB WD hard drive. What do I need to do to have the have drive recognized?

---

### Post by mitesh.agrwl on 2018-11-12
Hi,

> ubuntu@ubuntu:~$ apt-get install inxi 
E: Could not open lock file /var/lib/dpkg/lock-frontend - open (13: Permission denied)
E: Unable to acquire the dpkg frontend lock (/var/lib/dpkg/lock-frontend), are you root?


This error may be due to another process/daemon running which have locked the database.

> Ign:8 [http://download.opensuse.org/reposit...h/Ubuntu_17.04]("http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04")  InRelease
Get:9 [http://download.opensuse.org/reposit...h/Ubuntu_17.04]("http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04")  Release [996 B]
Get:10 [http://download.opensuse.org/reposit...h/Ubuntu_17.04]("http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04")  Release.gpg [189 B]
Get:11 [http://ppa.launchpad.net/unit193/inxi/ubuntu](http://ppa.launchpad.net/unit193/inxi/ubuntu) cosmic/main amd64 Packages [616 B]
Ign:10 [http://download.opensuse.org/reposit...h/Ubuntu_17.04]("http://download.opensuse.org/repositories/home:/alex_sh/Ubuntu_17.04")  Release.gpg
Get:12 [http://ppa.launchpad.net/unit193/inxi/ubuntu](http://ppa.launchpad.net/unit193/inxi/ubuntu) cosmic/main Translation-en [308 B]]

The repositories are from an old release, which may not be good and should be avoided.

Anyway you can use the command **sudo lshw** **-class storage **and paste the output.

---

### Post by praywwjd2004 on 2018-11-12
Thanks, here is the output:

ubuntu@ubuntu:~$ sudo lshw -class storage
  *-storage                 
       description: SATA controller
       product: 5 Series/3400 Series Chipset 6 port SATA AHCI Controller
       vendor: Intel Corporation
       physical id: 1f.2
       bus info: pci@0000:00:1f.2
       version: 06
       width: 32 bits
       clock: 66MHz
       capabilities: storage msi pm ahci_1.0 bus_master cap_list
       configuration: driver=ahci latency=0
       resources: irq:31 ioport:d800(size=8) ioport:d480(size=4) ioport:d400(size=8) ioport:d080(size=4) ioport:d000(size=32) memory:fbeee000-fbeee7ff
  *-scsi:0
       physical id: 1
       logical name: scsi0
       capabilities: emulated
  *-scsi:1
       physical id: 2
       bus info: usb@1:1.1
       logical name: scsi6
       capabilities: emulated scsi-host
       configuration: driver=usb-storage
  *-scsi:2
       physical id: 3
       bus info: usb@1:1.5
       logical name: scsi7
       capabilities: emulated scsi-host
       configuration: driver=usb-storage

---

### Post by mitesh.agrwl on 2018-11-12
Hi,

Sorry, little mistake, please check that the code  **sudo lshw -class disk **shows the details of your hard disk, if yes, paste the output and wait for some more experienced use to diagnose the issue. 

Have doubt, is it possible that DBan might have corrupted the hard disk.

---

### Post by praywwjd2004 on 2018-11-12
Here is the Output:

ubuntu@ubuntu:~$ sudo lshw -class disk
  *-cdrom                   
       description: DVD-RAM writer
       product: DVD A  DH16AASH
       vendor: ATAPI
       physical id: 0.0.0
       bus info: scsi@0:0.0.0
       logical name: /dev/cdrom
       logical name: /dev/cdrw
       logical name: /dev/dvd
       logical name: /dev/dvdrw
       logical name: /dev/sr0
       version: SA15
       capabilities: removable audio cd-r cd-rw dvd dvd-r dvd-ram
       configuration: ansiversion=5 status=nodisc
  *-disk
       description: SCSI Disk
       physical id: 0.0.0
       bus info: scsi@6:0.0.0
       logical name: /dev/sda
       version: 8.07
       serial: 1
       size: 7450MiB (7811MB)
       capabilities: removable
       configuration: ansiversion=4 logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sda
          size: 7450MiB (7811MB)
          capabilities: partitioned partitioned:dos
          configuration: signature=2b549395
  *-disk:0
       description: SCSI Disk
       product: Compact Flash
       vendor: Generic-
       physical id: 0.0.0
       bus info: scsi@7:0.0.0
       logical name: /dev/sdb
       version: 1.01
       capabilities: removable
       configuration: logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdb
  *-disk:1
       description: SCSI Disk
       product: Flash Reader
       vendor: Multiple
       physical id: 0.0.1
       bus info: scsi@7:0.0.1
       logical name: /dev/sdc
       version: 1.05
       capabilities: removable
       configuration: logicalsectorsize=512 sectorsize=512
     *-medium
          physical id: 0
          logical name: /dev/sdc


How can I check to see if the hard disc is corrupted after I wiped it with DBan?

---

### Post by 23dornot23d on 2018-11-12
When you was trying to install inxi ............ you did not put sudo in front of it that was all that looked to be wrong there.

ubuntu@ubuntu:~$ apt-get install inxi 

try

[B]sudo apt-get install inxi

[/B]then[B]

inxi -F
[/B]
I watched the video on the tool you used to delete the disk ..... [https://youtu.be/sHB2gDFBvCU](https://youtu.be/sHB2gDFBvCU)

Would **gparted** not have been good enough ....... which may be needed somewhere down the line ..... as I am not sure
but you probably need a partition table and information for that drive again.

**gparted** would do that - but maybe someone else could give you some more advice when you get to that point ...... hopefully.

Hope everything goes well for you .......

---

### Post by mitesh.agrwl on 2018-11-12
Hi [**[COLOR=#000000]23dornot23d[/COLOR]**]("https://ubuntuforums.org/member.php?u=953253"),

> as I am not sure
but you probably need a partition table and information for that drive again.

As the disk is not found in lshw, it is doubtful that gparted could help! Please check it.

---

### Post by praywwjd2004 on 2018-11-12
Thank you 23dornot23d that worked to install and here is the output of [B]inxi -F:

ubuntu@ubuntu:~$ inxi -F
System:
  Host: ubuntu Kernel: 4.18.0-10-generic x86_64 bits: 64 
  Desktop: Gnome 3.30.1 Distro: Ubuntu 18.10 (Cosmic Cuttlefish) 
Machine:
  Type: Desktop System: Gateway product: SX2840 v: N/A 
  serial: <root required> 
  Mobo: Gateway model: FIH57 serial: <root required> 
  BIOS: American Megatrends v: P01-B0 date: 01/20/2010 
CPU:
  Topology: Dual Core model: Intel Core i3 530 bits: 64 type: MT MCP 
  L2 cache: 4096 KiB 
  Speed: 1374 MHz min/max: 1200/2933 MHz Core speeds (MHz): 1: 1361 2: 1353 
  3: 1308 4: 1328 
Graphics:
  Device-1: Intel Core Processor Integrated Graphics driver: i915 v: kernel 
  Display: x11 server: X.Org 1.20.1 driver: modesetting unloaded: fbdev,vesa 
  resolution: 1600x900~60Hz 
  Message: Unable to show advanced data. Required tool glxinfo missing. 
Audio:
  Device-1: Intel 5 Series/3400 Series High Definition Audio 
  driver: snd_hda_intel 
  Sound Server: ALSA v: k4.18.0-10-generic 
Network:
  Device-1: Intel 82578DC Gigabit Network driver: e1000e 
  IF: enp0s25 state: up speed: 100 Mbps duplex: full mac: 90:fb:a6:86:b0:80 
Drives:
  Local Storage: total: 7.28 GiB used: 2.41 GiB (33.2%) 
  ID-1: /dev/sda type: USB model: 058f 6387 size: 7.28 GiB 
Partition:
  ID-1: / size: 2.78 GiB used: 565.7 MiB (19.9%) fs: overlay source: ERR-102 
Sensors:
  Missing: Required tool sensors not installed. Check --recommends 
Info:
  Processes: 216 Uptime: 2h 45m Memory: 5.56 GiB used: 1.50 GiB (27.0%) 
  Shell: bash inxi: 3.0.27



I was not aware of Gparted when I used DBan. I wonder if I could use Gparted now and if it would still partion?
[/B]

---

### Post by ajgreeny on 2018-11-12
If you used dban on the 1TB disk it will have wiped everything from it, including the partition table, without which there is nothing the installer can install to; no partition table so no partitions and no ability of the installer to create partitions.

Use gparted Device -> Create Partition Table, and there use either GPT or msdos table to create a new PT, after which you will be able to create new partitions.

---

### Post by praywwjd2004 on 2018-11-12
> **ajgreeny said:**
> If you used dban on the 1TB disk it will have wiped everything from it, including the partition table, without which there is nothing the installer can install to; no partition table so no partitions and no ability of the installer to create partitions.

Use gparted Device -> Create Partition Table, and there use either GPT or msdos table to create a new PT, after which you will be able to create new partitions.


I am trying to use gparted now but it is only seeing the flash drive as well. I am not very familiar with gparted so I don't if there are different options in there that would allow it to see the 1TB hard drive.

---

### Post by 23dornot23d on 2018-11-12
mmm ..........

> 
I am trying to use gparted now but it is only seeing the flash drive as  well. I am not very familiar with gparted so I don't if there are  different options in there that would allow it to see the 1TB hard  drive. 				


Just one question ........ is it seen from BIOS ............ the computers Basic Input Output System at the start when your computer first boots up.

You can usually get to this by pressing and sometimes holding down the escape key as it boots up ..........

Often with new drives you have to go into the BIOS and just set it so it knows the drive is there ..... maybe it needs some information about that

drive ............. in the olden days we used to have to enter it by hand ........... but I guess nowadays its automated and probably picks it up 

from the disk drive - presuming it can still get to that information.

Sorry for butting in ........ but thought this may help a little .....

Otherwise it may need some research ......... just a thought ........

---

### Post by praywwjd2004 on 2018-11-12
> **23dornot23d said:**
> mmm ..........



Just one question ........ is it seen from BIOS ............ the computers Basic Input Output System at the start when your computer first boots up.

You can usually get to this by pressing and sometimes holding down the escape key as it boots up ..........

Often with new drives you have to go into the BIOS and just set it so it knows the drive is there ..... maybe it needs some information about that

drive ............. in the olden days we used to have to enter it by hand ........... but I guess nowadays its automated and probably picks it up 

from the disk drive - presuming it can still get to that information.

Sorry for butting in ........ but thought this may help a little .....

Otherwise it may need some research ......... just a thought ........


I just checked and no the 1TB WD hard drive is not showing in the BIOS.

---

### Post by 23dornot23d on 2018-11-12
Does the BIOS have a search option for the drive - or a manual option to input information relative to a new drive being fitted .........

If not you may need to take it into somewhere that can reset it up for you ...... if that is possible ........

Unless anyone on here has any other ideas .........

I often take hard drives in and out of my laptop - but they always seem to pick up ok .......... the different sizes etc.

Yours is a desktop system from inxi above .....

[https://www.cnet.com/products/gateway-sx2840-01/specs/](https://www.cnet.com/products/gateway-sx2840-01/specs/)

On desktop systems nowadays - do they automatically detect the drives ...... and if so - would it need taking out and putting in again.
this is a question to anyone that is experienced with building or setting up new computers.

Otherwise my only advice would be to take it to a specialist ....... to sort it out .........

Can say no more as I do not know how the drive would be initially picked up in the machine from new .......

---

### Post by praywwjd2004 on 2018-11-12
I think I am going to try removing the hard drive and installing it in a different desktop to see if it will recognize it.

---

### Post by praywwjd2004 on 2018-11-12
> **praywwjd2004 said:**
> I think I am going to try removing the hard drive and installing it in a different desktop to see if it will recognize it.


That is not going to work. The way this HP desktop was assembled it is virtually impossible to get to the hard drive. I cannot remove the hard drive I was just barely able to reach the connecting wires to unplug it and plug it back in. 


if I use a larger usb drive can I just install Ubuntu on that and use it that way for now?

---

### Post by 23dornot23d on 2018-11-12
Adding a larger USB drive should work ....... its the way I often run my laptop ..... as long as the bios can be set to boot from it .........
then it automatically picks up on any usb drive I use ....... 

1 terrabyte hard drives can be a pain sometimes as they seem to need a tad longer to spin up - so do not always get recognised first boot .......

500 gig ones work very well - pick up first time on my own machine ...... there are a few types - some need a separate electrical connection
and others just plug in and away you go.

or are you talking of something smaller like a 32gig ...... as I use those too but in a external USB card reader
* check which yours is USB 2 or USB 3 ........... just a thought ( will not on mine boot from the internal card reader in the laptop though)

---

### Post by mitesh.agrwl on 2018-11-12
I am using 16 gb Sandisk Cruzer Blade for past one year, after my hard disk failed. Though it can not hold much data, do not need to do so, thanks to online services and a portable backup, but it is serving good.

Sometimes the system hangs, but it might be due to various reasons also, the system is too old. Could not figure out the problem myself, hoping to get the support from forum, but too much details or zip file might have raised a red flag!

---

### Post by praywwjd2004 on 2018-11-12
> **23dornot23d said:**
> Adding a larger USB drive should work ....... its the way I often run my laptop ..... as long as the bios can be set to boot from it .........
then it automatically picks up on any usb drive I use ....... 

1 terrabyte hard drives can be a pain sometimes as they seem to need a tad longer to spin up - so do not always get recognised first boot .......

500 gig ones work very well - pick up first time on my own machine ...... there are a few types - some need a separate electrical connection
and others just plug in and away you go.

or are you talking of something smaller like a 32gig ...... as I use those too but in a external USB card reader
* check which yours is USB 2 or USB 3 ........... just a thought ( will not on mine boot from the internal card reader in the laptop though)



Yes I am talking about a 16 GB portable Flash drive to install Ubuntu on then I will connect a 4TB external backup drive to save files on.

---

### Post by praywwjd2004 on 2018-11-12
> **mitesh.agrwl said:**
> I am using 16 gb Sandisk Cruzer Blade for past one year, after my hard disk failed. Though it can not hold much data, do not need to do so, thanks to online services and a portable backup, but it is serving good.

Sometimes the system hangs, but it might be due to various reasons also, the system is too old. Could not figure out the problem myself, hoping to get the support from forum, but too much details or zip file might have raised a red flag!


When I try to install Ubuntu on the 16GB flash drive I get the message: No root file system is defined
Please correct this from the partitioning menu.

Do I need to partition the flash drive before I can install Ubuntu on it?
If so how should I do that?

---

### Post by 23dornot23d on 2018-11-12
The root partition is defined by a /

The install should allow you to format the USB 16gig and create a root partition .........

I do not bother with a swap file but usually just leave some space at the start of the drive ..... 

Mine that I am using now looks like this in gparted ........ the installer should let you see something similar on your
own USB drive .......... but it needs to be a separate drive to the one you have the installation on ...... as I think you
already said it does not have enough space on it for the installation ...... 

If you can use a whole clean USB flash of 16gig ........ then use it ...... it will need formatting and setting as root /

as below ..... make sure to choose the correct drive the size will show as 16 gig on yours ......

obviously the one below is a 32gig drive and it is my main drive .... as I removed my hard drive.

Yours will possibly be different as you will be using two flash drives with your hard drive not working or being recognised

at this point in time ....... the letters sda sdb ..... will increment for each separate drive added ......

[IMG]https://sites.google.com/site/000menu/_/rsrc/1542069038301/wayland/problems-ubuntu-build/gparted.jpg[/IMG]

Check out the proper installation guides for 18.10 ...... going onto a flash drive as there are many more steps to
follow setting it up.

There are many links online - and here [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop?_ga=2.72206801.394600521.1542072078-618874642.1495123334#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop?_ga=2.72206801.394600521.1542072078-618874642.1495123334#0)

this is the one on ubuntuforums [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)

---

### Post by praywwjd2004 on 2018-11-12
> **23dornot23d said:**
> The root partition is defined by a /

The install should allow you to format the USB 16gig and create a root partition .........

I do not bother with a swap file but usually just leave some space at the start of the drive ..... 

Mine that I am using now looks like this in gparted ........ the installer should let you see something similar on your
own USB drive .......... but it needs to be a separate drive to the one you have the installation on ...... as I think you
already said it does not have enough space on it for the installation ...... 

If you can use a whole clean USB flash of 16gig ........ then use it ...... it will need formatting and setting as root /

as below ..... make sure to choose the correct drive the size will show as 16 gig on yours ......

obviously the one below is a 32gig drive and it is my main drive .... as I removed my hard drive.
 

Yours will possibly be different as you will be using two flash drives with your hard drive not working or being recognised

at this point in time ....... the letters sda sdb ..... will increment for each separate drive added ......

[IMG]https://sites.google.com/site/000menu/_/rsrc/1542069038301/wayland/problems-ubuntu-build/gparted.jpg[/IMG]

Check out the proper installation guides for 18.10 ...... going onto a flash drive as there are many more steps to
follow setting it up.

There are many links online - and here [https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop?_ga=2.72206801.394600521.1542072078-618874642.1495123334#0](https://tutorials.ubuntu.com/tutorial/tutorial-install-ubuntu-desktop?_ga=2.72206801.394600521.1542072078-618874642.1495123334#0)

this is the one on ubuntuforums [https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick)



Ok, I think I understand now. I need to use 2 flash drives. I load the install files on 1 then have it installed on the 2nd one. For some reason I thought I could do it all using only 1 flash drive. I am glad that you clarified that because I did not see that mentioned in any of the tutorials.

---

### Post by 23dornot23d on 2018-11-13
The reason for you having to use 2 flash drives is your main drive is not working ....... also you have no operating system other than the one on the flash drive - also your initial flash drive was not really large enough as it has told you there is not enough room to do a install to - as well as it holding the initial startup files and Operating System for 18.10 and with 18.10 being relatively new - most tutorials refer to 18.04 . ( so it is not a normal procedure covered by the many tutorials ) a lot use windows programs such as YUMI ..... others use programs that you need to install and also need a lot of explaining on their use .......... 

> 
inxi reported back this which is probably a smaller flash drive
[B]Drives:
  Local Storage: total: 7.28 GiB used: 2.41 GiB (33.2%) 
  ID-1: /dev/sda type: USB model: 058f 6387 size: 7.28 GiB 
Partition:
  ID-1: / size: 2.78 GiB used: 565.7 MiB (19.9%) fs: overlay source: ERR-102 
[/B]

So 2 flash drives is a good option in your case ....... till you sort out your main drive problems ( a 32gig could have been better to use - but you only mentioned 16 gig )

I prefer to run the latest version on 32 gig flash drives - (but this is personal preference as I have a lot of 3D programs and do quite a lot of rendering which needs space)
also when using flash drives look for transfer speeds some run much quicker than others ........ the ones I have say up to 95 meg a second ...... but usually perform quite a bit
slower at 20 meg/s ........ 

When you go as low as 2 meg a second **with slower old flash drives** the install takes almost 2 hours ( which is not really reasonable nowadays in my honest opinion ).

These newer micro cards and adapters going into the USB slot are what I have been using - just for information as it may be useful as the camera cards are quite fast nowadays.

This is a shot of mine in place and working ......

[IMG]https://sites.google.com/site/000menu/_/rsrc/1542122999701/wayland/problems-ubuntu-build/flash-card-reader.jpg[/IMG]


Could only find a link to 64gb cards ..... but the ones I use are 32gb
[https://www.walmart.com/c/kp/64gb-sd-cards](https://www.walmart.com/c/kp/64gb-sd-cards)
Not sure how long they last though - so always as well to be writing any valuable date to a proper drive made for backing up .

Best of luck with it any way .......

---

### Post by praywwjd2004 on 2018-11-13
> **23dornot23d said:**
> The reason for you having to use 2 flash drives is your main drive is not working ....... also you have no operating system other than the one on the flash drive - also your initial flash drive was not really large enough as it has told you there is not enough room to do a install to - as well as it holding the initial startup files and Operating System for 18.10 and with 18.10 being relatively new - most tutorials refer to 18.04 . ( so it is not a normal procedure covered by the many tutorials ) a lot use windows programs such as YUMI ..... others use programs that you need to install and also need a lot of explaining on their use .......... 



So 2 flash drives is a good option in your case ....... till you sort out your main drive problems ( a 32gig could have been better to use - but you only mentioned 16 gig )

I prefer to run the latest version on 32 gig flash drives - (but this is personal preference as I have a lot of 3D programs and do quite a lot of rendering which needs space)
also when using flash drives look for transfer speeds some run much quicker than others ........ the ones I have say up to 95 meg a second ...... but usually perform quite a bit
slower at 20 meg/s ........ 

When you go as low as 2 meg a second **with slower old flash drives** the install takes almost 2 hours ( which is not really reasonable nowadays in my honest opinion ).

These newer micro cards and adapters going into the USB slot are what I have been using - just for information as it may be useful as the camera cards are quite fast nowadays.

This is a shot of mine in place and working ......

[IMG]https://sites.google.com/site/000menu/_/rsrc/1542122999701/wayland/problems-ubuntu-build/flash-card-reader.jpg[/IMG]


Could only find a link to 64gb cards ..... but the ones I use are 32gb
[https://www.walmart.com/c/kp/64gb-sd-cards](https://www.walmart.com/c/kp/64gb-sd-cards)
Not sure how long they last though - so always as well to be writing any valuable date to a proper drive made for backing up .

Best of luck with it any way .......



Thank you, now I have another problem. When I try to boot from the usb now it takes me to the boot sequence screen. It shows my WD internal hard drive now (which is blank) but when I choose to boot from the usb it just goes to a black screen with a single blinking cursor in the top left corner and does not boot. I have tried booting from 2 different flash drives with Ubuntu on them and tried using 3 different usb ports on the computer. 

Do you have any idea why it is not booting from the usb anymore?

---

### Post by oldfred on 2018-11-13
Is BIOS/UEFI still seeing drive correctly?
If not double check connections are secure.

this just shows drive:
sudo lshw -C Disk -short

In Disks, and icon in upper right corner is Smart Status. All I know is good or bad, but it can also runs lots of tests. If shows good, tests probably not needed.

---

### Post by 23dornot23d on 2018-11-13
Its never seen the Main Drive correctly from the start - that is why the use of the flash drives.
But the OP has adjusted the cables in the meantime .... so it might now be seeing that drive ( which has absolutely nothing at all on it ) 

> 
Is BIOS/UEFI still seeing drive correctly?
If not double check connections are secure.


I have a feeling that the main internal drive will be showing up in the BIOS now - if the boot options come up and show it  ......... then it is being recognised by the bios and trying to boot to the main drive that has nothing on it ........ which I think is why you are seeing the white flashing cursor top left now ...... as there are no boot options
or anything on the main 1 terra drive yet.

Can you post a shot of the boot menu that shows up - and if you are using the flash drive - are you using the down arrow key to go onto the flash drive to
select it to boot from it ........... some photos of the boot menu and bios would be useful if you can show them.

Do you have a dvd/cd drive - if so do you have any boot media that will work from that drive ...... 

Bios allows you to change the boot sequence also .......... what is it set to boot from first ......... the first option ? is it the WD 1 terra drive.

I am hoping that you now have BIOS seeing the 1 Terra Drive that it was not seeing early on in this thread.

Selecting a boot media it can boot from ....... should allow you to see a boot screen ......

---

### Post by praywwjd2004 on 2018-11-13
This is the first screen that comes up when I turn on the computer:

 [IMG][IMG]http://i66.tinypic.com/nd6d14.png[/IMG][/IMG]

If I hit Del it brings me here:

[IMG][IMG]http://i66.tinypic.com/2r3fmt0.png[/IMG][/IMG]

It shows the WD hard drive here but it appears to be bad.

I will try to add screenshots of the Boot sequence if needed. The boot sequence has USB as #1 LAN #2 WD Hard drive #3

---

### Post by 23dornot23d on 2018-11-13
Its found the hard drive but is reporting SMART Capable and Status BAD
> 
A computer giving a "**S.M.A.R.T.** **Status BAD**, Backup and Replace" Press F1 to Resume error indicates that the hard drive is about to fail or has already failed. The **S.M.A.R.T.** system is a utility that monitors the "health" of the hard drive and reports any potential problems.

I had one of these problems with one of my hard drives and it was continuously locking the computer up .......... I did manage to use half of a 500 gig drive - but its only for testing now as I do not trust it anymore ........... chances are it is close to dying off ........ 

But the screen shots show us more than words can ...... 
> 
Device #01 :
Device #02 : Generic Compact
Device #03 : Multiple Flash



You do have a DVD drive too ..... do you have a CD / DVD disk with a boot image on it ........... as it will usually boot from a CD / DVD if one is in place at boot up.

Just a thought as the USBs do not seem to be doing a lot ..... is one USB the same you was using early on in this thread - or have you redone the install onto
larger USBs .......... so just as a check do you have a CD or Bootable DVD just to check nothing else got disturbed when you took the cables out of the drive and put them
back in again.

But the drive is showing up now .......... the bad news is it is reporting back as not in good condition.

---

### Post by praywwjd2004 on 2018-11-13
I am wondering if I had a currupt install files for Ubuntu. I loaded gparted on one of the flash drives and that loaded, however gparted did not see the 1TB WD hard drive. Also when I went back to my boot sequence USB is still #1 but the 1TB WD hard drive is no longer showing again.

Anyways I am going to try reloading the Ubuntu files on the flash drive again from Rufus. Last time I just copy and pasted the files from one flash drive to another. I don't know if that would have caused a problem but I guess it is a possibility.

---

### Post by 23dornot23d on 2018-11-13
> 
Last time I just copy and pasted the files from one flash drive to  another. I don't know if that would have caused a problem but I guess it  is a possibility.                 


Yep - you cannot just do that ...... that will be the problem ..........

> 
Anyways I am going to try reloading the Ubuntu files on the flash drive again from Rufus.


Ok looks very similar to Yumi ....  [https://www.pendrivelinux.com/yumi-multiboot-usb-creator/](https://www.pendrivelinux.com/yumi-multiboot-usb-creator/)

[https://rufus.ie/en_IE.html](https://rufus.ie/en_IE.html)



Good move ........ hopefully it will work again ..........

> 
Also when I went back to my boot sequence USB is still #1 but the 1TB WD hard drive is no longer showing again.



The hard drive might be also causing problems if it sometimes sees it and sometimes does not ............ can you hear it spinning up when it does show up.
Maybe it spins up sometimes but not others......... sometimes they overheat and bearings go in them .... lots of causes for bad drives .......

But we might be able to tell more once we have Ubuntu booting up ........... from a flash drive.

Best of Luck ......... with the new install ........

---

### Post by praywwjd2004 on 2018-11-13
I reloaded the files on my flash drive using rufus and was able to boot and install Ubuntu on the flash drive. It is running much much slower after installing it than it did when I was just trying it. If this is going to be the case I may just use it without installing it.

Also when I was installing Ubuntu it did see the 1TB internal drive but gave me a warning that it is likely to fail soon.

Thank you everyone for all of your help.

---

### Post by 23dornot23d on 2018-11-14
Good to hear you got it installed ..... mark it as solved - maybe this thread could help others in some way. :popcorn:

At some point it may be worth getting a faster larger USB drive - or replacing the one in the desktop - but as you say some
are tight and awkward to get to ...... I use USB drives quite a lot now - easy to just plug in and take with you if you want to
use them elsewhere.

This might be a useful command for the bad hard drive ....... have just run it on my own bad hard drive and the results are below for
information - so people know what it will report back if there is a problem.

```

# smartctl /dev/sda --all
smartctl 6.6 2016-05-31 r4324 [i686-linux-4.4.0-138-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST3500418AS
Serial Number:    6VM4K1B4
LU WWN Device Id: 5 000c50 018888b39
Firmware Version: CC37
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Wed Nov 14 18:57:21 2018 CET

==> WARNING: A firmware update for this drive may be available,
see the following Seagate web pages:
http://knowledge.seagate.com/articles/en_US/FAQ/207931en
http://knowledge.seagate.com/articles/en_US/FAQ/213891en

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  600) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  84) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   112   080   006    Pre-fail  Always       -       45797147
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   093   093   020    Old_age   Always       -       7402
  5 Reallocated_Sector_Ct   0x0033   002   002   036    Pre-fail  Always   FAILING_NOW 4035
  7 Seek_Error_Rate         0x000f   076   060   030    Pre-fail  Always       -       42791761
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       11829
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1281
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       129
188 Command_Timeout         0x0032   100   079   000    Old_age   Always       -       1627817836935
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   070   042   045    Old_age   Always   In_the_past 30 (0 250 30 12 0)
194 Temperature_Celsius     0x0022   030   058   000    Old_age   Always       -       30 (0 2 0 0 0)
195 Hardware_ECC_Recovered  0x001a   041   022   000    Old_age   Always       -       45797147
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       11903 (50 85 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3045717270
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       947518850

SMART Error Log Version: 1
ATA Error Count: 2511 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 2511 occurred at disk power-on lifetime: 11790 hours (491 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      01:04:16.088  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.047  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.039  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.004  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:15.994  READ DMA EXT

Error 2510 occurred at disk power-on lifetime: 11790 hours (491 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      01:04:16.088  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.047  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.039  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.004  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:15.994  READ DMA EXT

Error 2509 occurred at disk power-on lifetime: 11789 hours (491 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      00:01:37.625  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.484  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.477  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.457  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.445  READ DMA EXT

Error 2508 occurred at disk power-on lifetime: 11789 hours (491 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      00:01:37.625  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.484  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.477  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.457  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.445  READ DMA EXT

Error 2507 occurred at disk power-on lifetime: 11789 hours (491 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      00:01:24.172  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:24.114  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:24.106  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:24.079  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:24.070  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%     11772         0
# 2  Short offline       Completed: unknown failure    90%     11772         0
# 3  Extended offline    Completed: unknown failure    90%     11771         0
# 4  Conveyance offline  Completed: unknown failure    90%     11771         0
# 5  Conveyance offline  Completed: unknown failure    90%     11771         0
# 6  Short offline       Completed: unknown failure    90%     11771         0
# 7  Extended offline    Completed: unknown failure    90%     11690         0
# 8  Short offline       Completed: unknown failure    90%     11690         0

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.



```

---

### Post by praywwjd2004 on 2018-11-14
> **23dornot23d said:**
> Good to hear you got it installed ..... mark it as solved - maybe this thread could help others in some way. :popcorn:

At some point it may be worth getting a faster larger USB drive - or replacing the one in the desktop - but as you say some
are tight and awkward to get to ...... I use USB drives quite a lot now - easy to just plug in and take with you if you want to
use them elsewhere.

This might be a useful command for the bad hard drive ....... have just run it on my own bad hard drive and the results are below for
information - so people know what it will report back if there is a problem.

```

# smartctl /dev/sda --all
smartctl 6.6 2016-05-31 r4324 [i686-linux-4.4.0-138-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Family:     Seagate Barracuda 7200.12
Device Model:     ST3500418AS
Serial Number:    6VM4K1B4
LU WWN Device Id: 5 000c50 018888b39
Firmware Version: CC37
User Capacity:    500,107,862,016 bytes [500 GB]
Sector Size:      512 bytes logical/physical
Rotation Rate:    7200 rpm
Device is:        In smartctl database [for details use: -P show]
ATA Version is:   ATA8-ACS T13/1699-D revision 4
SATA Version is:  SATA 2.6, 3.0 Gb/s
Local Time is:    Wed Nov 14 18:57:21 2018 CET

==> WARNING: A firmware update for this drive may be available,
see the following Seagate web pages:
http://knowledge.seagate.com/articles/en_US/FAQ/207931en
http://knowledge.seagate.com/articles/en_US/FAQ/213891en

SMART support is: Available - device has SMART capability.
SMART support is: Enabled

=== START OF READ SMART DATA SECTION ===
SMART overall-health self-assessment test result: FAILED!
Drive failure expected in less than 24 hours. SAVE ALL DATA.
See vendor-specific Attribute list for failed Attributes.

General SMART Values:
Offline data collection status:  (0x82)    Offline data collection activity
                    was completed without error.
                    Auto Offline Data Collection: Enabled.
Self-test execution status:      (   0)    The previous self-test routine completed
                    without error or no self-test has ever 
                    been run.
Total time to complete Offline 
data collection:         (  600) seconds.
Offline data collection
capabilities:              (0x7b) SMART execute Offline immediate.
                    Auto Offline data collection on/off support.
                    Suspend Offline collection upon new
                    command.
                    Offline surface scan supported.
                    Self-test supported.
                    Conveyance Self-test supported.
                    Selective Self-test supported.
SMART capabilities:            (0x0003)    Saves SMART data before entering
                    power-saving mode.
                    Supports SMART auto save timer.
Error logging capability:        (0x01)    Error logging supported.
                    General Purpose Logging supported.
Short self-test routine 
recommended polling time:      (   1) minutes.
Extended self-test routine
recommended polling time:      (  84) minutes.
Conveyance self-test routine
recommended polling time:      (   2) minutes.
SCT capabilities:            (0x103f)    SCT Status supported.
                    SCT Error Recovery Control supported.
                    SCT Feature Control supported.
                    SCT Data Table supported.

SMART Attributes Data Structure revision number: 10
Vendor Specific SMART Attributes with Thresholds:
ID# ATTRIBUTE_NAME          FLAG     VALUE WORST THRESH TYPE      UPDATED  WHEN_FAILED RAW_VALUE
  1 Raw_Read_Error_Rate     0x000f   112   080   006    Pre-fail  Always       -       45797147
  3 Spin_Up_Time            0x0003   097   097   000    Pre-fail  Always       -       0
  4 Start_Stop_Count        0x0032   093   093   020    Old_age   Always       -       7402
  5 Reallocated_Sector_Ct   0x0033   002   002   036    Pre-fail  Always   FAILING_NOW 4035
  7 Seek_Error_Rate         0x000f   076   060   030    Pre-fail  Always       -       42791761
  9 Power_On_Hours          0x0032   087   087   000    Old_age   Always       -       11829
 10 Spin_Retry_Count        0x0013   100   100   097    Pre-fail  Always       -       0
 12 Power_Cycle_Count       0x0032   099   099   020    Old_age   Always       -       1281
183 Runtime_Bad_Block       0x0032   100   100   000    Old_age   Always       -       0
184 End-to-End_Error        0x0032   100   100   099    Old_age   Always       -       0
187 Reported_Uncorrect      0x0032   001   001   000    Old_age   Always       -       129
188 Command_Timeout         0x0032   100   079   000    Old_age   Always       -       1627817836935
189 High_Fly_Writes         0x003a   100   100   000    Old_age   Always       -       0
190 Airflow_Temperature_Cel 0x0022   070   042   045    Old_age   Always   In_the_past 30 (0 250 30 12 0)
194 Temperature_Celsius     0x0022   030   058   000    Old_age   Always       -       30 (0 2 0 0 0)
195 Hardware_ECC_Recovered  0x001a   041   022   000    Old_age   Always       -       45797147
197 Current_Pending_Sector  0x0012   100   100   000    Old_age   Always       -       0
198 Offline_Uncorrectable   0x0010   100   100   000    Old_age   Offline      -       0
199 UDMA_CRC_Error_Count    0x003e   200   200   000    Old_age   Always       -       0
240 Head_Flying_Hours       0x0000   100   253   000    Old_age   Offline      -       11903 (50 85 0)
241 Total_LBAs_Written      0x0000   100   253   000    Old_age   Offline      -       3045717270
242 Total_LBAs_Read         0x0000   100   253   000    Old_age   Offline      -       947518850

SMART Error Log Version: 1
ATA Error Count: 2511 (device log contains only the most recent five errors)
    CR = Command Register [HEX]
    FR = Features Register [HEX]
    SC = Sector Count Register [HEX]
    SN = Sector Number Register [HEX]
    CL = Cylinder Low Register [HEX]
    CH = Cylinder High Register [HEX]
    DH = Device/Head Register [HEX]
    DC = Device Command Register [HEX]
    ER = Error register [HEX]
    ST = Status register [HEX]
Powered_Up_Time is measured from power on, and printed as
DDd+hh:mm:SS.sss where DD=days, hh=hours, mm=minutes,
SS=sec, and sss=millisec. It "wraps" after 49.710 days.

Error 2511 occurred at disk power-on lifetime: 11790 hours (491 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      01:04:16.088  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.047  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.039  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.004  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:15.994  READ DMA EXT

Error 2510 occurred at disk power-on lifetime: 11790 hours (491 days + 6 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      01:04:16.088  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.047  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.039  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:16.004  READ DMA EXT
  25 00 08 ff ff ff 4f 00      01:04:15.994  READ DMA EXT

Error 2509 occurred at disk power-on lifetime: 11789 hours (491 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      00:01:37.625  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.484  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.477  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.457  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.445  READ DMA EXT

Error 2508 occurred at disk power-on lifetime: 11789 hours (491 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      00:01:37.625  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.484  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.477  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.457  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:37.445  READ DMA EXT

Error 2507 occurred at disk power-on lifetime: 11789 hours (491 days + 5 hours)
  When the command that caused the error occurred, the device was active or idle.

  After command completion occurred, registers were:
  ER ST SC SN CL CH DH
  -- -- -- -- -- -- --
  04 71 04 9d 00 32 40  Device Fault; Error: ABRT 4 sectors at LBA = 0x0032009d = 3276957

  Commands leading to the command that caused the error were:
  CR FR SC SN CL CH DH DC   Powered_Up_Time  Command/Feature_Name
  -- -- -- -- -- -- -- --  ----------------  --------------------
  25 00 18 ff ff ff 4f 00      00:01:24.172  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:24.114  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:24.106  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:24.079  READ DMA EXT
  25 00 08 ff ff ff 4f 00      00:01:24.070  READ DMA EXT

SMART Self-test log structure revision number 1
Num  Test_Description    Status                  Remaining  LifeTime(hours)  LBA_of_first_error
# 1  Extended offline    Completed: unknown failure    90%     11772         0
# 2  Short offline       Completed: unknown failure    90%     11772         0
# 3  Extended offline    Completed: unknown failure    90%     11771         0
# 4  Conveyance offline  Completed: unknown failure    90%     11771         0
# 5  Conveyance offline  Completed: unknown failure    90%     11771         0
# 6  Short offline       Completed: unknown failure    90%     11771         0
# 7  Extended offline    Completed: unknown failure    90%     11690         0
# 8  Short offline       Completed: unknown failure    90%     11690         0

SMART Selective self-test log data structure revision number 1
 SPAN  MIN_LBA  MAX_LBA  CURRENT_TEST_STATUS
    1        0        0  Not_testing
    2        0        0  Not_testing
    3        0        0  Not_testing
    4        0        0  Not_testing
    5        0        0  Not_testing
Selective self-test flags (0x0):
  After scanning selected spans, do NOT read-scan remainder of disk.
If Selective self-test is pending on power-up, resume after 0 minute delay.



```



Is this the correct code that you suggested I use for the bad drive? 
# smartctl /dev/sda --all
Did you run this code in Ubuntu?
This code is not bringing up any output for me.

I think I am going to disconnect the bad drive since I am not able to remove it from the computer.

---

### Post by 23dornot23d on 2018-11-14
You also may need the documentation and the command to load up smartmontools ..... but if you no longer plan
on using that drive - that is good.   As you can never tell when they will fail completely ......
Mine as I say - I use for testing and know it could fail anytime soon.

[https://help.ubuntu.com/community/Smartmontools](https://help.ubuntu.com/community/Smartmontools)

---

