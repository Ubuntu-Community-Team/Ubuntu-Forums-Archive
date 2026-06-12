---
title: "Driver rtl8111 vs. Driver Wusb54gc"
date: 2011-12-24
forum: Installation &amp; Upgrades
---

### Post by UltimateCat on 2011-12-24
:) Hi!
   Very conflicted on which driver to install.

I found that my internal card ( RTL8111/8168B) ( I think) needs a driver. Ubuntu does not appear to recognize it. 

My usb adapter (WUSB54GC) only works on the Windows XP SP3 AMD Phenom 9850 Quad Core: side of my partition. 

I have the kernel version on the Linux side : 2.6.32 - 25 generic #43 and trying so hard to get Ubuntu online.

Should I install the driver for the WUSB......or install the driver for the internal card.

As a newbie I am not 100% sure and feel I need good advice.  Been working on this for 5 weeks now and well....it's been challenging and has left me :confused:

Would greatly appreciate a members take on this and what to do; Please!

---

### Post by dandnsmith on 2011-12-26
First collect some info:
in a terminal window run
 *sudo lshw -class network*
this will give the network interface details
then run
 *sudo lspci -v*
which wiil show the fdrivers loaded for each class of gear - hunt for the network interface detail.

If you can post the listings, someone can decode and try to give further help

---

### Post by Old_Grey_Wolf on 2011-12-26
UltimateCat,

Do you have the CD for the WUSB54GC Linksys adapter?
Do you have the ability to connect with a wired Ethernet?

If you do, you could download the "Windows Wireless Drivers" program from the Ubuntu Software Center and use it to install the .inf drivers from the WUSB54GC CD.

---

### Post by UltimateCat on 2011-12-26
> **dandnsmith said:**
> First collect some info:
in a terminal window run
 *sudo lshw -class network*
this will give the network interface details
then run
 *sudo lspci -v*
which wiil show the fdrivers loaded for each class of gear - hunt for the network interface detail.

If you can post the listings, someone can decode and try to give further help

Have to go to the Linux side of my partition to give you the sudo lshw....need a few hrs.
Here is lspci:


 cat@username:~$ lspci
 

 00:00.0 Host bridge: Advanced Micro Devices [AMD] RS780 Host Bridge  
 00:01.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (int gfx)  
 00:05.0 PCI bridge: Advanced Micro Devices [AMD] RS780 PCI to PCI bridge (PCIE port 1)  
 00:11.0 SATA controller: ATI Technologies Inc SB700/SB800 SATA Controller [IDE mode]  
 00:12.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller  
 00:12.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller  
 00:12.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller  
 00:13.0 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI0 Controller  
 00:13.1 USB Controller: ATI Technologies Inc SB700 USB OHCI1 Controller  
 00:13.2 USB Controller: ATI Technologies Inc SB700/SB800 USB EHCI Controller  
 00:14.0 SMBus: ATI Technologies Inc SBx00 SMBus Controller (rev 3a)  
 00:14.1 IDE interface: ATI Technologies Inc SB700/SB800 IDE Controller  
 00:14.2 Audio device: ATI Technologies Inc SBx00 Azalia (Intel HDA)  
 00:14.3 ISA bridge: ATI Technologies Inc SB700/SB800 LPC host controller  
 00:14.4 PCI bridge: ATI Technologies Inc SBx00 PCI to PCI Bridge  
 00:14.5 USB Controller: ATI Technologies Inc SB700/SB800 USB OHCI2 Controller  
 00:18.0 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] HyperTransport Configuration  
 00:18.1 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Address Map  
 00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller  
 00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control  
 00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control  
 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 3100 Graphics  
 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)

---

### Post by UltimateCat on 2011-12-26
> **Old_Gray_Wolf said:**
> UltimateCat,

Do you have the CD for the WUSB54GC Linksys adapter?
Do you have the ability to connect with a wired Ethernet?

If you do, you could download the "Windows Wireless Drivers" program from the Ubuntu Software Center and use it to install the .inf drivers from the WUSB54GC CD.

Yes, I have the cd for the WUS....and I also have the driver for the NIC( Network Interface Card)  Tried to install the driver yesterday but SPM ( Synaptic Pkg Mgr) or I didn't do something right.  

No, I don't have the ability to connect with a wired ethernet.....modem is 10 feet or more down the hall.

---

### Post by UltimateCat on 2011-12-26
> **dandnsmith said:**
> First collect some info:
in a terminal window run
 *sudo lshw -class network*
this will give the network interface details
then run
 *sudo lspci -v*
which wiil show the fdrivers loaded for each class of gear - hunt for the network interface detail.

If you can post the listings, someone can decode and try to give further help

Went  to the terminal and typed what you advised, see below:

