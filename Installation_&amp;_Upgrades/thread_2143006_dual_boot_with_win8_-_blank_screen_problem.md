---
title: "dual boot with win8 - blank screen problem"
date: 2013-05-07
forum: Installation &amp; Upgrades
---

### Post by pete_the_great on 2013-05-07
Hi,

I got a new laptop recently (msi ge60) which came with windows 8 preinstalled, and I trying to sort out a dual boot setup with ubuntu 13.04. Right now, when I try to boot ubuntu I'm getting a blank purple screen. I've been following the instructions in the [Graphics resolution/Blank screen thread]("http://ubuntuforums.org/showthread.php?t=1743535"), but so far without success.

After getting my shiny new laptop, I resized the windows 8 partition to make room for ubuntu (using the windows utility). I then downloaded the 13.04 amd64 desktop image and burned it to disk. When I tried booting the disk, I would get a grub menu coming up, but then just a blank (black) screen whenever I selected either "try ubuntu" or "instal ubuntu". I tried turning off secureboot and fastboot, and editing the grub commands ( I tried nomodeset, nosplash --verbose text, etc.) but couldn't ever get anything other than a blank screen.

When I changed the boot mode from UEFI to BIOS (legacy), then I was able to boot the disc. I added some partitions and installed ubuntu. It didn't recognize windows 8, but I created a partition for /boot and installed grub there. I then installed boot-repair. I first ran boot-repair without making any changes, just to get a boot information summary ([here]("http://paste.ubuntu.com/5639594/")).  I then ran it again, using the recommended repair (boot information summary [here]("http://paste.ubuntu.com/5641866/")).

So now, when I turn on the computer (in UEFI mode) I get a grub menu from which I can select windows or ubuntu. Windows works fine. Selecting ubuntu just gives me a blank purple screen. Following step 2 of the blank screen thread, I've tried editing the grub entry for ubuntu so that it will boot into a text terminal. The grub entry for ubuntu has a line that ends with " ro quiet splash $vt_handoff". I've tried replacing this with "ro nosplash --verbose text", hoping that it would display some warning message/error, but I'm still just seeing a blank purple screen.

Thanks for reading. Any help/suggestions would be greatly appreciated.

---

### Post by oldfred on 2013-05-07
It looks like you still have Windows 8 hibernating.

But your issue is still related to video issue, what video chip/card do you have.
Nomodeset works for nVidia, unless it is Optimus.
With Intel you often need to use the screen size to force it to work.

For Intel, Example is probably not a laptop size. Change to yours.
 Force Intel Video mode as boot parameter in grub menu
video=1280x1024-24@60
and if that doesn't work you can try
video=VGA-1:1280x1024-24@60

You may be able to do this from Boot-Repair.
 Boot-Repair --> Advanced options --> GRUB options tab --> tick the "Uncomment GFXMODE" option --> Apply
Boot-Repair --> Advanced options --> GRUB options tab --> tick "Add kernel option: nomodeset" --> Apply

---

### Post by pete_the_great on 2013-05-07
Thanks for your reply. I didn't realise that windows had a faststart thing that made it hibernate automatically, but I've disabled that now.

My computer has an nvidia GeForce GTX 660m video card. It also has a core i7 processor, which has "Intel HD graphics 4000".

From the grub command line, I ran videoinfo, which gave the following:

Adapter 'Cirrus CLGD 5446 PCI Video Driver' : no info available
Adapter 'Bochs PCI Video Driver' : no info available
Adapter 'EFI GOP Driver' :
0x000 1920x1080x32 (7680) Directcolor mask 8/8/8/8 pos 16/8/0/24
as well as some other modes, down to 
0x004 1280x1024x32

I then tried editing the kernel line in the grub entry for ubuntu, so that it ended with " ro nosplash --verbose text video=1280x1024-32@60"
but I still got a blank screen. I tried the video=VGA-1:1280x1024-32@60 and using nomodeset, but still got the blank screen.

---

### Post by oldfred on 2013-05-07
Sounds like it is in Intel mode. Are you able to set which video you are using in UEFI/BIOS?

