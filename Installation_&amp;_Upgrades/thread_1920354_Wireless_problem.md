---
title: "Wireless problem"
date: 2012-02-04
forum: Installation &amp; Upgrades
---

### Post by lFuidy on 2012-02-04
This probably is as common as a full moon but I'm having serious wireless issues with Ubuntu 10.10.
I can get online with a cable easy but it won't connect by wireless. Basically the issue is that it does find the missing drivers needed but whenever I try to connect to my home network it either just doesn't go through or keeps asking the damn WEP password, which is always entered correctly...

---

### Post by kc1di on 2012-02-04
Could you give us a little more information?
What is the wireless card make and model? 
Will your net work use both wep/wpa?

give us the output of the terminal command 

```
lspci
```
Then we may be able to help.

---

### Post by lFuidy on 2012-02-04
Alright, sorry. :)
```
00:00.0 Host bridge: Intel Corporation Mobile 4 Series Chipset Memory Controller Hub (rev 07)
00:02.0 VGA compatible controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:02.1 Display controller: Intel Corporation Mobile 4 Series Chipset Integrated Graphics Controller (rev 07)
00:1a.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #4 (rev 03)
00:1a.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #5 (rev 03)
00:1a.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #6 (rev 03)
00:1a.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #2 (rev 03)
00:1b.0 Audio device: Intel Corporation 82801I (ICH9 Family) HD Audio Controller (rev 03)
00:1c.0 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 1 (rev 03)
00:1c.1 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 2 (rev 03)
00:1c.3 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 4 (rev 03)
00:1c.4 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 5 (rev 03)
00:1c.5 PCI bridge: Intel Corporation 82801I (ICH9 Family) PCI Express Port 6 (rev 03)
00:1d.0 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #1 (rev 03)
00:1d.1 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #2 (rev 03)
00:1d.2 USB Controller: Intel Corporation 82801I (ICH9 Family) USB UHCI Controller #3 (rev 03)
00:1d.7 USB Controller: Intel Corporation 82801I (ICH9 Family) USB2 EHCI Controller #1 (rev 03)
00:1e.0 PCI bridge: Intel Corporation 82801 Mobile PCI Bridge (rev 93)
00:1f.0 ISA bridge: Intel Corporation ICH9M LPC Interface Controller (rev 03)
00:1f.2 SATA controller: Intel Corporation ICH9M/M-E SATA AHCI Controller (rev 03)
00:1f.3 SMBus: Intel Corporation 82801I (ICH9 Family) SMBus Controller (rev 03)
09:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 03)
0c:00.0 Network controller: Broadcom Corporation BCM4312 802.11b/g LP-PHY (rev 01)
0f:00.0 SD Host controller: Ricoh Co Ltd Device e822 (rev 01)
0f:00.1 System peripheral: Ricoh Co Ltd Device e230 (rev 01)
0f:00.3 FireWire (IEEE 1394): Ricoh Co Ltd Device e832 (rev 01)
```

It finds 2 drivers:
Broadcom B43 wireless driver and Broadcom STA wireless driver. But it keeps removing each one I activate.

---

### Post by Gstrazds on 2012-02-04
Hi there - Do a search keyword "wireless" 

run the commands in terminal.. 

report back the findings.. 

Just went through this myself.. Flaky  install - found my broadcom driver - did a manual install; actually worked...then trapped..

Did a re-install.. It would appear that it is necessary? useful to boot to the usb install desktop (allows write to usbdisk)- activate the wireless driver which installs it into install partition.

did this with 11.04 - daily driver and 11.10 after a bunch of horror stories is working.. 
:popcorn:

Glenn

the 3.0.0-15 kernel has fixed most of the 3.0.0-12 problems But you have to go through -12 to get to -15 

getting the wireless activated downloads the 302 meg of files to save the grief..

---

### Post by lFuidy on 2012-02-04
> **Gstrazds said:**
> Hi there - Do a search keyword "wireless" 

run the commands in terminal.. 

report back the findings.. 


I'm sorry I'm completely new to Linux so I don't follow what you need me to do here.

---

### Post by kc1di on 2012-02-04
Hi again lFuidy, Welcome to linux and Ubuntu.
Your card is  a Broadcom 4312 which uses the Sta driver. 
Same card I have here works great once set up. 

