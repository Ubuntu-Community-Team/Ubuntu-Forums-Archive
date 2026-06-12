---
title: "log shows multiple problems"
date: 2017-03-02
forum: Installation &amp; Upgrades
---

### Post by Mark_in_Hollywood on 2017-03-02
In April 2016, I upgraded from 14.04LTS to 16.04LTS. All is well. About 2 months ago, I swapped out the motherboard and cpu for a new motherboard and cpu. System Monitor app finds the new 6 core CPU. All is almost well. The several logs show a number of faults, errors and problems. That has made me think that I need to do a clean install. Yet the OS and software apps run without problem. 

If the old adage, let sleeping dogs lie, best applies here, so be it. But if I can prevent future problems, increase efficiency and maximize resources, I would prefer it.

Below is a brief sample of the errors, faults, warnings and problems.

```
syslog

Mar  2 08:25:00 Lexington com.canonical.Unity.Scope.Info.Calculator[2652]: /usr/share/unity-scopes/scope-runner-dbus.py:24:** PyGIWarning**: Unity was imported without specifying a version first. Use gi.require_version('Unity', '7.0') before import to ensure that the right version gets loaded.
Mar  2 08:25:00 Lexington com.canonical.Unity.Scope.Info.Calculator[2652]:   from gi.repository import Unity

==============

Mar  2 07:15:15 Lexington kernel: [    0.000000] ACPI: IVRS 0x00000000DD9A4B10 0000D0 (v01 AMD    RD890S   00202031 AMD  00000000)
Mar  2 07:15:15 Lexington kernel: [    0.000000] ACPI: Local APIC address 0xfee00000
Mar  2 07:15:15 Lexington kernel: [    0.000000] No NUMA configuration found
Mar  2 07:15:15 Lexington kernel: [    0.000000] Faking a node at [mem 0x0000000000000000-0x000000011effffff]
Mar  2 07:15:15 Lexington nvidia-persistenced: The daemon no longer has permission to remove its runtime data directory /var/run/nvidia-persistenced

Mar  2 07:15:15 Lexington /usr/bin/snap[477]: cmd.go:111: DEBUG: restarting into "/snap/core/current/usr/bin/snap"
Mar  2 07:15:15 Lexington ureadahead[265]: ureadahead:/var/crash/.lock: No such file or directory

===============

Mar  2 07:15:15 Lexington kernel: [    0.000000] AGP: Your BIOS doesn't leave an aperture memory hole
Mar  2 07:15:15 Lexington kernel: [    0.000000] AGP: Please enable the IOMMU option in the BIOS setup
Mar  2 07:15:15 Lexington systemd[1]: Starting Clean up any mess left by 0dns-up...
Mar  2 07:15:15 Lexington kernel: [    0.000000] AGP: This costs you 64MB of RAM

==============


Mar  2 07:15:15 Lexington kernel: [    1.578361] microcode: CPU0: patch_level=0x06000822
Mar  2 07:15:15 Lexington kernel: [    1.578393] IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f3c0 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.578394] microcode: CPU1: patch_level=0x06000822
Mar  2 07:15:15 Lexington kernel: [    1.578442] microcode: CPU2: patch_level=0x06000822
Mar  2 07:15:15 Lexington kernel: [    1.578444] AMD-Vi: Event logged [
Mar  2 07:15:15 Lexington kernel: [    1.578483] microcode: CPU3: patch_level=0x06000822
Mar  2 07:15:15 Lexington kernel: [    1.578485] IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f400 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.578530] microcode: CPU4: patch_level=0x06000822
Mar  2 07:15:15 Lexington kernel: [    1.578537] AMD-Vi: Event logged [
Mar  2 07:15:15 Lexington kernel: [    1.578563] microcode: CPU5: patch_level=0x06000822
Mar  2 07:15:15 Lexington kernel: [    1.578579] IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f440 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.578627] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f480 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.578737] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f4c0 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.578789] microcode: Microcode Update Driver: v2.01 <tigran@aivazian.fsnet.co.uk>, Peter Oruba
Mar  2 07:15:15 Lexington kernel: [    1.578877] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f500 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.578986] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f540 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.579122] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f580 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.579232] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f5c0 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.579347] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f600 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.579457] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f640 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.579570] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f680 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.579681] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f6c0 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.579795] AMD-Vi: Event logged [IO_PAGE_FAULT device=02:00.0 domain=0x0011 address=0x000000010000f700 flags=0x0030]
Mar  2 07:15:15 Lexington kernel: [    1.579904] AMD-Vi: Event logged [


=======================


Mar  2 07:15:15 Lexington kernel: [   33.347523] xhci_hcd 0000:04:00.0: Stopped the command ring failed, maybe the host is dead
Mar  2 07:15:15 Lexington kernel: [   33.374139] xhci_hcd 0000:04:00.0: Host not halted after 16000 microseconds.
Mar  2 07:15:15 Lexington kernel: [   33.374140] xhci_hcd 0000:04:00.0: Abort command ring failed
Mar  2 07:15:15 Lexington kernel: [   33.374259] xhci_hcd 0000:04:00.0: HC died; cleaning up
Mar  2 07:15:15 Lexington kernel: [   33.374327] xhci_hcd 0000:04:00.0: Timeout while waiting for setup device command
Mar  2 07:15:15 Lexington kernel: [   33.374333] usb 10-1: hub failed to enable device, error -62
Mar  2 07:15:15 Lexington kernel: [   33.374400] usb usb10-port1: couldn't allocate usb_device
Mar  2 07:15:15 Lexington kernel: [   35.504868] lp: driver loaded but no devices found


===================


Mar  2 07:15:17 Lexington gpu-manager[960]: update-alternatives: error: no alternatives for x86_64-linux-gnu_gfxcore_conf


=====================

Mar  2 07:15:20 Lexington thermald[1120]: Unsupported cpu model, use thermal-conf.xml file or run with --ignore-cpuid-check


========================

Mar  2 07:15:24 Lexington colord[1379]: (colord:1379): Cd-WARNING **: failed to get session [pid 1129]: No such device or address


===================

Mar  2 07:15:39 Lexington ntop[1765]:   **ERROR** pcap_open_live(): 'eth0: SIOCETHTOOL(ETHTOOL_GET_TS_INFO) ioctl failed: No such device'
Mar  2 07:15:39 Lexington ntop[1765]:   Please correct the problem or select a different interface using the -i flag
Mar  2 07:15:39 Lexington ntop[1765]:   **FATAL_ERROR** Not root, ntop shutting down...
Mar  2 07:15:39 Lexington ntop[1765]:   CLEANUP[t140447929153728]: ntop caught signal 2 [state=2]
Mar  2 07:15:39 Lexington ntop[1765]:   ntop is now quitting...


========================

Mar  2 07:20:22 Lexington colord[1379]: (colord:1379): Cd-WARNING **: failed to get session [pid 2445]: No such device or address
Mar  2 07:20:22 Lexington rsyslogd: [origin software="rsyslogd" swVersion="8.16.0" x-pid="965" x-info="http://www.rsyslog.com"] rsyslogd was HUPed
```

