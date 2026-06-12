---
title: "Strange installation behavior, NVME seen by Win/Mint/Deb but not Ubuntu"
date: 2024-03-14
forum: Installation &amp; Upgrades
---

### Post by flea77 on 2024-03-14
I am pretty new to Linux so if there is something obvious I miss, please don't be too harsh, student driver here.

I have a Dell Precision 5520 i5 7th gen 8GB with either a 256GB or 512GB NVME SSD (more on that later).

The laptop had Windows 10 on it, ran fine. Wanted to convert to Ubuntu 23.10.1. Created USB drive and sometimes the USB drive gives me an error while in Gnome and I can click to make it go away or report it, I have done both. The error never seems to affect anything until I do an install. 

I had a devil of a time getting the installer to see the NVME. Launching Disks sees it but tells me No Media. Launching Gparted does not show the NVME at all but does show the USB.

After jacking with that for hours, even replacing the old Samsung 256GB NVME with a brand new Samsung 980 512GB, I finally got it to start the install at which point it promptly crashed and failed the installation. I even tried multiple USBs and verified the image by using it to install on other computers and VMs without issue.

Just for giggles I made a USB for Debian 12 and installed it, without a single hitch. Then to confuse the situation even further, I made a USB for MINT 21.3 and installed it, again, without a single issue.

At this point, after installing two different Linux distros without a problem, I attempted Ubuntu again and had the same issue where it does not see/can not deal with the NVME.

In the bios Secure boot is off, SATA is set to AHCI although I have tried RAID just for grins. Also, boot is set to UEFI.

I would really prefer to run Ubuntu but I have no idea where to go from here, and unfortunately am so new I don't even know intelligent questions to ask. Any pointers or help would be greatly appreciated.

---

### Post by oldfred on 2024-03-14
Have you updated UEFI firmware to latest version & SSD firmware, also?
Many needed those updates for Ubuntu to see the drives.

Compare firmware version to vendors support page for your system.
udisksctl status
inxi -d

From my older focal install on desktop:
```
fred@z170-focal-k:~$ udisksctl status
MODEL                     REVISION  SERIAL               DEVICE
--------------------
Samsung SSD 970 EVO Plus 500GB 2B2QEXM7  S4P2NF0M514514L      nvme0n1 
HGST HTS721010A9E630      JB0OA3J0  JR10004M0M0V8E       sda     
Samsung SSD 850 EVO       EMT2      000000123ACC         sdb     


```