Commands :

  

 cat@username:~$ sudo lshw - class network  
 [sudo] password for cat:  
 Hardware Lister (lshw) - B.02.14  
 usage: lshw [-format] [-options ...]  
        lshw -version  
 

 	-version        print program version (B.02.14)  
 

 format can be  
 	-html           output hardware tree as HTML  
 	-xml            output hardware tree as XML  
 	-short          output hardware paths  
 	-businfo        output bus information 
 

 options can be  
 	-class CLASS    only show a certain class of hardware  
 	-C CLASS        same as '-class CLASS' 
 	-c CLASS        same as '-class CLASS' 
 	-disable TEST   disable a test (like pci, isapnp, cpuid, etc. )  
 	-enable TEST    enable a test (like pci, isapnp, cpuid, etc. )  
 	-quiet          don't display status  
 	-sanitize       sanitize output (remove sensitive information like serial numbers, etc.)  
 	-numeric        output numeric IDs (for PCI, USB, etc.)  
 

 Next command:  lspci – v
 

 at@username:~$ lspci - v  
 Usage: lspci [<switches>]  
 

 Basic display modes:  
 -mm		Produce machine-readable output (single -m for an obsolete format)  
 -t		Show bus tree  
 

 Display options:  
 -v		Be verbose (-vv for very verbose)  
 -k		Show kernel drivers handling each device  
 -x		Show hex-dump of the standard part of the config space  
 -xxx		Show hex-dump of the whole config space (dangerous; root only)  
 -xxxx		Show hex-dump of the 4096-byte extended config space (root only)  
 -b		Bus-centric view (addresses and IRQ's as seen by the bus)  
 -D		Always show domain numbers  
 

 Resolving of device ID's to names:  
 -n		Show numeric ID's  
 -nn		Show both textual and numeric ID's (names & numbers)  
 -q		Query the PCI ID database for unknown ID's via DNS  
 -qq		As above, but re-query locally cached entries  
 -Q		Query the PCI ID database for all ID's via DNS  
 

 Selection of devices:  
 -s [[[[<domain>]:]<bus>]:][<slot>][.[<func>]]	Show only devices in selected slots  
 -d [<vendor>]:[<device>]			Show only devices with specified ID's  
 

 Other options:  
 -i <file>	Use specified ID database instead of /usr/share/misc/pci.ids.gz  
 -p <file>	Look up kernel modules in a given file instead of default modules.pcimap  
 -M		Enable `bus mapping' mode (dangerous; root only)  
 

 PCI access options:  
 -A <method>	Use the specified PCI access method (see `-A help' for a list)  
 -O <par>=<val>	Set PCI access parameter (see `-O help' for a list)  
 -G		Enable PCI access debugging  
 -H <mode>	Use direct hardware access (<mode> = 1 or 2)  
 -F <file>	Read PCI configuration dump from a given file 



Hope this helps you understand.  I have the driver for the (NIC) internal card.....just having a terrible time installing it-

---

### Post by dandnsmith on 2011-12-27
All that posting told me was that you're not using the versions of lshw and lspci which get installed with Ub 11.10, so the output I was looking for aren't there.
I was hoping to get any driver loaded by the kernel listed in the lspci.

Which versions of the Ubuntu and so on are you using?

I cannot help much with the driver install, as I've no idea what you have obtained, and what should be done - they usually come with a README file to explain things, and make files to do the work.

---

### Post by UltimateCat on 2011-12-27
> **dandnsmith said:**
> All that posting told me was that you're not using the versions of lshw and lspci which get installed with Ub 11.10, so the output I was looking for aren't there.
I was hoping to get any driver loaded by the kernel listed in the lspci.

Which versions of the Ubuntu and so on are you using?

I cannot help much with the driver install, as I've no idea what you have obtained, and what should be done - they usually come with a README file to explain things, and make files to do the work.


I have Ubuntu 10.04 and Ultimate Edition 2.7

If it was you, would you just follow the instruction and type in the commands mentioned in the Read Me file?

---

### Post by Old_Grey_Wolf on 2011-12-27
Dandnsmith asked you to enter

```
sudo lshw -class network
```

you entered

```
sudo lshw - class network
```

with a space after the &#8220;-&#8221;.

Then Dandnsmith asked you to enter

```
sudo lspci -v
```

you entered

```
sudo lspci &#8211; v
```

again with a space after the &#8220;-&#8221;.

Try entering the commands again without the space after the "-". Then maybe Dandnsmith will be able to help you.

With a space after the "-" it is not a valid command; therefore, Dandnsmith didn't get the desired information that was needed.

---

### Post by Old_Grey_Wolf on 2011-12-27
> **UltimateCat said:**
> 
No, I don't have the ability to connect with a wired ethernet.....modem is 10 feet or more down the hall.

Maybe you could buy something like this 50 foot cable for $3.46 [http://www.amazon.com/CAT-UTP-Snagless-Blue-50ft/dp/B0034XG9TQ](http://www.amazon.com/CAT-UTP-Snagless-Blue-50ft/dp/B0034XG9TQ) somewhere locally to get a wired Ethernet connection. Then get the wireless working using the "Windows Wireless Drivers" program from the Ubuntu Software Center.

---

### Post by UltimateCat on 2011-12-28
> **Old_Gray_Wolf said:**
> Dandnsmith asked you to enter

```
sudo lshw -class network
```you entered

```
sudo lshw - class network
```with a space after the “-”.

Then Dandnsmith asked you to enter

```
sudo lspci -v
```you entered

```
sudo lspci – v
```again with a space after the “-”.

Try entering the commands again without the space after the "-". Then maybe Dandnsmith will be able to help you.

With a space after the "-" it is not a valid command; therefore, Dandnsmith didn't get the desired information that was needed.

Sorry about that.  I will try again

Code:  sudo lspci -v......( got it )

---

### Post by UltimateCat on 2011-12-29
:)Typed in the command : Code: sudo lspci -v
Terminal :

Try entering the commands again without the space after the "-". Then maybe Dandnsmith will be able to help :
 

 00:18.2 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] DRAM Controller  
 	Flags: fast devsel  
 

 00:18.3 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Miscellaneous Control  
 	Flags: fast devsel  
 	Capabilities: [f0] Secure device <?> 
 

 00:18.4 Host bridge: Advanced Micro Devices [AMD] K10 [Opteron, Athlon64, Sempron] Link Control  
 	Flags: fast devsel  
 

 01:05.0 VGA compatible controller: ATI Technologies Inc Radeon 3100 Graphics  
 	Subsystem: Micro-Star International Co., Ltd. Device 7501  
 	Flags: bus master, fast devsel, latency 0, IRQ 27  
 	Memory at d0000000 (32-bit, prefetchable) [size=256M]  
 	I/O ports at d000 [size=256]  
 	Memory at feaf0000 (32-bit, non-prefetchable) [size=64K]  
 	Memory at fe900000 (32-bit, non-prefetchable) [size=1M]  
 	Capabilities: [50] Power Management version 3  
 	Capabilities: [a0] Message Signalled Interrupts: Mask- 64bit+ Queue=0/0 Enable+  
 	Kernel driver in use: fglrx_pci  
 	Kernel modules: fglrx, radeon  
 

 02:00.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL8111/8168B PCI Express Gigabit Ethernet controller (rev 02)  
 	Subsystem: Micro-Star International Co., Ltd. Device 501c  
 	Flags: bus master, fast devsel, latency 0, IRQ 26  
 	I/O ports at e800 [size=256]  
 	Memory at fdfff000 (64-bit, prefetchable) [size=4K]  
 	Memory at fdfe0000 (64-bit, prefetchable) [size=64K]  
 	Expansion ROM at febf0000 [disabled] [size=64K]  
 	Capabilities: [40] Power Management version 3  
 	Capabilities: [50] Message Signalled Interrupts: Mask- 64bit+ Queue=0/1 Enable+  
 	Capabilities: [70] Express Endpoint, MSI 01  
 	Capabilities: [b0] MSI-X: Enable- Mask- TabSize=2  
 	Capabilities: [d0] Vital Product Data <?>  
 	Capabilities: [100] Advanced Error Reporting <?>  
 	Capabilities: [140] Virtual Channel <?>  
 	Capabilities: [160] Device Serial Number 00-00-00-00-00-00-00-00  
 	Kernel driver in use: r8169  
 	Kernel modules: r8169  
 
:confused: not sure what this all means

---

### Post by dandnsmith on 2011-12-29
It means we've probably found the culprit. That 'r8169' module has given a lot of people problems, me amongst them.
For a reasonably quick fix, try replacing the r8169 module with the r8168, which seems to work without the same faulty behaviour.

There are a number of threads pertaining to this, to some of which I've addded some content - a good starting place, with almost all the needed content is [this one](http://ubuntuforums.org/showthread.php?t=1022411)

HTH

---

### Post by UltimateCat on 2012-01-06
> **Old_Gray_Wolf said:**
> Maybe you could buy something like this 50 foot cable for $3.46 [http://www.amazon.com/CAT-UTP-Snagless-Blue-50ft/dp/B0034XG9TQ](http://www.amazon.com/CAT-UTP-Snagless-Blue-50ft/dp/B0034XG9TQ) somewhere locally to get a wired Ethernet connection. Then get the wireless working using the "Windows Wireless Drivers" program from the Ubuntu Software Center.
Problem solved:D
I found the right driver.....WUSB54GC...tar.bz

---