---

### Post by oldfred on 2017-03-02
I have seen the IOMMU issue before:
 Some Gigabyte boards need acpi=off boot parameter also
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

---

### Post by #&amp;thj^% on 2017-03-02
> **oldfred said:**
> I have seen the IOMMU issue before:
 Some Gigabyte boards need acpi=off boot parameter also
 GIGABYTE GA-970A-DS3 motherboard not working with 64 bit kernel - IOMMU GRUB_CMDLINE_LINUX="iommu=soft"
[http://ubuntuforums.org/showthread.php?t=2111223&page=5](http://ubuntuforums.org/showthread.php?t=2111223&page=5)
[http://ubuntuforums.org/showthread.php?t=2292025](http://ubuntuforums.org/showthread.php?t=2292025)
[http://ubuntuforums.org/showthread.php?t=2242023](http://ubuntuforums.org/showthread.php?t=2242023)
[SOLVED] GA-970A-DS3P revision 1 no usb 3.0
[http://ubuntuforums.org/showthread.php?t=2188370](http://ubuntuforums.org/showthread.php?t=2188370)

+1 Great information here.:D
> If the old adage, let sleeping dogs lie, best applies here, so be it. But if I can prevent future problems, increase efficiency and maximize resources, I would prefer it.
The Old Adage is worth heeding here...
with systemd in the picture now...it has been the norm for me to see similar errors on both my machine and clients machines I have seen with Hardware swaps or replacements such as you have done (Hardware Changes)

You can read about about the IOMMU here:
[http://en.wikipedia.org/wiki/IOMMU](http://en.wikipedia.org/wiki/IOMMU)


Still, as of yet, no indication as to WHY the error is happening on a non-AGP system without an aperture or IOMMU setting in the BIOS, and no (physically possible) solutions have been offered.

it just annoyed me to see the startup message saying I was loosing memory. That being said, I tried a lot of the basic solutions posted here and there(iommu=noagp and iommu=memaper=3) without any resolve.

What did work for me was adding:

```
iommu=noaperture
```

Or check in your Bios to see if that option is availble to enable.

As it turns out, IOMMU was working all along, it's just that the kernel logs weren't showing it. But the IOMMU driver was there, it was working, and I serendipitously found out when I mistakenly typed ps -ef instead of dmesg like this:
```
$ ps -ef | grep -i iommu
me        7729 18279  0 11:48 pts/0    00:00:00 grep -i iommu

```
But again "If it's not broke don't fix it"
Ha!! but like a moth to flames I had to try to fix it! (3 weeks worth of time on this matter)


I hope this post actually helps someone else.

---

### Post by Mark_in_Hollywood on 2017-03-03
As though the above wasn't enough, today, a day after my OP, I saw an article about[ Linux vs. Win10 and security]("https://www.linuxnewssite.com/let-amd-know-you-want-coreboot-libreboot-support-and-open-sourcing-the-psp-platform-security-processor-03032017273.html").

That story involves Sandboxing and other security issues and when I ran the code from that story:

chrome://gpu/

Much to my surprise, the GPU listed is no longer in this 'puter. And not much is "working". Along with the original motherboard and cpu there was an EVGA 9500-GT graphics card. It is now replaced with an EVGA GT-710.

 See the pages attached as the .PDF, below.

I apologize to OldFred. This motherboard is a MSI 970 Gaming and an AMD FX-6300 CPU. Sorry 'bout that. 

I have enabled the 64K in the BIOS, and set GRUB to "iommu=soft", but am still seeing page_faults repeating dozens of times as the first lines at boot up. Same slow boot up. Passing strange.

---

### Post by oldfred on 2017-03-03
I do not know AMD.

But if you switched to an older nVidia card, you may need a different legacy nVidia driver.
       #To see video:
sudo lshw -c display
sudo lshw | grep -A 11 display
lspci | grep VGA
#Resolution:
xwininfo -root
xrandr -q
xrandr --q1
#What is installed
dkms status 


 Updated driver search by nVidia model, do not download, just check correct driver version
[http://www.geforce.com/drivers](http://www.geforce.com/drivers) 

If older nVidia card, then drivers are in Ubuntu's repository. But you must purge old drivers before attempting to install a different driver.

---

### Post by Mark_in_Hollywood on 2017-03-03
Dear OldFred. Here is what happened hardware wise. New MSI motherboard model** 970 Gaming**. New CPU AMD **FX-6300**. New Nvidia Graphic card **GT710**.

Just for completeness sake, even though this is all new hardware, not older, as you stated above, I have run the commands. Here is the terminal responses:

mark@Lexington:~$ sudo lshw -c display
[sudo] password for mark: 
  *-display               
       description: VGA compatible controller
       product: NVIDIA Corporation
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
       configuration: driver=nvidia latency=0
       resources: irq:32 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:fe000000-fe07ffff


mark@Lexington:~$ sudo lshw | grep -A 11 display
           *-display
                description: VGA compatible controller
                product: NVIDIA Corporation
                vendor: NVIDIA Corporation
                physical id: 0
                bus info: pci@0000:01:00.0
                version: a1
                width: 64 bits
                clock: 33MHz
                capabilities: pm msi pciexpress vga_controller bus_master cap_list rom
                configuration: driver=nvidia latency=0
                resources: irq:32 memory:fd000000-fdffffff memory:f0000000-f7ffffff memory:f8000000-f9ffffff ioport:e000(size=128) memory:fe000000-fe07ffff


mark@Lexington:~$ lspci | grep VGA
01:00.0 VGA compatible controller: NVIDIA Corporation Device 128b (rev a1)


mark@Lexington:~$ xwininfo -root

xwininfo: Window id: 0x2a0 (the root window) (has no name)

  Absolute upper-left X:  0
  Absolute upper-left Y:  0
  Relative upper-left X:  0
  Relative upper-left Y:  0
  Width: 1360
  Height: 768
  Depth: 24
  Visual: 0x21
  Visual Class: TrueColor
  Border width: 0
  Class: InputOutput
  Colormap: 0x20 (installed)
  Bit Gravity State: ForgetGravity
  Window Gravity State: NorthWestGravity
  Backing Store State: NotUseful
  Save Under State: no
  Map State: IsViewable
  Override Redirect State: no
  Corners:  +0+0  -0+0  -0-0  +0-0
  -geometry 1360x768+0+0


mark@Lexington:~$ xrandr -q
Screen 0: minimum 8 x 8, current 1360 x 768, maximum 16384 x 16384
DVI-I-0 disconnected (normal left inverted right x axis y axis)
DVI-I-1 disconnected (normal left inverted right x axis y axis)
HDMI-0 disconnected (normal left inverted right x axis y axis)
DVI-D-0 connected primary 1360x768+0+0 (normal left inverted right x axis y axis) 760mm x 450mm
   1360x768      60.02*+
   1920x1080     60.00    59.94    50.00    23.97    60.05    60.00    50.04  
   1280x768      59.87  
   1280x720      59.94    50.00  
   1024x768      75.03    70.07    60.00  
   800x600       75.00    72.19    60.32  
   720x576       50.00    50.08  
   720x480       59.94    59.94    60.05  
   640x480       75.00    72.81    59.94    59.93  


mark@Lexington:~$ xrandr --q1
 SZ:    Pixels          Physical       Refresh
*0   1360 x 768    ( 460mm x 260mm )  *50  
 1   1920 x 1080   ( 650mm x 365mm )   51   52   53   54   55   56   57  
 2   1280 x 768    ( 433mm x 260mm )   58  
 3   1280 x 720    ( 433mm x 243mm )   59   60  
 4   1024 x 768    ( 346mm x 260mm )   61   62   63  
 5    800 x 600    ( 270mm x 203mm )   64   65   66  
 6    720 x 576    ( 243mm x 195mm )   67   68  
 7    720 x 480    ( 243mm x 162mm )   69   70   71  
 8    640 x 480    ( 216mm x 162mm )   72   73   74   75  
 9   1360 x 765    ( 460mm x 259mm )   76  
Current rotation - normal
Current reflection - none
Rotations possible - normal left inverted right 
Reflections possible - X Axis Y Axis


mark@Lexington:~$ dkms status
bbswitch, 0.8, 4.4.0-64-generic, x86_64: installed
bbswitch, 0.8, 4.4.0-65-generic, x86_64: installed
nvidia-340, 340.101, 4.4.0-64-generic, x86_64: installed
nvidia-340, 340.101, 4.4.0-65-generic, x86_64: installed

Reading at:

[https://ubuntuforums.org/showthread.php?t=2336077](https://ubuntuforums.org/showthread.php?t=2336077)

I have changed the BIOS per it's wisdom.


In BIOS, I have the following settings:
> Disabled XHCI hand off in BIOS
> Disabled EHCI hand off in BIOS
> Disabled Legacy USB Support in BIOS

 I have enabled the IOMMU to 64meg. I can read USB 2.0 devices  in the USB 3.0 front panel slot, as long as they are not SanDisk drives. The SanDisks will mount on the USB 2.0 slot. I have no USB 3.0 devices.

This has prevented the page_fault boot time problem.

---

### Post by oldfred on 2017-03-03
Sorry, thought that was an older nVidia card.
I am running a product: GF108 [GeForce GT 620], but find difference between open source & nVidia driver to be minimal for what I use system for.

---