How to update Samsung:
[https://wiki.archlinux.org/index.php/Solid_state_drive](https://wiki.archlinux.org/index.php/Solid_state_drive) & 
[https://www.samsung.com/semiconductor/minisite/ssd/download/tools/](https://www.samsung.com/semiconductor/minisite/ssd/download/tools/)
Look at firmware, not Magician which is Windows.

But my Dell 5310 with Intel 11th gen Intel chip just worked.
I forgot to change to AHCI which I have suggested to many. And still had Secure boot on.
It installed without issue, but used Intel® VMD driver for NVMe drive. I had not seen that before but it was available in kernel for  a while. Not sure Ubuntu included it until 22.04.

---

### Post by flea77 on 2024-03-14
I checked the SSD's firmware and it matches what Samsung says is the latest. 

I checked my Dell BIOS and there was an update, ran the update, booted to Ubuntu USB afterwards and have the exact same issue.

---

### Post by oldfred on 2024-03-14
Do you have a small Optane drive?

Similar but older thread
[https://ubuntuforums.org/showthread.php?t=2436198](https://ubuntuforums.org/showthread.php?t=2436198)

Is fast boot in UEFI off
Is fast startup in Windows off, and if bitlocker is that off?

---

### Post by flea77 on 2024-03-15
Optane? Not that I have seen. Dell also says that in their computers NVMe can not be accelerated with Optane so I dont see why someone would install one [https://www.dell.com/support/kbdoc/en-us/000132484/how-to-install-an-intel-optane-m-2-nvme-accelerator-into-your-existing-dell-optiplex-inspiron-precision-and-alienware-systems](https://www.dell.com/support/kbdoc/en-us/000132484/how-to-install-an-intel-optane-m-2-nvme-accelerator-into-your-existing-dell-optiplex-inspiron-precision-and-alienware-systems)

I have not gone through everything in that linked thread but I did see that Enable Legacy Option ROMs was supposed to be set to off so I made that change.

Fast boot in UEFI has three options: Minimal, Thorough, and Auto. It was set to Thorough and I also tried Auto.

There is no Windows. The currently installed SSD went from brand new to Linux.

After those two changes, I get the same results. Disks says there is a nvme device there but also says "No media" and that the partition is unknown. Parted does not see anything other than the USB drive it booted from. Remember that right now, there is a fully working Mint 21.3 install on the nvme that nothing in Ubuntu seems to be able to see or understand.

I will go through that link you provided in more detail later today. Thanks for helping.

---

### Post by flea77 on 2024-03-15
OK, my mind is officially blown. Just for grins I thought I would try Ubuntu 22.04 LTS and it seems to work perfectly. I haven't tried installing it, but both Disks and Gparted work booted from the USB just like you would expect. 

So my complete newbie thoughts are there is something that has changed in Ubuntu 23.10 that Ubuntu 22.04, Mint 21.3, and Debian 12.5 all seem to have nailed down.

I should mention that the USB drive is the same, USB port I am using to boot is the same, I made all of the USBs with the same Rufus version on the same computer in the same USB port using DD mode.

---

### Post by tea for one on 2024-03-15
The installer for Ubuntu 23.10 is very different to the installer in 22.04.
The download page for Ubuntu 23.10 has two options:-
[LIST]
[*]Download 23.10
[*]Download 23.10 (Legacy Desktop Installer)
[/LIST]

---

### Post by flea77 on 2024-03-15
Yep, thought about that. Used the legacy desktop installer and the results are the same. My guess is that the kernel, drivers, and Disks/Gparted is the same.

---

### Post by flea77 on 2024-03-17
Just to consolidate:

SSD firmware is the latest
Laptop firmware is the latest
SSD has been swapped out
SATA is set to AHCI
Fast boot in UEFI has three options: Minimal, Thorough, and Auto. It was set to Thorough and I also tried Auto.
Windows 10 works perfectly
Mint 21.3 works perfectly
Debian 12.5 works perfectly
Fedora 39 Disks works perfectly
KALI 2024.1 Disks and Gparted work perfectly
Elementary OS 7 Gparted works perfectly
Zorin OS 16.2 Gparted and Disks work perfectly
Ubuntu 22.04 LTS works perfectly
Ubuntu 23.10.1 does not see the nvme but does see the USB, Disks shows the nvme but says no media, Gparted does not see the nvme
Ubuntu 23.10 legacy does not see the nvme but does see the USB, Disks shows the nvme but says no media, Gparted does not see the nvme

Open to any suggestions on where to go from here...

---

### Post by MAFoElffen on 2024-03-17
Since you are doing "tests"... Could I please ask you to try the Daily ISO for Noble? : [https://cdimage.ubuntu.com/daily-live/current/](https://cdimage.ubuntu.com/daily-live/current/)

That is due to release as LTS next month, and uses the same installer as 23.10. With Noble, there is no longer a legacy Installer, just the newer one. 

I think that would be a good test case for Noble... And if there is a problem, a bug report filed to get it corrected before the LTS release. That is my own big concern with reading this.

---

### Post by ubfan1 on 2024-03-17
What kernel versions do the working installs have?  23.10 uses kernel 6.5.  After the first update/upgrade, the 22.04 you installed should definitely have a 6.5 kernel as the default boot too -- does it work? If not,  hopefully you should be able to  boot the older 5.15 kernel if it is  listed in the grub menu choices.

---

### Post by flea77 on 2024-03-18
Happy to help!

Downloaded and booted, received two crash errors, reported them and they have already been reported by others so nothing new. The good news is that both Disks and Gparted appear to work fine. They both see the nvme and existing Mint partitions as they should.

Stupid question: Can I just install this pre-release version and keep it updated and wind up with the final 24.04 LTS?

Installed just fine with the one error, then I installed KDE and rebooted, now the system will not boot, it just hangs at /dev/nvme01p2 clean blah blah blocks. I think I might need to wait until it is formally released ;-)

Thanks!

---

### Post by ubfan1 on 2024-03-18
Probably will work, but 24.04 is still under heavy development, so might have some leftover cruft if you update early.  24.04 is using the 6.8 kernel, so may be all sorts of additional issues.  If your 22.04 runs with the 5.15 kernel, I'd keep that until the (next month) release of 24.04,  then make the (official) upgrade.

---

### Post by flea77 on 2024-03-18
I have a working Mint 21.3 install on the drive so I will stick with that until 24.04 comes out. Right now 24.04 installed but gave me a lot of grief after that which I should expect given it is pre-release. Whatever the problem it is nice to know it is just Ubuntu 23.10 specific and in a month that won't be a problem ;-)

Thank you all for your help. Much appreciated.

---

### Post by MAFoElffen on 2024-03-18
> **flea77 said:**
> Happy to help!

Downloaded and booted, received two crash errors, reported them and they have already been reported by others so nothing new. The good news is that both Disks and Gparted appear to work fine. They both see the nvme and existing Mint partitions as they should.

Stupid question: Can I just install this pre-release version and keep it updated and wind up with the final 24.04 LTS?

Installed just fine with the one error, then I installed KDE and rebooted, now the system will not boot, it just hangs at /dev/nvme01p2 clean blah blah blocks. I think I might need to wait until it is formally released ;-)

Thanks!

Thank you for your help with that... I was worried if it would see it or not. Glad it did, and had no problems (there).

Noble Kubuntu is going through a lot right now. In fact, all flavors are going through a lot of changes in the next 2-3 weeks. Ubuntu itself is fairly stable right now (at the moment, LOL). DEV testing is a challenge, expecting change every day. On my static installs, I get "at least" 10-20 updates a day. Daily builds are installs that are meant to test the installer, along with those changes to the base system. Both are where we work things out, and see how that goes. LOL ... "The challenge" is fun, and entertaining to me.

Best would be what was mentioned: Install 22.04 LTS until 24.04 LTS is released.

---

