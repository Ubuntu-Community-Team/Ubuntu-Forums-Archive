---
title: "MSI X670E ACE, can’t install Ubuntu Linux 23.04"
date: 2023-10-12
forum: Installation &amp; Upgrades
---

### Post by sblantipodi on 2023-10-12
Hi all.


I am trying to install Linux to my MSI X670E ACE motherboard running a 7950X3D.


I have three m.2 ssd nvme, one of them runs Windows without problems.


I flashed my Ubuntu 23 on my usb key, I booted the usb key and I get this error:

[IMG]https://forum.level1techs.com/uploads/default/optimized/4X/c/b/9/cb952cb49f442d483fea75231dde14596a15b919_2_720x540.jpeg[/IMG]

After this error I get this one

[IMG]https://forum.level1techs.com/uploads/default/original/4X/a/9/c/a9c04afcc91274f14c8bc0fa677d63d22e6a0f75.jpeg[/IMG]




And after that one when it’s time to create a partition on the disk, I see no disks available for the installation and obviously can’t proceed.
I'm using the latest BIOS version available.


Any help would be really appreciated.


Thanks.

---

### Post by tea for one on 2023-10-12
Also posted here [https://forum.level1techs.com/t/msi-x670e-ace-cant-install-ubuntu-linux/202305](https://forum.level1techs.com/t/msi-x670e-ace-cant-install-ubuntu-linux/202305)

Nevertheless, let's start from scratch.

Assuming that your Windows disk is not your target disk
Isolate, de-activate or physically remove all disks other than your target disk.

Only some of the following suggestions may be applicable
Disable Secure Boot (Some vendors require an Admin password to access the Secure Boot setting)
Disable Fast Boot (It may prevent access to one-time boot menu via dedicated keys because the device boots too fast) 
Disable Legacy mode 
Check that Legacy USB Support is enabled
Change SATA mode to AHCI where the default is RAID or Intel RST (Windows may need AHCI driver)
[https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500](https://superuser.com/questions/1672500/ubuntu-installation-with-intel-rst?noredirect=1#comment2565531_1672500)
Disable TPM (Trusted Platform Module) or PTT (Platform Trust Technology) or FTPM (Firmware Trusted Platform Module) or TPT (Trust Platform Technology)
Disable Optane memory and storage
Remove Optane drive and reset UEFI to default (with the suggested changes above)
[https://ubuntuforums.org/showthread.php?t=2471365](https://ubuntuforums.org/showthread.php?t=2471365)
Enable Microsoft 3rd Party UEFI CA 

Boot into a live Ubuntu session
Open a terminal and enter
```
sudo parted -l
```
Post the terminal output (inc. the command) within code tags (via Adv Reply)

---

### Post by Rubi1200 on 2023-10-12
In addition to all the excellent advice from **tea for one** also consider trying the legacy installer.

I tried and failed twice with the new installer but legacy worked like a charm:
[https://ubuntu.com/download/desktop](https://ubuntu.com/download/desktop)[COLOR=#000000] and scroll down the page to here [/COLOR][https://prnt.sc/COz5p_sRxPqP](https://prnt.sc/COz5p_sRxPqP)

---

### Post by oldfred on 2023-10-12
In addition, check that SSD have latest firmware.

And if you want to experiment with Legacy, be sure to use gpt partitioning.
The only difference with UEFI and Legacy is the version of grub and required gpt partitions.
With UEFI, you have to have the ESP - efi system partition. And with BIOS you have to have the bios_grub partition. 
You can add both as first partitions and make it easy to convert from BIOS to UEFI or vice-versa.

---

### Post by sblantipodi on 2023-10-12
Hi,
I like to have two MBR, one for linux and one for windows and then switch between them using the BIOS UEFI boot priority.

To do this, I usually disconnect my windows ssd before installing linux.
Is there a smarter way to do it?

I have an SSD with windows installed, 
I have an empty SSD where I want to install linux.

How can I tell ubuntu to write the MBR on the second SSD and don't touch the windows MBR on the first SSD? 

Thanks

---

### Post by oldfred on 2023-10-12
Threads merged. Please do not post same question again. We all are volunteers & need to know what has already been suggested.
Also UEFI systems do not boot from MBR, they use ESP - efi system partition which is FAT32 with boot,esp flags.

Ubuntu Ubiquity installer with 22.04 and before defaults to first drive. Multiple work arounds in bug report.
[https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379](https://bugs.launchpad.net/ubuntu/+source/ubiquity/+bug/1396379)
Most find turning off esp flag on Windows drive works easier, but you have to turn it back on after Ubuntu install.

---

### Post by sblantipodi on 2023-10-12
I'm sorry but that are very different questiosn, isn't it?
how this two questons coexist in the same thread?

---

### Post by tea for one on 2023-10-12
> **sblantipodi said:**
> Hi,
I like to have to MBR, one for linux and one for windows and then switch between them using the BIOS UEFI boot priority.
Yes, booting via UEFI boot menu is good practice.
Each OS on a separate disk with ESP and GPT is ideal.
MBR is old fashioned and should be avoided in 2023.
> To do this, I usually disconnect my windows ssd before installing linux.
Is there a smarter way to do it?
No better way, I mentioned this in post no. 2.
> I have an SSD with windows installed, 
I have an empty SSD where I want to install linux.
I can I tell ubuntu to write the MBR on the second SSD and don't touch the windows MBR on the first SSD? 
You create the disk with GPT not MBR.
If the Windows disk is isolated, then create a GPT (partition table) on your target disk.

Each OS must have GPT and ESP

---

### Post by sblantipodi on 2023-10-12
> **tea for one said:**
> Yes, booting via UEFI boot menu is good practice.
Each OS on a separate disk with ESP and GPT is ideal.
MBR is old fashioned and should be avoided in 2023.

No better way, i mentioned this in post no. 2.
 
You create the disk with GPT not MBR.
If the Windows disk is isolated, then create a GPT (partition table) on your target disk.

Each OS must have GPT and ESP

ok thank you. 
I'll try all your suggestions and report back! Thank you very much!!!

---

### Post by sblantipodi on 2023-10-12
I was using the standard installer version 23.04,
I now downloaded the legacy installer version 23.10 and it worked like a charm without additional things to do on my side or bios change.


I don&#8217;t know if it&#8217;s the legacy installer that fixed the problem or if it&#8217;s the newer version.

Regarding the two SSDs, I haven't deattached or disabled the Windows one, on the installation phase I simply said to the installer to let me do the manual partitioning and I choosed to install the boot thing on the linux ssd.



For now I&#8217;m set thank you all.

---

