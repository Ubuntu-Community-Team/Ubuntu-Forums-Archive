---
title: "“Install alongside Windows 10” gone from Ubuntu 18.04 Installer"
date: 2019-12-12
forum: Installation &amp; Upgrades
---

### Post by kubasienczyk on 2019-12-12
I’m trying to install Ubuntu 18.04 alongside Win10, but after booting from the USB the option to install Ubuntu alongside the existing OS is gone.

I have shrunk existing partitions to create 90 GB worth of an unallocated space, which always did the trick. It doesn’t now: the option is gone.

Does it have something to do with the fact, that my disk has 4 partitions already? (c:/ windows 183 GB, 350 MB EFI System Partition, 619 MB OEM Partition and 202 GB Data partition, all preconfigured).

What do I do?

---

### Post by TheFu on 2019-12-12
Can't tell the real issue from the description. We need some facts.  The best way to provide that is by booting from any Ubuntu desktop ISO (flash drive), installing boot-repair into that live/try ubuntu environment, running boot-repair and only using the "gather information" button at the bottom-center of the screen.  DO NOT ASK IT TO FIX ANYTHING. That is very important!

Next, post the URL back here so we can see the real environment.

Or should we guess at answers until one is correct?

---

### Post by yancek on 2019-12-12
[QUOTEDoes it have something to do with the fact, that my disk has 4 partitions already?][/QUOTE]

No.  Read the first paragraph at the link below under the section Partition Requirements.  A common reason for this situation is leaving fastboot and or hibernation as the default in windows.  Have you tried the manual option, Something Else and if you do, do you see any windows partitions when you are in the Installation type window?  

[https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions](https://docs.microsoft.com/en-us/windows-hardware/manufacture/desktop/configure-uefigpt-based-hard-drive-partitions)

---

### Post by kubasienczyk on 2019-12-13
I have options to erase, encrypt, use LVM and do Something else. I can see all discs in Something else, but nowhere does the installer recognise existing Win10. I have turned fastboot off prior though.

I’d gladly post a URL from boot-repair, but so far I can’t get the wi-fi to work in the try Ubuntu session.

---

### Post by yancek on 2019-12-13
>  I have turned fastboot off prior though.


Do you have the hibernation options off, explained at the microsoft site below?  Did you disable hibernation and fastboot immediately prior to attempting to install Ubuntu?  Some windows updates will turn both back on.  You will not be asked if you want this nor will you be informed. 

[https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running](https://support.microsoft.com/en-us/help/920730/how-to-disable-and-re-enable-hibernation-on-a-computer-that-is-running)

---

### Post by kubasienczyk on 2019-12-13
I turned fastboot off prior to the Ubuntu install attempt, but not hibernation. I have done this now, following the guide, and attempted the boot installer again. Still, no „alongside” option, just erase, encrypt, LVM and something else.

---

### Post by TheFu on 2019-12-13
Can you plug in an ethernet cable?

---

### Post by Frogs Hair on 2019-12-13
You can use the something else option and install to the unallocated space, but I'd be a bit concerned that the wifi doesn't connect. You may find a solution after installation. I have not used the along side option with Win 7 or 10, but it was always visible in the installer .

---

### Post by kubasienczyk on 2019-12-13
I can, bit the lack of wi-fi visibility worries me. Same here: whenever I had installed Ubuntu alongside Windows, it was always working right off the bat.

---

### Post by kubasienczyk on 2019-12-13
Exactly my point: it should work with Try session. Also, the installer doesn&#8217;t recognize Win10 in Do Something Else session.

I have an unallocated space ready, but I don&#8217;t know where to install the boot loader. I&#8217;m scared to damage existing Windows installation (it&#8217;s my third day of using this brand new CPU).

There&#8217;s also an ongoing discussion elsewhere:
[https://askubuntu.com/questions/1195724/install-alongside-windows-10-gone-from-ubuntu-installer?noredirect=1#comment2003032_1195724](https://askubuntu.com/questions/1195724/install-alongside-windows-10-gone-from-ubuntu-installer?noredirect=1#comment2003032_1195724)
about Intel&#8217;s RAID mode, but it&#8217;s contents are a bit over my head. I&#8217;m a Ubuntu simpleton.

---

### Post by TheFu on 2019-12-13
> **kubasienczyk said:**
> I can, bit the lack of wi-fi visibility worries me. Same here: whenever I had installed Ubuntu alongside Windows, it was always working right off the bat.

If you plug in the ethernet, then you can use boot-repair to post the information we need to actually provide valid advice. Up to this point, it has been educated guessing.

---

### Post by oldfred on 2019-12-13
If new system with Windows pre-installed it will be UEFI with gpt partitioning.

You always install grub to drive like /dev/sda or /dev/nvme0n1, it may show details on brand/model of drive. Never install grub bootloader to a partition like sda1 or nvme0n1p1.     

If old BIOS it installs grub to MBR. If newer UEFI it automatically installs grub to first ESP - efi system partition sharing with other installs, but making Ubuntu first in UEFI boot order. Windows updates may reset UEFI to make Windows first in UEFI boot order.

What brand/model system?
Many now need drives set to AHCI from RAID/Intel SRT.
And many should have UEFI and SSD firmware update whether installing Ubuntu or not. 

 Almost all systems need UEFI updates, anyway, for mitigation of Meltdown and Spectre CPU vulnerabilities from cpu speculative execution and caching.

---

### Post by kubasienczyk on 2019-12-16
OK, turns out I can’t connect the network via Ethernet, as the laptop has no such port. Oh well.
However, I managed to snap a photo of an error occuring while loading the Try Ubuntu session (which loads anyway, just no wi-fi and *install alongside Windows* option:

[https://ibb.co/XsJhXtj](https://ibb.co/XsJhXtj)

---

### Post by oldfred on 2019-12-16
I think you need to resolve the Wireless issue first, so then we can easily work on other issues.
Post in Wireless sub-forum
[https://ubuntuforums.org/forumdisplay.php?f=336](https://ubuntuforums.org/forumdisplay.php?f=336)

Sticky from Wireless sub-forum
[https://ubuntuforums.org/showthread.php?t=370108](https://ubuntuforums.org/showthread.php?t=370108)
You need to download script and run it to see details on your wireless chip and configuration.
Easy to do if you have wired connection. If not you have to copy to flash drive or FAT32 partition that you can read from live installer & then copy results back to be able to post them.
They will want brand/model system and if you know wireless chip? Script should show chip details.

---