remove any drivers you may have installed and re activate the sta driver only.  It should work.  

do a system update /upgrade first. so that you have the latest modules.  you may have to connect temporarily via hard wire.

---

### Post by lFuidy on 2012-02-04
When I have the STA driver activated, it doesn't detect any signals. If I have the B43 driver, it detects them but it won't connect.

---

### Post by kc1di on 2012-02-04
take a look at this thread seems there was a problem with 10.10 and broadcom wireless after updated kernel.  

[http://ubuntuforums.org/showpost.php?p=10312711&postcount=5]("http://ubuntuforums.org/showpost.php?p=10312711&postcount=5")

Also try the following see it it loads the module for the 4312.

```
sudo rmmod wl
sudo modprobe wl
```

Sorry I don't have 10.10 loaded on any machines right now but broadcom works fine in 11.10

---

### Post by Gstrazds on 2012-02-06
> **lFuidy said:**
> I'm sorry I'm completely new to Linux so I don't follow what you need me to do here.

Well  Here you help yourself...

When I said do a search using the keyword "wireless" that would be in the search box here at Ubuntu forums.

You will find many previous questions already posted and commented on.. including the "required tests" in order to determine what went wrong.. 

Your broadcom answers already exist; same driver as me.. 

I read through the posts to find a thread that recommended that " you can install the driver manually with the url to get it... which I did.. read the readme.. very exactly written.. vola driver installed and downloading.. were a trap occurred; I did not re-boot like I ought to have.. 

Then I said; How about just re-installing

I put 11.04 and 11.10 on two separate usb sticks with the expand the space feature to cover the whole 1gig stick..

I was not sure it would work since the recommendation is at least 2gig; So there is roughly 300 meg of extra space available in the virtual "Install session" 

I only realized this when the broadcom wireless driver showed up on the install desktop upon re-boot.. :D

Activating the wireless driver caused a write to the usb stick which enabled it on re-boot; which enabled the the 302 meg download to 3.0.0-15 bypassing the 3.0.0-12 release.. version 11.10

I think you have a flaky install Re-install using the usb stick idea [http://www.ubuntu.com/download/ubuntu/download](http://www.ubuntu.com/download/ubuntu/download)

copied from the above url...

Insert a USB stick with at least 2GB of free space
 
The easiest way to get up an running with USB is to use the USB installer provided by pendrivelinux.com. You’ll need to download and install using the link below. Then follow the instructions.
 
[http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.8.7.8.exe](http://www.pendrivelinux.com/downloads/Universal-USB-Installer/Universal-USB-Installer-1.8.7.8.exe)
Select Ubuntu Desktop Edition from the dropdown list

otherwise.. 

[SOLVED] Wireless / WiFi stopped working after Ubuntu 11.10
by cirelosborn supplied the "I did this" part...


sudo gedit /etc/modprobe.d/blacklist.conf
lspci | grep work
sudo lshw -C network
lsmod
rfkill list all
rfkill unblock all

from the broadcom wireless driver readme...

BUILD INSTRUCTIONS
------------------
1. Setup the directory by untarring the proper tarball:
For 32 bit:
For 64 bit:
hybrid-portsrc.tar.gz
hybrid-portsrc-x86_64.tar.gz

Example:
# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz

2. Build the driver as a Linux loadable kernel module (LKM):
# make clean (optional)

# make

When the build completes, it will produce a wl.ko file in the top level directory.

If your driver does not build, check to make sure you have installed the kernel package described in the requirements above.

This driver now supports the new linux cfg80211 wireless configuration API in addition to the older Wireless Extensions (Wext). 

The makefile will automatically build the right version for your system but it can be overridden if needed:

# make API=WEXT

or

# make API=CFG80211

--edited--

Fresh installation:
------------------
1: Remove any other drivers for the Broadcom wireless device.
There are several other drivers (besides this one) that can drive
Broadcom 802.11 chips such as b43, bcma and ssb. 

They will conflict with this driver and need to be uninstalled before this driver can be installed.

Any previous revisions of the wl driver also need to be removed.

Note: On some systems such as Ubuntu 9.10, the ssb module may load during boot even though it is blacklisted (see note under Common Issues on how to resolve this. 

Nevertheless, ssb still must be removed (by hand or script) before wl is loaded. The wl driver will not function properly if ssb the module is loaded.

# lsmod
| grep "b43\|ssb\|bcma\|wl"

If any of these are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod bcma
# rmmod wl

To blacklist these drivers and prevent them from loading in the future:

# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf

2: Insmod the driver.

Otherwise, if you have not previously installed a wl driver, you'll need to add a security module before using the wl module. Most newer systems use lib80211 while others use ieee80211_crypt_tkip. See which one works for your system.

# modprobe lib80211
or
# modprobe ieee80211_crypt_tkip

If your using the cfg80211 version of the driver, then cfg80211 needs to beloaded:

# modprobe cfg80211

Then:
# insmod wl.ko

wl.ko is now operational. It may take several seconds for the Network Manager to notice a new network driver has been installed and show the surrounding wireless networks.

If there was an error, see Common issues below.

Common issues:
----------------
* After the insmod you may see this message:
WARNING: modpost: missing MODULE_LICENSE()
It is expected, not harmful and can be ignored.

--cut--
Credit...

Broadcom Linux hybrid wireless driver
Version 5.100.82.1XX
DISCLAIMER
----------
This is an Official Release of Broadcom's hybrid Linux driver for use with
Broadcom based hardware.
WHERE TO GET THE RELEASE
------------------------
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
IMPORTANT NOTE AND DISCUSSION OF HYBRID DRIVER
----------------------------------------------
There are separate tarballs for 32 bit and 64 bit x86 CPU architectures.
Make sure you use the appropriate tarball for your machine.


Goodluck

Glenn

---

### Post by varunendra on 2012-02-07
> **lFuidy said:**
> 
```
0c:00.0 Network controller: Broadcom Corporation **BCM4312** 802.11b/g [COLOR=Red]**LP-PHY **[/COLOR](rev 01)
```It finds 2 drivers:
Broadcom **B43** wireless driver and** Broadcom STA** wireless driver. But it keeps removing each one I activate.
I don't think those are correct drivers for your card. Please try this:

[LIST]
[*]Open synaptic and type **BCM** in the search box
[*]**"completely remove"** all the currently installed packages corresponding to BCM
[*]Install **ONLY** two packages: **b43-fwcutter** and **firmware-b43-lpphy-installer**.
[*]Restart and try to connect.
[/LIST]
Post back the results.

---

### Post by Gstrazds on 2012-02-11
I wanted to add the complete readme in the latest Broadcom driver... the last poster commented on "these drivers may not be for you" other sections of the readme discuss "upgrades" and how to  "blacklist them"

I also pondered the original posters problem.. and how he could get two drivers in the (10.10) install in the first place...

Speculating that he installed ? 11.10 then Installed 10.10 over-top of 11.10 without erasing the previous install.. caused the conflict to occur.. 

Just musing

Broadcom Linux hybrid wireless driver
Version 5.100.82.1XX
DISCLAIMER
----------
This is an Official Release of Broadcom's hybrid Linux driver for use with
Broadcom based hardware.
WHERE TO GET THE RELEASE
------------------------
[http://www.broadcom.com/support/802.11/linux_sta.php](http://www.broadcom.com/support/802.11/linux_sta.php)
IMPORTANT NOTE AND DISCUSSION OF HYBRID DRIVER
----------------------------------------------
There are separate tarballs for 32 bit and 64 bit x86 CPU architectures.
Make sure you use the appropriate tarball for your machine.
Other than 32 vs 64 bit, the hybrid binary is agnostic to the specific
versions (2.6.X) and distributions (Fedora, Ubuntu, SuSE, etc). It performs
all interactions with the OS through OS specific files (wl_linux.c, wl_iw.c,
osl_linux.c) that are shipped in source form. You compile this source on
your system and link with a precompiled binary file (wlc_hybrid.o_shipped)
which contains the rest of the driver.
PRECOMPILED DRIVER
-------------------
Some distros (Ubuntu and Fedora at the least) already have a version of
this driver in their repositories precompiled, tested and ready to go.
You just use the package manager to install the proper package. If
its available for your distro, this is usually an easier solution. See
the end of this document for further discussion.
ABOUT THIS RELEASE
-------------------
This is a rollup release. It includes and deprecates all previous releases
and patches. At the time of release there are no existing patches for this
release from Broadcom.
SUPPORTED DEVICES
-----------------
The cards with the following PCI Device IDs are supported with this driver.
Both Broadcom and and Dell product names are described.
Cards not listed
here may also work.
BRCM
PCI
Product Name
Vendor ID
------------- ----------
4311 2.4 Ghz
0x14e4
4311 Dualband
0x14e4
4311 5 Ghz
0x14e4
4312 2.4 Ghz
0x14e4
4313 2.4 Ghz
0x14e4
4321 Dualband
0x14e4
4321 Dualband
0x14e4
4321 2.4 Ghz
0x14e4
4321 5 Ghz
0x14e4
4322 Dualband
0x14e4
4322 2.4 Ghz
0x14e4
4322 5 Ghz
0x14e4
PCI
Device ID
---------
0x4311
0x4312
0x4313
0x4315
0x4727
0x4328
0x4328
0x4329
0x432a
0x432b
0x432c
0x432d
Dell
Product ID
-----------
Dell 1390
Dell 1490
Dell
Dell
Dell
Dell
1395
1501
1505
1500
Dell 1510
02/03/2012 07:55 PM
43224
43225
43227
43228
Dualband
2.4 Ghz
2.4 Ghz
Dualband
0x14e4
0x14e4
0x14e4
0x14e4
0x4353
0x4357
0x4358
0x4359
Dell 1520
Dell 1530
To find the Device ID's of Broadcom cards on your machines do:
# lspci -n | grep 14e4
NOTABLE CHANGES
---------------
Added Cfg80211 support (described below)
Added Monitor mode
(described below)
REQUIREMENTS
------------
Building this driver requires that your machine have the proper tools,
packages, header files and libraries to build a standard a kernel module.
This usually is done by installing the kernel developer or kernel source
package and varies from distro to distro. Consult the documentation for
your specific OS.
If you cannot successfully build a module that comes with your distro's
kernel developer or kernel source package, you will not be able to build
this module either.
If you try to build this module but get an error message that looks like
this:
make: *** /lib/modules/"release"/build: No such file or directory. Stop.
Then you do not have the proper packages installed, since installing the
proper packages will create /lib/modules/"release"/build on your system.
On Fedora install 'kernel-devel' (Development Package for building kernel
modules to match the kernel) from the Package Manager (System->
Administration-> Add/Remove Software).
On Ubuntu, you will need headers and tools. Try these commands:
# apt-get install build-essential linux-headers-generic
# apt-get build-dep linux
To check to see if you have this directory do this:
# ls /lib/modules/`uname -r`/build
BUILD INSTRUCTIONS
------------------
1. Setup the directory by untarring the proper tarball:
For 32 bit:
For 64 bit:
hybrid-portsrc.tar.gz
hybrid-portsrc-x86_64.tar.gz
Example:
# mkdir hybrid_wl
# cd hybrid_wl
# tar xzf <path>/hybrid-portsrc.tar or <path>/hybrid-portsrc-x86_64.tar.gz
2. Build the driver as a Linux loadable kernel module (LKM):
# make clean
(optional)
02/03/2012 07:55 PM
# make
When the build completes, it will produce a wl.ko file in the top level
directory.
If your driver does not build, check to make sure you have installed the
kernel package described in the requirements above.
This driver now supports the new linux cfg80211 wireless configuration API in
addition to the older Wireless Extensions (Wext). The makefile will
automaticly build the right version for your system but it can be
overridden if needed:
# make API=WEXT
or
# make API=CFG80211
INSTALL INSTRUCTIONS
--------------------
Upgrading from a previous version:
---------------------------------
If you were already running a previous version of wl, you'll want to provide
a clean transition from the older driver. (The path to previous driver is
usually /lib/modules/<kernel-version>/kernel/net/wireless)
#
#
#
#
#
rmmod wl
mv <path-to-prev-driver>/wl.ko <path-to-prev-driver>/wl.ko.orig
cp wl.ko <path-to-prev-driver>/wl.ko
depmod
modprobe wl
The new wl driver should now be operational and your all done.
Fresh installation:
------------------
1: Remove any other drivers for the Broadcom wireless device.
There are several other drivers (besides this one) that can drive
Broadcom 802.11 chips such as b43, bcma and ssb. They will conflict with
this driver and need to be uninstalled before this driver can be installed.
Any previous revisions of the wl driver also need to be removed.
Note: On some systems such as Ubuntu 9.10, the ssb module may load during
boot even though it is blacklisted (see note under Common Issues on how to
resolve this. Nevertheless, ssb still must be removed
(by hand or script) before wl is loaded. The wl driver will not function
properly if ssb the module is loaded.
# lsmod
| grep "b43\|ssb\|bcma\|wl"
If any of these are installed, remove them:
# rmmod b43
# rmmod ssb
# rmmod bcma
# rmmod wl
To blacklist these drivers and prevent them from loading in the future:
# echo "blacklist ssb" >> /etc/modprobe.d/blacklist.conf
02/03/2012 07:55 PM
# echo "blacklist bcma" >> /etc/modprobe.d/blacklist.conf
# echo "blacklist b43" >> /etc/modprobe.d/blacklist.conf
2: Insmod the driver.
Otherwise, if you have not previously installed a wl driver, you'll need
to add a security module before using the wl module. Most newer systems
use lib80211 while others use ieee80211_crypt_tkip. See which one works for
your system.
# modprobe lib80211
or
# modprobe ieee80211_crypt_tkip
If your using the cfg80211 version of the driver, then cfg80211 needs to be
loaded:
# modprobe cfg80211
Then:
# insmod wl.ko
wl.ko is now operational. It may take several seconds for the Network
Manager to notice a new network driver has been installed and show the
surrounding wireless networks.
If there was an error, see Common issues below.
Common issues:
----------------
* After the insmod you may see this message:
WARNING: modpost: missing MODULE_LICENSE()
It is expected, not harmful and can be ignored.
* If you see this message:
"insmod: error inserting 'wl.ko': -1 Unknown symbol in module"
Usually this means that one of the required modules (as mentioned above) is
not loaded. Try this:
# modprobe lib80211 or ieee80211_crypt_tkip (depending on your os)
# modprobe cfg80211
Now re-try to insmod the wl driver:
# insmod wl.ko
* If the wl driver loads but doesn't seem to do anything:
the ssb module may be the cause. Sometimes blacklisting ssb may not
be enough to prevent it from loading and it loads anyway. (This is mostly
seen on Ubuntu/Debian systems).
Check to see if ssb, bcma, wl or b43 is loaded:
# lsmod | grep "ssb\|wl\|b43\|bcma"
If any of these are installed, remove them:
# rmmod ssb
# rmmod bcma
# rmmod wl
# insmod wl
02/03/2012 07:55 PM
Back up the current boot ramfs and generate a new one:
# cp /boot/initrd.img-`uname -r` somewheresafe
# update-initramfs -u
# reboot
3: Setup to always load at boot time.
The procedure to make a module load at boot time varies from distro to
distro. Consult the docs for your specific distro to see how. The
following seems to work for my setup on Fedora and Ubuntu. Check your
docs to see the procedure for your distro.
Follow these steps to have the driver load as part of the boot process:
# load driver as described above
# cp wl.ko /lib/modules/`uname -r`/kernel/drivers/net/wireless
# depmod -a
# echo modeprobe wl >> /etc/rc.local
(Fedora/SUSE)
Ubuntu ships a version of wl.ko, so those need to be disabled. On my
system the were several versions, so I searched and renamed the .ko's
like this:
# sh: for i in `find /lib /var -name wl\.ko`; do mv $i ${i}.orig; done
TX POWER EXPLAINED
------------------
'iwconfig eth1 txpower' & 'iwlist eth1 txpower' set and get the drivers
user-requested transmit power level. This can go up to 32 dbm and allows
the user to lower the tx power to levels below the regulatory limit.
Internally, the actual tx power is always kept within regulatory limits
no matter what the user request is set to.
ISSUES FIXED AND WHAT'S NEW IN THIS RELEASE
-------------------------------------------
+ Added cfg80211 API support. The choice of API is done at compile time. If
kernel version >= 2.6.32, cfg80211 is used, otherwise wireless extension
is used. (End users should notice little difference.)
+ Supports Linux kernel 2.6.38
+ Fix for problem with rebooting while wireless disabled via airline switch.
+ Fixed a kernel panic observed on some 64-bit systems
HOW TO USE MONITOR MODE
-----------------------
To enable monitor mode:
$ echo 1 > /proc/brcm_monitor0
Enabling monitor mode will create a 'prism0' network interface. Wireshark and
other netwokk tools can use this new prism0 interface.
To disable monitor mode:
$ echo 0 > /proc/brcm_monitor0
ISSUES FIXED AND WHAT'S NEW IN RECENT RELEASES
-------------------------------------------
+ Supports monitor mode
02/03/2012 07:55 PM
+ Supports cfg80211
+ Supports hidden networks
+ Supports rfkill
KNOWN ISSUES AND LIMITATIONS
----------------------------
#72238 - 20% lower throughput on channels 149, 153, 157, and 161
#72324 - Ubuntu 8.04: cannot ping when Linux STA is IBSS creator with WEP
enabled
#72216 - Ubuntu 8.04: standby/resume with WPA2 and wpa_supplicant causes
a continuous assoc/disassoc loop (issue with wpa_supplicant, restarting
wpa_supplicant fixes the issue)
#76739 Ubuntu9.04: unable to connect to hidden network after stdby/resume
#76793 Ubuntu9.04: STA fails to create IBSS network in 5 Ghz band
KNOWN ISSUES AND LIMITATIONS IN EXTERNAL COMPONENTS
----------------------------
wpa_supplicant 0.6.3 + nl80211 + WEP - (Note: This would only affect you if
you are using wpa_supplicant directly from the command line and specify
nl80211 interface, e.g. "wpa_supplicant -Dnl80211 -ieth1 ..". If you are using
network manager GUI to connect it should work file.)
wpa_supplicant 0.6.3 might have a bug that affect WEP connections created
through nl80211. Upgrade to wpa_supplicant to 0.7.3 would solve this problem.
Ubuntu 10.10 kernel + nl80211 + WPA/WPA2 - (Note: This would only affect you if
you are using wpa_supplicant directly from the command line and specify
nl80211 interface, e.g. "wpa_supplicant -Dnl80211 -ieth1 ..". If you are using
network manager GUI to connect it should work file.)
Some kernel versions of Ubuntu such as 2.6.35-22 (released with Ubuntu
10.10) may have problems that affect WPA/WPA2 connections created through
nl80211. Upgrade to 2.6.35-25 or later should solve this problem.
HOW TO INSTALL A PRE-COMPILED DRIVER
-----------------------------------
Some of the major linux distros already supply a version of this driver, so
you don't have to compile your own. Most of the distros keep this driver
along with other proprietary or non-GPL drivers in a separate repository.
For further information see the documentation for your specific distro.
Fedora:
------
su -c 'rpm -Uvh
[http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm](http://download1.rpmfusion.org/free/fedora/rpmfusion-free-release-stable.noarch.rpm)
[http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm](http://download1.rpmfusion.org/nonfree/fedora/rpmfusion-nonfree-release-stable.noarch.rpm)'
su -
yum update
yum install kmod-wl
Ubuntu:
------
Go to System->Administration->Hardware Drivers
Choose the Broadcom STA wireless driver
Activate
02/03/2012 07:55 PM
Sometimes the driver does not show up in the Hardware Drivers choices.
this case, try reintalling the driver from the GUI or shell like this:
In
From the GUI:
Package Manager (System>Administration>Synaptic Package Manager). Click the
Reload button in the upper left corner of Synaptic to refresh your index then
search for and reinstall the package named bcmwl-kernel-source.
From the shell:
sudo apt-get update
sudo apt-get --reinstall install bcmwl-kernel-source
In either GUI or text case, after reinstalling, reboot your machine.
Now go back to System->Administration->Hardware Drivers
and you should see the driver enabled and working.
02/03/2012 07:55 PM

---

