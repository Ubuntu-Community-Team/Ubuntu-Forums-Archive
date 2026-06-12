---
title: "Installing Ubuntu 22.04 alongside Windows 11"
date: 2022-10-08
forum: Installation &amp; Upgrades
---

### Post by maglin2 on 2022-10-08
I have a windows 11 desktop and would like to dual boot Ubuntu 22.04 alongside.
I have shrunk Windows C drive and made free space.
I am uncertain about how to install though. EFI is completely unfamiliar to me. (So is Windows come to that, so fouling it up during Ubuntu install and having to reinstall it would be a pain).

1. Do I need to create another EFI partition in the Ubuntu install? Some guides say so, but the link out to the install alongside Windows guide from the Ubuntu Install Tutorial makes no mention [https://ubuntu.com/tutorials/install-ubuntu-desktop#6-drive-management](https://ubuntu.com/tutorials/install-ubuntu-desktop#6-drive-management). It is a little dated though.
Can I just create an ext4 primary / partition for Ubuntu install and let everything (including Home and Swap folder) be put in there?

2. Do I need to turn off Secureboot in EFI? (This option doesn't actually exist in my EFI, but I can alter it from Windows to 'Other OS'.).
Thanks in advance
Dave

---

### Post by oldfred on 2022-10-08
Only one ESP -efi system partition per drive/device.
So if on same drive as Windows, installer will auto find existing ESP and use it.
Installer now uses swap file by default. If you want swap partition, you have to create it yourself using the Something Else manual install option.

If you want separate /home partition, you also have to use Something Else. Default install is just / (root) using all available space. Or some options use entire drive, erasing all other installs. I prefer something else so I can see exactly what is where, but you have to have some idea of what partitions are and sizes you want. I also use data partition, and if using Windows two data partitions, one NTFS and one ext4. I do not use snaps, but default now is snaps & you need a bit larger / as they are each larger than a standard .deb type app version.

Other OS is the Secure boot setting. My older early UEFI system said if installing Windows 7, you had to use Other OS as Windows 7 did not support UEFI Secure Boot.

---

### Post by maglin2 on 2022-10-09
Thanks oldfred. I found your UEFI tutorial thread after posting this.

I've got a Windows recovery USB. I'll make a system image (I think that's still supported - I haven't used Windows since  Windows 7 in 2012) and then give it a go. (By the way, you sorted out a dual boot issue for me back then too!)

The 22.04.1 live USB boots to a black screen (it has loaded though, I can hear the Try/Install screen jingle). Nomodeset gives graphics (though wrong format and low resolution). 

The CPU (CPU Intel® Core&#8482; i3-10100    3.60GHz) and integrated graphics  (Intel® UHD Graphics 630) seem to be supported  for Ubuntu, so I live in hope that an install might correct that.

Thanks again 
Dave

---

### Post by maglin2 on 2022-10-09
The install didn't go too well.
The not bad news is that Windows still boots.
Ubuntu 22.04 still boots to black screen unless I use nomodeset. Then the format and resolution of the graphics are wrong.
Key info (I think) from LSHW is
*-display UNCLAIMED
             description: VGA compatible controller
             product: CometLake-S GT2 [UHD Graphics 630]
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 03
             width: 64 bits
             clock: 33MHz
             capabilities: pciexpress msi pm vga_controller bus_master cap_list
             configuration: latency=0
             resources: iomemory:600-5ff iomemory:400-3ff memory:6000000000-6000ffffff memory:4000000000-400fffffff ioport:5000(size=64) memory:c0000-dffff
  *-memory UNCLAIMED
             description: RAM memory
             product: Tiger Lake-H Shared SRAM
             vendor: Intel Corporation
             physical id: 14.2
             bus info: pci@0000:00:14.2
             version: 11
             width: 64 bits
             clock: 33MHz (30.3ns)
             capabilities: pm cap_list
             configuration: latency=0
             resources: iomemory:600-5ff iomemory:600-5ff memory:6001114000-6001117fff memory:600111b000-600111bfff

*-serial:2 UNCLAIMED
             description: Serial bus controller
             product: Tiger Lake-H SPI Controller
             vendor: Intel Corporation
             physical id: 1f.5
             bus info: pci@0000:00:1f.5
             version: 11
             width: 32 bits
             clock: 33MHz
             configuration: latency=0
             resources: memory:a0504000-a0504fff

About in Settings gives graphics as llvmpipe (LLVM 13.0.1, 256 bits). Should be Intel 630, which should be supported.

Checking for additional drivers yields nothing.

The install was done with Secureboot set to Other OS. Fastboot was off.

Any help or thoughts much appreciated.

Thanks
Dave
  
PS - after a bit more googling I wonder if I might need an OEM kernel? There is mint post suggesting that, albeit for 20.04 [https://forums.linuxmint.com/viewtopic.php?f=49&t=350311](https://forums.linuxmint.com/viewtopic.php?f=49&t=350311)

---

### Post by ubfan1 on 2022-10-09
You might have to enable the "restricted" software source from the Software & Updates to get the Proprietary Nvidia drivers to show up.  Checkoff that box, run a sudo apt-get update, then see if "Additional Drivers" shows more.

---

### Post by maglin2 on 2022-10-09
I'm a bit puzzled by that. I may be misunderstanding, but my impression is that this is an Intel cpu and Intel integrated graphics. I don't see how Nvidia drivers would be involved?

---

### Post by oldfred on 2022-10-09
Have you updated UEFI firmware?

I have both a 12th gen desktop Intel system and a 11th Gen Intel laptop dual booting.
Both installed & worked with 22.04 and and defaulted to standard i915 driver.
Not sure why a 10th gen Intel video would not work.

---

### Post by ubfan1 on 2022-10-09
Symptoms are similar to when Nvidia HW is booted with the nouveau drivers but the "nomodeset" is not given.  Any other proprietary drivers might show up.  I too have an 11th Gen Intel but with Nvidia, so I cannot say I've ever used the i915 driver.

---

### Post by maglin2 on 2022-10-10
> **oldfred said:**
> Have you updated UEFI firmware?

I have both a 12th gen desktop Intel system and a 11th Gen Intel laptop dual booting.
Both installed & worked with 22.04 and and defaulted to standard i915 driver.
Not sure why a 10th gen Intel video would not work.

That's something I still need to figure out how to do. My last machine was far too old to get BIOS updates! Never done EFI updates before.
It's a new machine. ASUS BIOS Utility. Motherboard ASUS® H510T2. The BIOS build date is given as 05/07/22 version 1601.
ME FW Version (which I'm guessing is another firmware aspect) is 15.0.21.1549.

Edit - having just checked ASUS website version 1601 (Issued 24/05/22) seems to be latest version.

---

### Post by oldfred on 2022-10-10
One of my UEFI system, when reading the manual had a video setting, but did not seem to say video anywhere in description.
Check UEFI settings for any sort of video mode setting.

---

### Post by maglin2 on 2022-10-10
OK, I'll have a look through for anything likely. A lot of the ACRONYM entries in the Advanced pages of UEFI are pretty incomprehensible to me though!

I tried the OEM kernel. Same result. Black screen if nomodeset not specified.

---

### Post by maglin2 on 2022-10-10
The manual for this motherboard, ASUS® H510T2, only seems to be available in Simplified Chinese (US and UK support sites)!

Looking through the UEFI entries the only obvious graphics settings I came across were for Render standby (enabled) and Pre-allocated graphics memory size - set at 32M.

---

### Post by maglin2 on 2022-10-12
Also tried Fedora Live USB. Just the same - black screen when graphics load.
Further suggestions welcomed - on different approach, or as to what I might be doing wrong (not at all unlikely).
Otherwise until/unless Intel/Ubuntu resolve issues with i915 driver loading with i3-10100 cpu I guess I'll have to learn to love Windows 11. Might test my temper!

---

### Post by oldfred on 2022-10-12
I believe Asus has not changed UEFI a lot, just added some new features.
My old Z-97 then my be similar?

Asus z97 screenshots:
[http://ubuntuforums.org/showthread.php?t=2258575&page=2](http://ubuntuforums.org/showthread.php?t=2258575&page=2)

Reviewing that manual I see VT-D and a variety of settings. Most are auto but one says auto, CPU graphics, PCIe & PCI. I might see if you have those and try different settings.

I did convert from nVidia to Intel video as old nVidia card was lower performance. But that was several years ago & that system died the beginning of Summer.

---

### Post by maglin2 on 2022-10-13
The only mention of CPU graphics is set to auto and greyed out. 
VT-d is enabled.
PCIe has some options to do with power, speed and clock gating, but I am very reluctant to fiddle with them, not having any idea what the result might be.
There are some discussions online about i915 not finding the right display port.
I am out of my depth with this, but is there anything I might do interrogating the current (nomodeset) install to produce useful diagnostic info?

---

### Post by oldfred on 2022-10-13
Bit older, most discussion seemed to be about newer kernel which 22.04 would have.
Not sure if other comments may help?
[https://ubuntuforums.org/archive/index.php/t-2459881.html](https://ubuntuforums.org/archive/index.php/t-2459881.html)

---

### Post by maglin2 on 2022-10-14
Thanks oldfred.

For the time being I'm going to forget Linux on this machine and just run it with Windows. I need  a Windows machine for some applications anyway.

My initial upgrade intention was a Linux Desktop and a Windows Laptop. It now seems I will have a Windows Desktop and a Linux Laptop for the foreseeable future, but I can live with that.

I'll try Ubuntu on it occasionally just in case whatever issue applies is resolved by an update.

Dave

---

### Post by maglin2 on 2022-10-15
Well here's an odd (but pleasing) thing.

I put a PCLinuxOS LiveUSB in and it works! (Without safe mode or nomodeset)

```
[FONT=monospace][COLOR=#000000][guest@localhost ~]$ inxi -G [/COLOR]
[COLOR=#5454ff]**Graphics:**[/COLOR][COLOR=#000000] [/COLOR]
  [COLOR=#5454ff]**Device-1:**[/COLOR][COLOR=#000000] Intel CometLake-S GT2 [UHD Graphics 630] [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] i915 [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] kernel [/COLOR]
  [COLOR=#5454ff]**Display:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**server:**[/COLOR][COLOR=#000000] X.org [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 1.21.1.4 [/COLOR][COLOR=#5454ff]**driver:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**X:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**loaded:**[/COLOR][COLOR=#000000] intel,v4l [/COLOR][COLOR=#5454ff]**gpu:**[/COLOR][COLOR=#000000] i915 [/COLOR]
    [COLOR=#5454ff]**resolution:**[/COLOR][COLOR=#000000] 1920x1080~60Hz [/COLOR]
  [COLOR=#5454ff]**OpenGL:**[/COLOR][COLOR=#000000] [/COLOR][COLOR=#5454ff]**renderer:**[/COLOR][COLOR=#000000] Mesa Intel UHD Graphics 630 (CML GT2) [/COLOR][COLOR=#5454ff]**v:**[/COLOR][COLOR=#000000] 4.6 Mesa [/COLOR]
    22.1.7 
[guest@localhost ~]$ 

[/FONT]
```

SO maybe I won't give up just yet!

---

### Post by maglin2 on 2022-10-16
PCLinuxOS latest liveusb ships with kernel 5.19.6, so I guess Ubuntu 22.10 might get there fairly soon. Beta is on 5.19.0. I'll wait and see.

Update: :rolleyes:22.10 Beta works!:P

---

### Post by maglin2 on 2022-10-20
Confirm graphic driver issue with this CPU (Intel® Core&#8482; i3-10100) resolved in kernel 5.19. Running Kubuntu 22.10.

---