While Lenovo, discusses dual video and settings that worked.
 [http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358](http://askubuntu.com/questions/272570/unable-to-install-ubuntu-on-lenovo-y500/290358#290358)

[http://communities.intel.com/thread/34221](http://communities.intel.com/thread/34221)

 Also one used nolapic.
[http://ubuntuforums.org/showthread.php?t=2133816](http://ubuntuforums.org/showthread.php?t=2133816)


       Linux 3.2 To 3.8 Kernels With Intel Ivy Bridge Graphics
[http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1](http://www.phoronix.com/scan.php?page=article&item=intel_linux32_38&num=1)

---

### Post by pete_the_great on 2013-05-08
Thanks a lot for your help, but I'm still not having any success. There's no option to specify what graphics are used in the bios.

I've tried acpi_osi=Linux and acpi_backlight=off, and also acpi=off, but these all give the same blank screen. So does i915.modeset=1.

From the live cd, lshw gives the following
```
*-display UNCLAIMED     
       description: VGA compatible controller
       product: GK107M [GeForce GTX 660M]
       vendor: NVIDIA Corporation
       physical id: 0
       bus info: pci@0000:01:00.0
       version: a1
       width: 64 bits
       clock: 33MHz
       capabilities: pm msi pciexpress vga_controller cap_list
       configuration: latency=0
       resources: memory:f5000000-f5ffffff memory:e0000000-efffffff memory:f0000000-f1ffffff ioport:e000(size=128) memory:f6000000-f607ffff
  *-display
       description: VGA compatible controller
       product: 3rd Gen Core processor Graphics Controller
       vendor: Intel Corporation
       physical id: 2
       bus info: pci@0000:00:02.0
       version: 09
       width: 64 bits
       clock: 33MHz
       capabilities: msi pm vga_controller bus_master cap_list rom
       configuration: driver=i915 latency=0
       resources: irq:43 memory:f6400000-f67fffff memory:d0000000-dfffffff ioport:f000(size=64)
```

while lspci gives

```
00:00.0 Host bridge: Intel Corporation 3rd Gen Core processor DRAM Controller (rev 09)
00:01.0 PCI bridge: Intel Corporation Xeon E3-1200 v2/3rd Gen Core processor PCI Express Root Port (rev 09)
00:02.0 VGA compatible controller: Intel Corporation 3rd Gen Core processor Graphics Controller (rev 09)
00:14.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB xHCI Host Controller (rev 04)
00:16.0 Communication controller: Intel Corporation 7 Series/C210 Series Chipset Family MEI Controller #1 (rev 04)
00:1a.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #2 (rev 04)
00:1b.0 Audio device: Intel Corporation 7 Series/C210 Series Chipset Family High Definition Audio Controller (rev 04)
00:1c.0 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 1 (rev c4)
00:1c.1 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 2 (rev c4)
00:1c.2 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 3 (rev c4)
00:1c.3 PCI bridge: Intel Corporation 7 Series/C210 Series Chipset Family PCI Express Root Port 4 (rev c4)
00:1d.0 USB controller: Intel Corporation 7 Series/C210 Series Chipset Family USB Enhanced Host Controller #1 (rev 04)
00:1f.0 ISA bridge: Intel Corporation HM76 Express Chipset LPC Controller (rev 04)
00:1f.2 SATA controller: Intel Corporation 7 Series Chipset Family 6-port SATA Controller [AHCI mode] (rev 04)
00:1f.3 SMBus: Intel Corporation 7 Series/C210 Series Chipset Family SMBus Controller (rev 04)
01:00.0 VGA compatible controller: NVIDIA Corporation GK107M [GeForce GTX 660M] (rev a1)
03:00.0 Ethernet controller: Qualcomm Atheros Killer E2200 Gigabit Ethernet Controller (rev 13)
04:00.0 Unassigned class [ff00]: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
04:00.1 SD Host controller: Realtek Semiconductor Co., Ltd. RTS5209 PCI Express Card Reader (rev 01)
05:00.0 Network controller: Intel Corporation Centrino Wireless-N 135 (rev c4)
```

and hwinfo --framebuffer gives

```
> hal.1: read hal dataprocess 6943: arguments to dbus_move_error() were incorrect, assertion "(dest) == NULL || !dbus_error_is_set ((dest))" failed in file ../../dbus/dbus-errors.c line 282.
This is normally a bug in some application using the D-Bus library.
libhal.c 3483 : Error unsubscribing to signals, error=The name org.freedesktop.Hal was not provided by any .service files
02: None 00.0: 11001 VESA Framebuffer                           
  [Created at bios.464]
  Unique ID: rdCR.QgFYtsmQZBC
  Hardware Class: framebuffer
  Model: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  Vendor: "Intel Corporation"
  Device: "Intel(R) Sandybridge/Ivybridge Graphics Controller"
  SubVendor: "Intel(R) Sandybridge/Ivybridge Graphics Chipset Accelerated VGA BIOS"
  SubDevice: 
  Revision: "Hardware Version 0.0"
  Memory Size: 63 MB + 960 kB
  Memory Range: 0xd0000000-0xd3feffff (rw)
  Mode 0x0307: 1280x1024 (+1280), 8 bits
  Mode 0x031a: 1280x1024 (+2560), 16 bits
  Mode 0x031b: 1280x1024 (+5120), 24 bits
  Mode 0x0305: 1024x768 (+1024), 8 bits
  Mode 0x0317: 1024x768 (+2048), 16 bits
  Mode 0x0318: 1024x768 (+4096), 24 bits
  Mode 0x0312: 640x480 (+2560), 24 bits
  Mode 0x0314: 800x600 (+1600), 16 bits
  Mode 0x0315: 800x600 (+3200), 24 bits
  Mode 0x0301: 640x480 (+640), 8 bits
  Mode 0x0303: 800x600 (+832), 8 bits
  Mode 0x0311: 640x480 (+1280), 16 bits
  Mode 0x037d: 1920x1080 (+1920), 8 bits
  Mode 0x037e: 1920x1080 (+3840), 16 bits
  Mode 0x037f: 1920x1080 (+7680), 24 bits
  Config Status: cfg=new, avail=yes, need=no, active=unknown
```

so I guess the live cd is using the intel graphics (i915) without a problem. (Although I had to switch the BIOS into legacy mode to boot the live cd, otherwise I just get a black screen). 

I've also tried using vga=895 (I think this corresponds to the 24 bit 1920x1080), but that didn't work either.

---

### Post by oldfred on 2013-05-08
I found several threads in the MSI forum, but I do not know if they apply.

[http://forum-en.msi.com/index.php?topic=167582.msg1226666#msg1226666](http://forum-en.msi.com/index.php?topic=167582.msg1226666#msg1226666)

---

