---
title: "Upgrade to 17.04, hard drive unmounts/disappears seemingly at random"
date: 2017-04-19
forum: Installation &amp; Upgrades
---

### Post by Tachyon on 2017-04-19
I have a Dell XPS 9550 and was dual-booting Windows 10 with Ubuntu 16.04. Over the weekend, I upgraded to 16.10 and then 17.04 without any apparent problems.

Since the upgrade, however, here is what happens:
[LIST]
[*]Icons on the launcher disappear and indicator icons turn into blank squares
[*]If I have a terminal open, commands are no longer found. E.g., I enter `dmesg` and it comes back with "command not found". `/bin/dmesg` gives same result
[*]I have to do a power reset; when I press the power button, the screen will go black with a blinking cursor in the top left corner.
[*]Occasionally when this has happened I see this error message: [http://imgur.com/a/vysAx](http://imgur.com/a/vysAx)
[/LIST]

I tried booting from a live USB and running fsck, and it came back clean.

I tried doing a clean install, during which I:
[LIST]
[*]deleted the swap partition
[*]deleted the ext4 partition with the Ubuntu installation
[*]created a brand new ext4 partition and installed 17.04
[/LIST]

Here's my current partition setup:
```
Disk /dev/nvme0n1: 238.5 GiB, 256060514304 bytes, 500118192 sectors
Units: sectors of 1 * 512 = 512 bytes
Sector size (logical/physical): 512 bytes / 512 bytes
I/O size (minimum/optimal): 512 bytes / 512 bytes
Disklabel type: gpt
Disk identifier: 79239590-312D-4C78-944E-2D1CAEB0B1B8

Device             Start       End   Sectors  Size Type
/dev/nvme0n1p1      2048   1026047   1024000  500M EFI System
/dev/nvme0n1p2   1026048   1288191    262144  128M Microsoft reserved
/dev/nvme0n1p3   1288192 426864964 425576773  203G Microsoft basic data
/dev/nvme0n1p4 426866688 427823103    956416  467M Windows recovery environment
/dev/nvme0n1p5 427823104 500117503  72294400 34.5G Linux filesystem

```

And here's the output of sudo smartctl -a /dev/nvme0n1:
```
smartctl 6.6 2016-05-31 r4324 [x86_64-linux-4.10.0-19-generic] (local build)
Copyright (C) 2002-16, Bruce Allen, Christian Franke, www.smartmontools.org

=== START OF INFORMATION SECTION ===
Model Number:                       PM951 NVMe SAMSUNG 256GB
Serial Number:                      S29NNXBG905733
Firmware Version:                   BXV76D0Q
PCI Vendor/Subsystem ID:            0x144d
IEEE OUI Identifier:                0x002538
Controller ID:                      1
Number of Namespaces:               1
Namespace 1 Size/Capacity:          256,060,514,304 [256 GB]
Namespace 1 Utilization:            204,282,724,352 [204 GB]
Namespace 1 Formatted LBA Size:     512
Local Time is:                      Wed Apr 19 17:56:09 2017 EDT
Firmware Updates (0x06):            3 Slots
Optional Admin Commands (0x0017):   Security Format Frmw_DL *Other*
Optional NVM Commands (0x001f):     Comp Wr_Unc DS_Mngmt Wr_Zero Sav/Sel_Feat
Maximum Data Transfer Size:         32 Pages

Supported Power States
St Op     Max   Active     Idle   RL RT WL WT  Ent_Lat  Ex_Lat
 0 +     6.00W       -        -    0  0  0  0        5       5
 1 +     4.20W       -        -    1  1  1  1       30      30
 2 +     3.10W       -        -    2  2  2  2      100     100
 3 -   0.0700W       -        -    3  3  3  3      500    5000
 4 -   0.0050W       -        -    4  4  4  4     2000   22000

Supported LBA Sizes (NSID 0x1)
Id Fmt  Data  Metadt  Rel_Perf
 0 +     512       0         0

=== START OF SMART DATA SECTION ===
Read NVMe SMART/Health Information failed: NVMe Status 0x2002

```
I'm not experiencing any I/O errors when in Windows.

I have not yet determined any pattern or apparent cause for the I/O errors (i.e., it doesn't appear to be correlated with a specific app or happen after a certain interval).

So, what other diagnostic steps would you recommend I take? Any ideas for solutions, or is my best option to do a clean install of 16.04 (where, again, I had zero problems) and just keep using it for the time being?

Thanks in advance for your advice.

---

### Post by ubfan1 on 2017-04-19
You version of smartctl is 6.6, so it should work with nvme devices.  The fix ([https://www.smartmontools.org/ticket/657](https://www.smartmontools.org/ticket/657)) show it running with -x instead of -a, try that.

---

### Post by Tachyon on 2017-04-19
Thanks for the suggestion. Unfortunately, that produces the exact same output as -a.

Full disclosure: The BIOS has two settings for the hard drive's SATA operation. There is a "RAID on" mode (default) and an "AHCI mode". When I was first installing Ubuntu 15.10 onto this computer, I had to switch the SATA operation mode to AHCI in order for the Ubuntu installer to see the drive. It has remained in this mode since. I don&#8217;t know anything about hard drive operation, so I have no idea if that's relevant to this issue.

---

### Post by hamsterready on 2017-05-21
Hi there,

I have same dell model and same problem. Did you manage to resolve the problem?

Please let me know.

Cheers

---

### Post by Tachyon on 2017-05-21
> **hamsterready said:**
> Hi there,

I have same dell model and same problem. Did you manage to resolve the problem?

Please let me know.

Cheers
Unfortunately not. It seems to be happening less frequently, for what it’s worth, so the system is stable-ish to the point where I haven't yet downgraded. Occasionally I'm also experiencing graphics freezes, where I can still switch between desktops and use the panel, but I can't move the mouse or interact with any windows. I don't know if this is related.

Thank you for posting and letting me know it's the model and not just my computer/drive! That gives me hope that a future kernel or driver update will stabilize things.

For anyone else out there … if there are any other diagnostics or log dumps I can post to help figure this out, let me know.

---

### Post by oldfred on 2017-05-21
Have you updated both UEFI/BIOS and NVMe firmware? 

 Dell XPS 13 9360 16.04 worked after nvme firmware & BIOS update, 16.10 did not, new rEFInd for NVMe
[http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install](http://askubuntu.com/questions/884991/ubuntu-16-10-dual-boot-error-grub-efi-amd64-signed-package-failed-to-install) 

Dell only  seems to work with AHCI, not with RAID mode on drives.
      
 Dell UEFI Dual boot instructions using Something Else
[https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN](https://www.dell.com/support/article/us/en/19/SLN301754/how-to-install-ubuntu-and-a-recent-windows-operating-system-as-a-dual-boot-on-your-dell-pc?lang=EN)

---

### Post by hamsterready on 2017-05-22
Thanks mate, I thought it might be something with my drive ... but after finding your post it seems clear it something dell/kernel/ubuntu related. Will keep searching.

---

