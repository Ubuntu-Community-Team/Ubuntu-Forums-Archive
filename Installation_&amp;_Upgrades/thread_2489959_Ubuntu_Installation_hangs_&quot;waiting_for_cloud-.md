---
title: "Ubuntu Installation hangs &quot;waiting for cloud-init... \&quot;"
date: 2023-08-16
forum: Installation &amp; Upgrades
---

### Post by jinglenose on 2023-08-16
To install Ubuntu I downloaded the iso file onto my Linux Mint desktop and burned it onto a USB.
I entered the bios of my new PC and set it to boot off the USB with secure boot disabled.
I then put the USB into my newly built PC and it booted.
The Ubuntu menu came up OK and I chose "Try or Install Ubuntu".
The machine listed lots of OKs and then posted the message...

"
Starting Time & Date Service
Ubuntu 22.04.2 LTS ubuntu-server tty1
connecting...
waiting for cloud-init... \
"

Then machine then does absolutely nothing else and the install halts.

The USB drive is a Kingston 32GB drive placed in the USB 2.0 ports which I believe do not need drivers.

I tried formatting it before I burned the image and it makes no difference.

I can't find anyone else with this error.

Any ideas why this would be? 

Any help would be greatly appreciated.

The machine is a brand new custom build and has the following hardware:

[TABLE]
[TR]
[TD="align: left"][AMD Ryzen 9 5950X Processor (16C/32T, 72MB Cache, Up to 4.9 GHz Max Boost)]("https://www.amazon.co.uk/AMD-Ryzen-5950X-Processor-Cache/dp/B0815Y8J9N/ref=sr_1_1?keywords=AMD+Ryzen+9+5950X+Processor+%2816C%2F32T%2C+72MB+Cache%2C+Up+to+4.9+GHz+Max+Boost&s=computers&sr=1-1")

[TABLE]
[TR]
[TD="align: left"][MSI MAG X570S TOMAHAWK MAX WIFI]("https://www.amazon.co.uk/MSI-TOMAHAWK-Motherboard-Channel-Bluetooth/dp/B09BYZ9J93/ref=sr_1_4?keywords=MSI+MAG+X570S+TORPEDO+MAX+wifi&s=computers&sr=1-4")

[TABLE]
[TR]
[TD="align: left"][Crucial Pro RAM]("https://www.amazon.co.uk/Crucial-2x32GB-3200MT-Desktop-CP2K32G4DFRA32A/dp/B0C29W4G29/ref=sr_1_1_sspa?keywords=64GB+DDR4+RAM&s=computers&sr=1-1-spons&sp_csd=d2lkZ2V0TmFtZT1zcF9hdGY&psc=1") [TABLE]
[TR]
[TD="align: left"]2x32GB DDR4 RAM

[TABLE]
[TR]
[TD="align: left"][Generic AMD chipset]("https://www.amazon.co.uk/Dilwe-Computer-Graphics-Express-Desktop-default/dp/B095319YG5/ref=d_dp-upsell-widget_sccl_4_2/262-1075965-5221415?content-id=amzn1.sym.6a8bf132-c500-4b85-9b7c-a82353db78fa&pd_rd_i=B08RNV7D22&th=1") Dilwe HD6450 Graphics Card, 2G 64bit DDR3 Graphics.

be quiet! BN283 Straight Power 11 750W ATX Power Supply

For now I have one Crucial PCIe Gen 3 2TB SSD in the M.2 slot.  The BIOS sees this OK.
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]
[/TD]
[/TR]
[/TABLE]

---

### Post by MAFoElffen on 2023-08-16
Why are you using Server 22.04.2, instead of 22.04.3?

Did you verify the checksum of the image before burning to USB? Because the cloud-init is on the image, so if there is a problem with that... Just saying.

How did you burn the image to the USB?

You have very new hardware. Did you use the Grub2 Menu's second option to install with HWE Kernel?

---

### Post by jinglenose on 2023-08-16
Hi MAFoElffen,

