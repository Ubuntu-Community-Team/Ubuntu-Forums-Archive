---
title: "Problem installing Ubuntu 18.04 on NVMe"
date: 2018-04-29
forum: Installation &amp; Upgrades
---

### Post by walter-i on 2018-04-29
Hi,

there seems to be an issue installing 18.04 on an NVMe (Samsumg 960 Evo).
I just purchased it and I thought I'd take the opportunity to jump to 18.04.

I have a USB drive with the image; it booth properly, Grub asks if I want to choose between 18.04 and 18.04 with acpi off.
Both of them yield the same result: the installer cannot determine the size of the disk's sectors, goes to the default of 63 and then it pretty much hangs there.

Not sure what to do.

The PC's config, if needed:
- MSI Tomahawk B350 with Ryzen R5 1600
- 16Gb of RAM
- GPU R9 270
- 500GB 960 Evo

Suggestions?

Thanks,
W.

Edit: image> [https://ubuntuforums.org/attachment.php?attachmentid=279512&d=1525116429](https://ubuntuforums.org/attachment.php?attachmentid=279512&d=1525116429)

---

### Post by linux4me on 2018-04-29
The first thing I'd do is make sure you have the most recent BIOS for that MB. I see [on the MSI site]("https://www.msi.com/Motherboard/support/B350-TOMAHAWK") that they released v. 7A34v1G of the BIOS on 3/20/2018, which includes "Improved M.2 device compatibility." That could be the solution right there if you aren't using that version of the BIOS: flash to the latest version of the BIOS and re-try a fresh install of 18.04.

---

### Post by oldfred on 2018-04-29
Also 63 does not sound right for sectors.

 [http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary](http://askubuntu.com/questions/156994/partition-does-not-start-on-physical-sector-boundary)
Since drives became over 8GB CHS cylinders, heads, sectors has been obsolete and LBA is how drive is configured. For more compatibility with newer drives, 4k drives, SSDs and better configuration, partitions now start at sector 2048 rather than rounding to cylinders. With 512 bytes per sector that is 1MB at the beginning of the drive. 

      
 First, understand that most partitioning tools have moved to a policy of aligning partitions on 1 MiB (2048-sector) boundaries as a way of improving performance with some types of arrays and some types of new hard disks (those with 4096-byte physical sectors). 
[https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/](https://www.ibm.com/developerworks/linux/library/l-linux-on-4kb-sector-disks/)
[http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/](http://www.ibm.com/developerworks/linux/library/l-4kb-sector-disks/)
Post on 8-sector boundaries alignment by srs5694
[http://ubuntuforums.org/showthread.php?t=1685666](http://ubuntuforums.org/showthread.php?t=1685666)

---

### Post by P-I H on 2018-04-30
I have about the same configuration[COLOR=#000000]
[/COLOR]```
p-i@pi-MS-7A34:~$ inxi -F
System:    Host: pi-MS-7A34 Kernel: 4.15.0-20-generic x86_64 bits: 64
           Desktop: Gnome 3.28.1 Distro: Ubuntu 18.04 LTS
Machine:   Device: desktop Mobo: Micro-Star model: B350 TOMAHAWK (MS-7A34) v: 1.0 serial: N/A
           UEFI: American Megatrends v: 1.90 date: 09/19/2017
CPU:       8 core AMD Ryzen 7 1700 Eight-Core (-MT-MCP-) cache: 4096 KB
           clock speeds: max: 3743 MHz 1: 3004 MHz 2: 3007 MHz 3: 3004 MHz
           4: 3027 MHz 5: 3027 MHz 6: 3036 MHz 7: 3019 MHz 8: 3006 MHz
           9: 3287 MHz 10: 3005 MHz 11: 3018 MHz 12: 3006 MHz 13: 2996 MHz
           14: 2999 MHz 15: 3581 MHz 16: 3743 MHz
Graphics:  Card: Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 470/480/570/580]
           Display Server: x11 (X.Org 1.19.6 ) driver: amdgpu
           Resolution: 2560x1440@143.99hz
           OpenGL: renderer: Radeon RX 580 Series (POLARIS10 / DRM 3.23.0 / 4.15.0-20-generic, LLVM 6.0.0)
           version: 4.5 Mesa 18.0.0-rc5
Audio:     Card-1 Advanced Micro Devices [AMD/ATI] Ellesmere [Radeon RX 580]
           driver: snd_hda_intel
           Card-2 C-Media CMI8788 [Oxygen HD Audio] driver: snd_virtuoso
           Card-3 Logitech Webcam C250 driver: USB Audio
           Sound: Advanced Linux Sound Architecture v: k4.15.0-20-generic
Network:   Card: Realtek RTL8111/8168/8411 PCIE Gigabit Ethernet Controller
           driver: r8169
           IF: enp33s0 state: up speed: 1000 Mbps duplex: full
Drives:    HDD Total Size: 740.2GB (14.9% used)
           ID-1: /dev/nvme0n1 model: Samsung_SSD_960_EVO_250GB size: 250.1GB
           ID-2: /dev/sda model: SanDisk_Ultra_II size: 240.1GB
           ID-3: /dev/sdb model: Samsung_SSD_850 size: 250.1GB
Partition: ID-1: / size: 228G used: 103G (48%) fs: ext4 dev: /dev/nvme0n1p2
RAID:      No RAID devices: /proc/mdstat, md_mod kernel module present
Sensors:   System Temperatures: cpu: 34.0C mobo: 35.0C gpu: 36.0
           Fan Speeds (in rpm): cpu: N/A fan-1: 555 fan-2: 486 fan-3: 1011 fan-4: 0 fan-5: 742
Info:      Processes: 497 Uptime: 50 min Memory: 2431.0/16053.6MB
           Client: Shell (bash) inxi: 2.3.56 
p-i@pi-MS-7A34:~$
```
This was on a system with Ubuntu 17.10 installed on the NVMe disk. The installation hanged when I used "Erase disk and install Ubuntu"
I had to use "Something else" and select the partition to use for the installation.
I'm using the 1.9 BIOS from end of March which I think is the best one so far.
Perhaps you need to format the NVMe disk before the installation.

---

### Post by walter-i on 2018-04-30
Hi everyone,

I have the latest BIOS, and since I dual-boot, I already installed Windows without issues, so I don't think there's a specific problem with the HW/Bios.
I will take a photo of the messages when I load the USB key, and post it later today.

W.

---

### Post by walter-i on 2018-04-30
Here's what happens when I try to boot the USB key.
I hope you can open the attachment.

W.

---

### Post by rbmorse on 2018-04-30
Machine looks like it's trying to boot from an optical disk (iso9660_Joliet).  Did you just copy the .iso file to the USB drive or did you use a startup drive creator utility to put Ubuntu on the flash drive?

---

### Post by walter-i on 2018-05-01
I used Yumi to create the pendrive...
I tried also with Etcher but it die not work (the USB key showed having only a few bytes and was not bootable.
Should I use a different software?

---

### Post by ajgreeny on 2018-05-01
If you have an installation of *ubuntu somewhere that you can run, try using [mkusb]("https://help.ubuntu.com/community/mkusb") to create the bootable USB, and in view of your comments about the USB key it is also probably worth trying another one; that one may be corrupt in some way.

---

### Post by walter-i on 2018-05-01
OK, so I deep-formatted the USB key, re-downloaded the iso and re-run Yumi.
Now it goes one step further: I see the page that lets me choose if run Ubuntu from USB key, or install, or ...
After a couple of seconds, kernel panic (see attached screenshot).

I tried with a different USB key: same result.

Any clue?

W.

---

### Post by oldfred on 2018-05-01
May not be issue, but there probably is a newer UEFI, which you should install.

UEFI: American Megatrends v: 1.90 date: 09/19/2017

Have you tried nomodeset boot parameter.
At grub menu you can use e for edit, scroll to linux line and replace quiet splash with nomodeset.
 How to set NOMODESET and other kernel boot options in grub2 - both BIOS liveCD & grub first boot ( also UEFI with grub) 
How to add boot parameters,  grub menu after install (also grub when UEFI)
[https://wiki.ubuntu.com/Kernel/KernelBootParameters](https://wiki.ubuntu.com/Kernel/KernelBootParameters)
[https://help.ubuntu.com/community/Grub2](https://help.ubuntu.com/community/Grub2)
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

### Post by walter-i on 2018-05-01
Hi oldfred,

i edited the grup.cfg and replaced "quiet splash" with nomodeset. Same result.
I also found that other occurrences of kernel panic were solved by adding "selinux = 0", which I did, but it also made no difference.

I don't know how would I install the newer UEFI: I am using the latest BIOS, and I have checked that it allows booting UEFI+Legacy (as opposed to only UEFI).
Where would I download/install the updated UEFI?

Thank you for the help: it is appreciated.
W.

---

### Post by oldfred on 2018-05-01
You get the latest UEFI from your vendor.
They normally have a drivers & updates page. Drivers are almost always just Windows, but BIOS/UEFI is for entire system regardless of operating system.
My motherboard has three ways to update. From inside Windows, from FAT32 flash drive with DOS, and directly from within UEFI reading update file from any FAT32 partition. I typically copy into a new folder in my ESP or sometimes to flash drive.

The Intel issue for KPTI/Retpoline for Meltdown/Spectre mitigation or other changes     has required all vendors to update UEFI and all operating systems to update kernels.

---

### Post by walter-i on 2018-05-01
I have the latest BIOS installed (rev G).That's the only update that should matter in this case: the rest of the drivers are for Windows only.
I have never had such issues when installing Ubuntu (or any Distro, for that matters) via USB. It is really odd and I cannot get my head around what could be going wrong.
I think I'm going to try with another distro to see if the issue is specific to Ubuntu 18.04, or if it is more likely related to my hardware. Still, I have been running 16.04 for ... well, 2 years and I was looking forward to jump to 18.04 and Gnome: never really got to like Unity.

---

### Post by DonA on 2018-05-01
I'm having a similar problem.  My Lenovo P50s has a single ~250GB SSD.  I had 16.04 LTS installed on the SSD, but wiped it while trying to install 18.04 LTS.  (I seem to recall having to do some gyrations during the 16.04 install a couple years back, but I can't remember the successful incantation now.) When I boot from the 18.04 Live USB, the only disk that is recognized is the USB itself, no SSD.  But if I boot GParted Live, it sees the SSD just fine.  I'm trying to figure out what GParted Live is doing that 18.04 Live is not.  I've also tried the nomodeset with no difference.

---

### Post by linux4me on 2018-05-01
> **walter-i said:**
> I have the latest BIOS installed (rev G).That's the only update that should matter in this case: the rest of the drivers are for Windows only.
I have never had such issues when installing Ubuntu (or any Distro, for that matters) via USB. It is really odd and I cannot get my head around what could be going wrong.
I think I'm going to try with another distro to see if the issue is specific to Ubuntu 18.04, or if it is more likely related to my hardware. Still, I have been running 16.04 for ... well, 2 years and I was looking forward to jump to 18.04 and Gnome: never really got to like Unity.

I just tried installing Ubuntu 18.04 on my Dell laptop, which has a 250 GB M.2 Samsung 860 Evo SSD. Other than that laptop's usual issues with its nVidia Optimus graphics, the SSD was recognized and Ubuntu installed just fine. I guess that rules out the distro as the cause, and makes it seem more likely its particular to your other hardware/firmware.

---

### Post by walter-i on 2018-05-11
I tried with Linux Mint and no luck. Totally different errors (something "not found"). It seems to me that the installer is having a hard time finding my m.2 disk.
I am not familiar with Grub4Dos so I am not sure how to move forward ...

---

### Post by oldfred on 2018-05-11
Where are you getting grub4dos? 
Extremely old, used to boot using Windows BIOS boot loader to boot a BIOS install, years ago. Not recommended. may not even know about NVMe? And you probably want UEFI boot, anyway.

Grub2 was updated in 2014 to support NVMe drives.

---

### Post by walter-i on 2018-05-12
> **oldfred said:**
> Where are you getting grub4dos? 


I'm using Yumi from Pendrivelinux to create the prendrive. Should I use a different one? I am using 2.0.0.5, non-UEFI (the UEFI is beta, so I thought it would be less stable).
Should I build it in a different way?

---

### Post by oldfred on 2018-05-12
UEFI may be beta as it requires lots of updates for Meltdown & Spectre. Both UEFI & all operating systems need updates.

 MSI Tomahawk B350 with Ryzen R5 1600 New UEFI required
[https://ubuntuforums.org/showthread.php?t=2390475](https://ubuntuforums.org/showthread.php?t=2390475)
ASUS PRIME B350M-E major issues
[https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux](https://www.phoronix.com/scan.php?page=news_item&px=AMD-Raven-Ridge-Mobo-Linux)

Did not know pendrive used grub4dos. Most installers use syslinux for BIOS boot or grub for UEFI boot.
       
 Lots of info on USB boot for installing
[https://help.ubuntu.com/community/Installation/FromUSBStick](https://help.ubuntu.com/community/Installation/FromUSBStick) 
           
 Most find this works:
[https://help.ubuntu.com/community/mkusb](https://help.ubuntu.com/community/mkusb)
[https://wiki.ubuntu.com/Win32DiskImager/iso2usb](https://wiki.ubuntu.com/Win32DiskImager/iso2usb)

Note that installers that use dd or dd under the hood, do not create standard formatted flash drives & erase entire flash drive. You have to then erase beginning of drive, to allow partitioning tools to see it correctly and allow you to partition & format it again.

---

### Post by P-I H on 2018-05-13
As I wrote before I have the same motherboard and had also problem to install on the NVMe disk, actually the same as you have.
This is what I did
- downloaded the 18.04 ISO from [http://releases.ubuntu.com/18.04/](http://releases.ubuntu.com/18.04/)
- copied the ISO to an USB with sudo dd if=/home/user-name/Downloads/ubuntu-18.04-desktop-amd64.iso of=/dev/sdx
the x depends on the number of drives. The NVMe is  /dev/nvme0n1p1nd, the 960 Evo is /dev/sda and the USB will most likely be /dev/sdb. Be very careful as the dd command overwrites everything on a disk. It's perhaps best to disconnect all disks and only keep the NVMe. In this case the USB stick will be /dev/sda. 
- booted the ISO. Boot Mode Select in BIOS settings is set to "Legacy+UEFI" and Grub boots in UEFI mode. 
- Erase Disk and install Ubuntu didn't work and I had to use the Something else method.

---

### Post by walter-i on 2018-05-20
I booted using my old SSD on Ubuntu 16.04. I'm creating the USB key as you suggested: I will post results...

---

### Post by walter-i on 2018-05-23
Indeed, no issues with the USB created with Ubuntu. Thanks!

---