Thanks for trying to help.  I went away on holiday and forgot to mention that I tried 22.04.3 first and it has the same problem.  I also tried HWE Kernel and it dumps a load of stuff ending in the message "End kernel panic - not syncing: Attempted to kill the idle task!"  and then halts the install.

Any ideas what I can try next?

---

### Post by MAFoElffen on 2023-08-18
Actually, I'm looking to see what may be going on.

I know that Ubuntu Server 20.04 and 22.04 will run on AMD Ryzen 9 5950X CPU's. I know that User's have run Ubuntu Desktop 20.04 on that motherboard. 

The Radeon HD 6450 Graphics card technology is very 'dated'... Considered Legacy, with support for it from AMD stopping about 3-4 years ago.
[quote=AMD]
This product has been moved to a legacy support model and no additional driver releases are planned.
[/quote]
At the Grub2 Boot menu, if you press the <E> key, <Arrow-Down> to the line that starts with "linux", at the end of that line, add "radeon.modeset=0"

---

### Post by jinglenose on 2023-08-26
Hi, thanks for your suggestions.  I've been on holiday hence the delay.

The graphics card is really basic because I only want it to use four lanes, the other 16 lanes I want to use for a PCIe RAID array as I want to use the machine as a database server.  I never thought to check if it was still supported, I thought they would have stopped selling it.  The RAID array appears to be recognised by the BIOS when I put it in but I have removed it to try and simplify the problem.
I guess I could get a newer supported graphics card with say 8 lanes and then limit it to four lanes by putting it in the second PCIe slot that only has four lanes?
[IMG]https://drive.google.com/file/d/1JATpktkGuvXIZeXlbiOBbiNh9ZpOMXtN/view?usp=drive_link[/IMG]

I also tried different USB ports and a USB-C SSD with very similar results... "[end Kernel panic - not syncing: Fatal exception in interrupt]..."

I have tried adding the line "radeon.modeset=0" and it goes around in a loop ending in the image attached...[https://drive.google.com/file/d/1JATpktkGuvXIZeXlbiOBbiNh9ZpOMXtN/view?usp=drive_link](https://drive.google.com/file/d/1JATpktkGuvXIZeXlbiOBbiNh9ZpOMXtN/view?usp=drive_link)

Not sure how to upload an image on here seems tricky.

---

### Post by jinglenose on 2023-08-26
[It looks like AMD 6450 should run fine on Ubuntu Server 20.04]("https://askubuntu.com/questions/1334658/amd-drivers-for-ubuntu-20-04-64-bit#:~:text=The%20first%20output%20suggests%20that,%2D14%2D12%2Dx86."), I have the same problem with that version since it was the first version of Ubuntu I tried.

---

### Post by jinglenose on 2023-08-27
OK it looks like I fixed it.  

When I originally tried to set up the PCIe RAID array it wouldn't work so I fiddled with associated settings.  I changed the setting "PCI_Ex Gen Switch" selection mode from Auto to PCIe 4.0 in an attempt to get things to work.  This apparently causes problems with the PCIe 3.0 graphics card but not enough to mean it does't work just enough to cause major problems later on.

I reset the BIOS to the factory default, set secure boot off, fast boot off and I disabled "Trusted Computing" (TPM stuff) and the installer for Ubuntu Server 22.04 ran just fine. System now boots into command line interface.

:guitar:

---

### Post by MAFoElffen on 2023-08-27
Glad to see you found the solution to your issues. Please mark this as "Solved".

Just to clarify and gather my own information on this, because I try to support the Users that come here with issues... What was the motherboard? Are you using BIOS PCIe bifurcation?  Were you using that to implement software RAID (mdadm) or BIOS RAID on that board? (It read as it is was the BIOS implemented RAID)

Personally- IMHO, the Vendor's BIOS RAID implementations didn't work for me. They were not true hardware RAID, like LSI MegaRAIID controllers, but still a type of fakeRAID implementation. Linux mdadm has been around for a long time in production servers. LVM2 RAID uses mdadm with it's own extensions. ZFS RAIDz is what I am using now, and am very happy.

---

